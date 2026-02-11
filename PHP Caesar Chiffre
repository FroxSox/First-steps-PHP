<?php
    declare(strict_types=1); # enforce type safety where possible

    error_reporting(E_ALL); # show all warnings, notices, errors etc.
    ini_set('display_errors', 1);



    /*
    $abc = range("A", "Z");
    $secret = array_merge(range("D", "Z"), ['A','B','C']);

    $msg = "HELLO WORLD!";
    $msgSecret = '';

    for ($i = 0; $i < strlen($msg); $i++) {
        $currentCharacter = substr($msg, $i, 1);

        if ( ($index = array_search($currentCharacter,$abc)) !== false) {
            $msgSecret .= $secret[$index];
        }
        else {
            $msgSecret .= $currentCharacter;
        }
    }

    echo $msgSecret . "\n";
    */

    echo cesarCypherArrayFixed() . "\n";
    echo cesarCypherArrayFixed("Donald Trump") . "\n";

    echo cesarCypherArrayOffset("ABC") . "\n";
    echo cesarCypherArrayOffset("ABC",26) . "\n";

    echo cesarCypherAscii("ABC",4) . "\n";
    $secMsg = cesarCypherAscii("Donald Trump :(",3) . "\n";
    echo $secMsg;
    echo cesarCypherAscii($secMsg,-3) . "\n";

    echo cesarCypherAscii("aBCÿ",3) . "\n";


    function loopOverMessageArray(string $msg,array $abc,array $secret): string {
        $msgSecret = '';

        for ($i = 0; $i < strlen($msg); $i++) {
            $currentCharacter = substr($msg, $i, 1);

            if ( ($index = array_search($currentCharacter,$abc)) !== false) {
                $msgSecret .= $secret[$index];
            }
            else {
                $msgSecret .= $currentCharacter;
            }
        }

        return $msgSecret;
    }

    function cesarCypherArrayFixed(string $msg = "HELLO WORLD!"): string {
        $abc = range("A", "Z");
        $secret = array_merge(range("D", "Z"), ['A','B','C']); # hard coded offset by 3

        return loopOverMessageArray($msg,$abc,$secret);
    }

    function cesarCypherArrayOffset(string $msg, int $offset=3): string {
        $offset = abs($offset);
        $abc = range("A", "Z");
        $secretFirstPart = array_slice($abc, $offset);
        $secretSecondPart = array_diff($abc, $secretFirstPart);
        $secret = array_merge($secretFirstPart,$secretSecondPart);

        return loopOverMessageArray($msg,$abc,$secret);
    }

    function cesarCypherAscii(string $msg, int $offset=3): string {

        /*
        $a = 97;
        $z = 122;

        $A = 65;
        $Z = 90;
        */

        $cypherRanges = [97 => 122,65 => 90]; # a-z, A-Z

        $msgSecret = '';

        for ($i = 0; $i < strlen($msg); $i++) {
            $currentCharacter = substr($msg, $i, 1);

            $asciiValue = ord($currentCharacter);
            $isWithinRange = false;

            #           array      as key         => valuee
            foreach ($cypherRanges as $rangeIndex => $range) {
                if ($asciiValue >= $rangeIndex && $asciiValue <= $range) {
                    $msgSecret .= chr($asciiValue + $offset);
                    $isWithinRange = true;
                    break;
                }
            }

            if (!$isWithinRange) {
                $msgSecret .= $currentCharacter;
            }

            /*
            if ($asciiValue >= $a && $asciiValue <= $z) {
                $msgSecret .= chr($asciiValue + $offset);
            }
            elseif ($asciiValue >= $A && $asciiValue <= $Z) {
                $msgSecret .= chr($asciiValue + $offset);
            }
            else {

            }

            if (($asciiValue >= $a && $asciiValue <= $z) || ($asciiValue >= $A && $asciiValue <= $Z)) {
                $msgSecret .= chr($asciiValue + $offset);
            }
            */

            /*
            if ( ($index = array_search($currentCharacter,$abc)) !== false) {
                $msgSecret .= $secret[$index];
            }
            else {
                $msgSecret .= $currentCharacter;
            }
            */


        }

        return $msgSecret;

    }






































































































































































































