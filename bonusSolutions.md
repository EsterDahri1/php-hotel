BONUS come si faceva -->

<?php

$hotels = [

    [
        'name' => 'Hotel Belvedere',
        'description' => 'Hotel Belvedere Descrizione',
        'parking' => true,
        'vote' => 4,
        'distance_to_center' => 10.4
    ],
    [
        'name' => 'Hotel Futuro',
        'description' => 'Hotel Futuro Descrizione',
        'parking' => true,
        'vote' => 2,
        'distance_to_center' => 2
    ],
    [
        'name' => 'Hotel Rivamare',
        'description' => 'Hotel Rivamare Descrizione',
        'parking' => false,
        'vote' => 1,
        'distance_to_center' => 1
    ],
    [
        'name' => 'Hotel Bellavista',
        'description' => 'Hotel Bellavista Descrizione',
        'parking' => false,
        'vote' => 5,
        'distance_to_center' => 5.5
    ],
    [
        'name' => 'Hotel Milano',
        'description' => 'Hotel Milano Descrizione',
        'parking' => true,
        'vote' => 2,
        'distance_to_center' => 50
    ],


    BONUS:
     if(isset($_GET['rating'])){
        $hotels = array_filter($hotels, function ($hotel){
            return $hotel['vote'] >= $_GET['rating'];
        })
     }else{

     }



    if(isset($_GET['parking'] && $_GET['parking'] == 1)){
        var_dump('filter by has parking');

        $hotels = array_filter($hotels, function ($hotel){

            return $hotel['parking']

        });
    }elseif(isset$_GET['parking'] && $_GET['parking'] == 0){
            $hotels = array_filter($hotels, function ($hotel){

                return !  $hotel['parking']

            });
    }

];

?>

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PHP hotel</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">

</head>

<body class="bg-info bg-opacity-25">

    <div class="container">

        <!--BONUS-->


        <div class="filters">
        <form>
            <div>
                <input class="form-check-input" type="radio" name="parking" id="parking" value="1">
                <label class="form-check-label" for="parking">
                    Can Park
                </label>
            </div>
            <div>
                <input class="form-check-input" type="radio" name="parking" id="no_parking" value="0">
                <label class="form-check-label" for="no_parking">
                    Cannot Park
                </label>
            </div>


            <div>
                <label for="rating" class="form-check-select">Rating</label> 
                <option value="" selected>All</option>
                <option value="1" <?php echo (isset($_GET['rating'] && $_GET['rating'] == 1 ? 'selected' : 'none')?>>1</option>
                <option value="2"  <?php echo (isset($_GET['rating'] && $_GET['rating'] == 2 ? 'selected' : 'none')?>>2+</option>   
                <option value="3"  <?php echo (isset($_GET['rating'] && $_GET['rating'] == 3 ? 'selected' : 'none')?>>3+</option>   
                <option value="4"  <?php echo (isset($_GET['rating'] && $_GET['rating'] == 4 ? 'selected' : 'none')?>>a+</option>              
            </div>

            <button type="submit" class="btn btn-primary">Filter</button>
            <button type="reset" class="btn btn-danger">Reset</button>
        </form>
        </div>


        <!--EndBONUS-->


        <div class="mt-3 bg-info border-1 rounded-1 shadow-sm">
            <h1 class="p-3 text-white text-center">List of hotels you can stay in</h1>
        </div>
        <table class="mt-5 table table-hover table-bordered">
            <caption></caption>
            <thead>
                <tr>
                    <th scope="col">Nome</th>
                    <th scope="col">Descrizione</th>
                    <th scope="col">Parcheggio</th>
                    <th scope="col">Voto</th>
                    <th scope="col">Distanza dal centro</th>
                </tr>
            </thead>
            <tbody>
                <?php foreach ($hotels as $hotel) : ?>
                    <tr>
                        <th scope="row"><?php echo $hotel['name'] ?></th>
                        <td><?php echo $hotel['description'] ?></td>
                        <td><?php echo ($hotel['parking']) ? '✔️' : '✖️' ?></td>
                        <td><?php echo $hotel['vote'] ?> stars</td>
                        <td><?php echo $hotel['distance_to_center'] ?> km</td>
                    </tr>
                <?php endforeach; ?>
            </tbody>
        </table>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>
</body>

</html>