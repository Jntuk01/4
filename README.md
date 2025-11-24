# 4
Exp-3:merge two arrays:
<!DOCTYPE html>
<html>
<head>
    <title>Merge and Sort Arrays</title>
</head>
<body>
    <h2>Merge Two Arrays and Sort in Descending Order</h2>

    <!-- Input Form -->
    <form method="post">
        Enter first array (comma separated): <br>
        <input type="text" name="array1" required><br><br>

        Enter second array (comma separated): <br>
        <input type="text" name="array2" required><br><br>

        <input type="submit" value="Merge & Sort">
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        // Get input from form
        $input1 = $_POST['array1'];
        $input2 = $_POST['array2'];

        // Convert comma-separated string into array
        $array1 = array_map('intval', explode(',', $input1));
        $array2 = array_map('intval', explode(',', $input2));

        // Merge the arrays
        $mergedArray = array_merge($array1, $array2);

        // Sort in descending numeric order
        rsort($mergedArray, SORT_NUMERIC);

        // Display result
        echo "<h3>Result:</h3>";
        echo implode(" ", $mergedArray);
    }
    ?>
</body>
</html>


Exp-4:copy file:
<!DOCTYPE html>
<html>
<head>
    <title>Copy File Content</title>
</head>
<body>
    <h2>Copy Contents from One File to Another</h2>

    <form method="post">
        Source File: <input type="text" name="source" placeholder="input.txt" required><br><br>
        Destination File: <input type="text" name="dest" placeholder="output.txt" required><br><br>
        <input type="submit" value="Copy File">
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $source = $_POST['source'];
        $dest   = $_POST['dest'];

        // Check if source file exists
        if (!file_exists($source)) {
            echo "<p style='color:red;'>Error: Source file not found!</p>";
        } else {
            // Read the content of source file
            $content = file_get_contents($source);

            // Write content into destination file
            file_put_contents($dest, $content);

            echo "<p style='color:green;'>Contents of <b>$source</b> copied successfully into <b>$dest</b>!</p>";
        }
    }
    ?>
</body>
</html>

Exp-5:prime numbers:
<!DOCTYPE html>
<html>
<head>
    <title>Prime Numbers 1-50</title>
</head>
<body>
    <h2>Prime Numbers Between 1 and 50</h2>
    <p>
    <?php
    for ($num = 2; $num <= 50; $num++) {
        $isPrime = true;

        // check divisibility
        for ($i = 2; $i <= sqrt($num); $i++) {
            if ($num % $i == 0) {
                $isPrime = false;
                break;
            }
        }

        if ($isPrime) {
            echo $num . " ";
        }
    }
    ?>
    </p>
</body>
</html>

Exp-7:string operations:
<!DOCTYPE html>
<html>
<head>
    <title>PHP String Operations</title>
</head>
<body>
    <h2>PHP String Operations</h2>

    <form method="post">
        Enter a String: <input type="text" name="mainStr" placeholder="Type a sentence" required><br><br>
        Enter Word to Search: <input type="text" name="searchStr" placeholder="Word to find"><br><br>
        <input type="submit" value="Process String">
    </form>

    <hr>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $str = $_POST['mainStr'];
        $search = $_POST['searchStr'];

        // a) Find length of string
        $length = strlen($str);

        // b) Count number of words
        $wordCount = str_word_count($str);

        // c) Reverse string
        $reversed = strrev($str);

        // d) Search for a specific string
        if ($search != "") {
            if (strpos($str, $search) !== false) {
                $searchResult = "The word '$search' was found in the string.";
            } else {
                $searchResult = "The word '$search' was NOT found in the string.";
            }
        } else {
            $searchResult = "No search word entered.";
        }

        echo "<h3>Results:</h3>";
        echo "a) Length of string: $length <br>";
        echo "b) Number of words: $wordCount <br>";
        echo "c) Reversed string: $reversed <br>";
        echo "d) Search result: $searchResult <br>";
    }
    ?>
</body>
</html>

Exp-welcome page:
<!DOCTYPE html>
<html>
<head>
    <title>Welcome Page</title>
</head>
<body>

<h2>
    <?php
        echo "Welcome to the website!";
    ?>
</h2>

</body>
</html>



Exp-calculator:
<!DOCTYPE html>
<html>
<head>
    <title>Simple PHP Calculator</title>
</head>
<body>

<h2>PHP Calculator</h2>

<form method="post">
    Enter First Number:
    <input type="number" step="any" name="num1" required><br><br>

    Enter Second Number:
    <input type="number" step="any" name="num2" required><br><br>

    <input type="submit" name="add" value="Add">
    <input type="submit" name="sub" value="Subtract">
    <input type="submit" name="mul" value="Multiply">
    <input type="submit" name="div" value="Divide">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {

    // Convert inputs to numbers
    $a = floatval($_POST['num1']);
    $b = floatval($_POST['num2']);

    if (isset($_POST['add'])) {
        echo "<h3>Result: " . ($a + $b) . "</h3>";
    }

    if (isset($_POST['sub'])) {
        echo "<h3>Result: " . ($a - $b) . "</h3>";
    }

    if (isset($_POST['mul'])) {
        echo "<h3>Result: " . ($a * $b) . "</h3>";
    }

    if (isset($_POST['div'])) {
        if ($b == 0) {
            echo "<h3 style='color:red;'>Error: Cannot divide by zero!</h3>";
        } else {
            echo "<h3>Result: " . ($a / $b) . "</h3>";
        }
    }
}
?>
</body>
</html>

Exp-even/odd:
<!DOCTYPE html>
<html>
<head>
    <title>Even or Odd Checker</title>
</head>
<body>

<h2>Check Even or Odd</h2>

<form method="post">
    Enter a number:
    <input type="number" name="num" required>
    <input type="submit" value="Check">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $num = $_POST['num'];

    if ($num % 2 == 0) {
        echo "<h3>$num is an EVEN number</h3>";
    } else {
        echo "<h3>$num is an ODD number</h3>";
    }
}
?>

</body>
</html>

Exp-largest of three:
<!DOCTYPE html>
<html>
<head>
    <title>Largest of Three Numbers</title>
</head>
<body>

<h2>Find the Largest Number</h2>

<form method="post">
    Enter Number 1: <input type="number" name="num1" required><br><br>
    Enter Number 2: <input type="number" name="num2" required><br><br>
    Enter Number 3: <input type="number" name="num3" required><br><br>
    <input type="submit" value="Check Largest">
</form>

<br>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {

    $num1 = $_POST['num1'];
    $num2 = $_POST['num2'];
    $num3 = $_POST['num3'];

    if ($num1 >= $num2 && $num1 >= $num3) {
        echo "<strong>$num1 is the largest number.</strong>";
    } elseif ($num2 >= $num1 && $num2 >= $num3) {
        echo "<strong>$num2 is the largest number.</strong>";
    } else {
        echo "<strong>$num3 is the largest number.</strong>";
    }
}
?>

</body>
</html>
