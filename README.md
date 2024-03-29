# Regex

All regex expressions made on diferent languages

## Python 3:

### Valid date:
    r'^(?:(?:(?:(?:(?:[13579][26]|[2468][048])00)|(?:[0-9]{2}(?:(?:[13579][26])|(?:[2468][048]|0[48]))))-(?:02-(?:0[1-9]|1[0-9]|2[0-8])))|(?:(?:[0-9]{4}-(?:(?:(?:0[13578]|1[02])-(?:0[1-9]|[12][0-9]|3[01]))|(?:(?:0[469]|11)-(?:0[1-9]|[12][0-9]|30))|(?:02-(?:0[1-9]|[1][0-9]|2[0-9]))))))$'

### Detect Floating Point Number:
    r'^[+-]?\d*\.\d+$'
    
### Valid Roman Numerals:
    r'M{0,3}(C[MD]|D?C{0,3})(X[CL]|L?X{0,3})(I[VX]|V?I{0,3})$'

### Valid phone number:
    On this example, it must start with 7,8 or 9 and be length 9
    r'^[789]\d{8}$'
<br>

    Allow for prefix (+ sign and 2 or 3 digits) and 9 numbers (divided in grops of 3 or not)
    (\+\d{2,3})? ?\d{3} ?\d{3} ?\d{3}
<br>

    Spanish phone:
    ^(\+\d{2,3})? ?\d{3} ?(\d{3} ?\d{3}|\d{2} ?\d{2} ?\d{2})$

### Valid Email Address:
    The username starts with an English alphabetical character, and any subsequent characters
    consist of one or more of the following: alphanumeric characters, -,., and _.
    The domain and extension contain only English alphabetical characters.
    The extension is max length 3, min length 1.
    
    r'^[a-zA-Z][a-zA-Z1-9._-]* <[a-z][a-z1-9._-]*@[a-z]+\.[a-z]{1,3}>$'
    
    user123 <user34_43@fjkds.com> it's correct
    
    if Email with no numbers:
    
    r'^([\w\.]+@\w+(\.\w+)+)$'
    
    Basic email:
    ^[a-z][a-z1-9._-]*@[a-z]+\.[a-z]{1,3}$


### Valid Hex Color Code
    r'(?!^)(#[a-fA-F0-9]{6}|#[a-fA-F0-9]{3})'
    
### Detect "&&" and "||" between spaces:
    r'(?<= )(&&|\|\|)(?= )'
    
### Multiple test in order to check if valid password:
    import re;
    rex = [
        r'([A-Z]).*([A-Z])', #At least 2Upper english alphabet characters
        r'\d.*\d.*\d', #At least 3 numbers
        r'^[A-Za-z0-9]+$', #Only english alphabet and numbers
        r'^.{10}$', #Length = 10
        r'^(?:([A-Za-z0-9])(?!.*\1))*$' #No repetitions of characters
    ];
    case = input();
    print("Valid" if all([re.search(rex[j], case) for j in range(len(rex))]) else "Invalid");

### Valid credit card:
    #These expressions can be used the same way as the "Multiple test in order to check if valid password".
    rex = [
        # start with 4, 5 or 6;
        # only numbers and total length = 16 digits
        # may be divided in 4-digits-group divided by "-"
        # do not repeat the same digit more than 3 times
        r'^[456]\d{3}(-?\d{4}){3}$',
        r'^(?:(\d)-?(?!(-?\1){3,}))+$'
    ];


## JavaScript:

### Correct Spannish IDs:
    ·Passport:
    This expression checks whenever a string named id is a passport:
      /^[A-Z][0-9]{8}$/
    ·CIF:
    whenever a string named id is a CIF
     /^([ABCDEFGHJKLMNPQRSUVW])(\d{7})([0-9A-J])$/
    ·NIE
    whenever a string named id is a NIE
     /^[XYZ]\d{7,8}[A-Z]$/

## Java:

### Website:

    ^https?://(www2?\.)?[-a-zA-Z\d@:%._\+~#=]{1,256}\.[a-zA-Z\d()]{1,6}\b([-a-zA-Z\d()@:%_\+.~#?&/=]*)$

### Valid IP address:
    If IP v4:
    
    "^((([0-1]?[0-9]?[0-9]|[2][0-5][0-5])\\.){3}([0-1]?[0-9]?[0-9]|[2][0-5][0-5])|^([0-9a-f]{1,4}:){7}[0-9a-f]{1,4})$"
    
    Once it's valid, you can check if it is a IPV6:
    
    "^([0-9a-f]{1,4}:){7}[0-9a-f]{1,4}$"
    
    
### Duplicated word on text:
    "\\b(\\w+)(?:\\W+\\1\\b)+"
    
### Valid user name:

    The username consists of 8 to 30 characters inclusive. If the username
    consists of less than 8 or greater than 30 characters, then it is an 
    invalid username.
    The username can only contain alphanumeric characters and underscores (_).
    Alphanumeric characters describe the character set consisting of lowercase
    characters [a-z], uppercase characters [A-Z], and digits [0-9].
    The first character of the username must be an alphabetic character.
    
    "[a-zA-Z][a-zA-Z_0-9]{7,29}"
    
### Detect HTML links:
    "(?<code1><a href=\".+?\")(?<code2>.*?[<h1><b>]*>[\\s]*)(?<code3>.*?<)"
    
### Detect HTML Tags:
    "(?<=<)[a-z0-3]+"
    
