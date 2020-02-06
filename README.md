# Regex

All regex expressions made on diferent languages


## Python 3:

### Detect Floating Point Number:
    r'^[+-]?\d*\.\d+$'
    
### Valid Roman Numerals:
    r'M{0,3}(C[MD]|D?C{0,3})(X[CL]|L?X{0,3})(I[VX]|V?I{0,3})$'

### Valid phone number:
    On this example, it must start with 7,8 or 9 and be length 9
    r'^[789]\d{8}$'

### Valid Email Address:
    The username starts with an English alphabetical character, and any subsequent characters
    consist of one or more of the following: alphanumeric characters, -,., and _.
    The domain and extension contain only English alphabetical characters.
    The extension is max length 3, min length 1.
    
    r'^[a-zA-Z][a-zA-Z1-9._-]* <[a-z][a-z1-9._-]*@[a-z]+\.[a-z]{1,3}>$'
    
    if Email with no numbers:
    
    r'^([\w\.]+@\w+(\.\w+)+)$'


### Valid Hex Color Code
    r'(?!^)(#[a-fA-F0-9]{6}|#[a-fA-F0-9]{3})'





## Java:

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
    "http[s]?:\\/\\/(ww[w2]\\.)?(([a-zA-Z0-9\\-]+\\.)+([a-zA-Z\\-])+)"
    
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