### Detect the Domain Name:
    "http[s]?:\\/\\/(www2?\\.)?(([a-zA-Z0-9\\-]+\\.)+([a-zA-Z\\-])+)"
    
### Identifying comments:
    import java.io.*;
    import java.util.*;
    import java.text.*;
    import java.math.*;
    import java.util.regex.*;
    public class Solution {

        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
            String line = "";
            while(sc.hasNext()){
                line = sc.nextLine();
                Matcher m = Pattern.compile("\\/\\/.*$").matcher(line);
                if(m.find()){
                    System.out.println(m.group());
                }
                else if(Pattern.compile("\\/\\*").matcher(line).find()){//start /*
                Matcher aux = Pattern.compile("\\/\\*").matcher(line);
                aux.find();
                    String text = line.substring(aux.start(), line.length());
                    while(!Pattern.compile("\\*\\/").matcher(line).find()){
                        line = sc.nextLine();
                        text += "\n"+line.trim();
                    }
                    System.out.println(text);
                }
            }
        }
    }
### Detecting Valid Latitude and Longitude Pairs:
    "^\\([-+]?([1-8]?[0-9](\\.\\d+)?|90(\\.0+)?), [-+]?([1-9]?[0-9](\\.\\d+)?|1[0-7][0-9](\\.\\d+)?|180(\\.0+)?)\\)$"
    
### Valid PAN format (Indian SSN):
    "[A-Z]{5}\\d{4}[A-Z]"
    
### Programming Language Detection:
    import java.io.*;
    import java.util.*;
    import java.text.*;
    import java.math.*;
    import java.util.regex.*;
    public class Solution {

        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
            String line = "";
            while(sc.hasNext()){
                line = sc.nextLine();
                if(Pattern.compile("#include").matcher(line).find()){
                    System.out.println("C");
                    break;
                }
                else if(Pattern.compile("java").matcher(line).find()){
                    System.out.println("Java");
                    break;
                }
                else if(Pattern.compile("(print |def)").matcher(line).find()){
                    System.out.println("Python");
                    break;
                }
            }
        }
    }
### Detect HTML Attributes
    import java.io.*;
    import java.util.*;
    import java.text.*;
    import java.math.*;
    import java.util.regex.*;

    public class Solution {

    public static void main(String[] args) throws NumberFormatException, IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        Pattern p = Pattern.compile("<(\\w+).*?(>|(\\/>))");
        Pattern pAttribute = Pattern.compile("\\s+(\\w+)=['\"].*?[\"']");
        int n = Integer.parseInt(br.readLine().trim());
        TreeMap<String, TreeSet<String>> map = new TreeMap<>();
        for (int i = 0; i < n; ++i) {
            String line = br.readLine().trim();
            Matcher m = p.matcher(line);
            while (m.find()) {
                String tag = m.group(1);//ex: div
                TreeSet<String> set = map.get(tag);
                if (set == null) {
                    set = new TreeSet<>();
                    map.put(tag, set);
                }
                String text = m.group();//ex: <a href="ab cd" attr1=' xyz'>
                Matcher m2 = pAttribute.matcher(text);
                while (m2.find()) {
                    set.add(m2.group(1));
                }
            }
        }
        for(Map.Entry<String, TreeSet<String>> entry: map.entrySet()) {
            StringBuilder sb = new StringBuilder();
            sb.append(entry.getKey()).append(":");
            for(String attr: entry.getValue()) {
                sb.append(attr).append(",");
            }
            if(sb.charAt(sb.length() - 1) == ',') {
                sb.deleteCharAt(sb.length() - 1);
            }
            System.out.println(sb.toString());
        }

        }
    }
    
### 
    /*
    given the numbers 1,2,3,4,5,6,7,8,9 on that order; find all combinations (with +-) that are equal to 100.
    eg: 1234+5678 != 100
        12+34-567-89
    */
    public class reto {
        public static void main(String[] args) {
            int[] numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9};
            String[] symbol = {"","+","-"};		
            /**
             Sistema ternario: 8 digits + 1
             0 1 2 10 11 12 20 21 22 100
             max number = 8 digits --> 22222222 ==> 6561 possible combinations
            */

            Base ternario = new Base(3);//We work on base 3
            String resultado;
            String equation;
            for(int i = 0; i < 6561; i++){//6561
                ternario.setNumero(i);
                resultado = ternario.getResultado();
                equation = "1";
                for(int j = 0; j < 8; j++){
                    equation = equation + symbol[Integer.parseInt(resultado.substring(j, j+1))] + numbers[j+1];
                }
                String[] parts = equation.split("(?=[/+])|(?<=[/+])|(?=[/-])|(?<=[/-])");
                double result = Double.parseDouble(parts[0]);
                for(int l = 1; l < parts.length; l+=2){
                    switch (parts[l]) {//symbol
                        case "+" :
                            result += Double.parseDouble(parts[l+1]);
                            break;
                        case "-" :
                            result -= Double.parseDouble(parts[l+1]);
                            break;
                    }
                }
                if(result == 100){
                    System.out.println("Comb: " + equation);//sol
                }
            }
        }
        public static String operacion(String signo, int number1, int number2) {
            if(signo == ""){
                return Integer.toString(number1) + Integer.toString(number2);
            }
            else if(signo == "+"){
                return Integer.toString(number1 + number2);
            }
            else{
                return Integer.toString(number1 - number2);
            }
        }
    }
