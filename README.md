CTF中那些脑洞大开的编码和加密
===
CTF中脑洞密码题(非现代加密方式)一般都是各种古典密码的变形，一般出题者会对密文进行一些处理，但是会给留一些线索<br>
### 0x00 目录

##### 常见编码: <br>
    1.ASCII编码 
    2.Base64/32/16编码 
    3.shellcode编码 
    4.Quoted-printable编码 
    5.XXencode编码 
    6.UUencode编码 
    7.URL编码 
    8.Unicode编码 
    9.Escape/Unescape编码 
    10.HTML实体编码
    11.敲击码(Tap code) 
    12.莫尔斯电码(Morse Code)
    13.编码的故事 
 
##### 各种文本加密 <br>
    换位加密: 
        1.栅栏密码(Rail-fence Cipher) 
        2.曲路密码(Curve Cipher) 
        3.列移位密码(Columnar Transposition Cipher) 
     
    替换加密: <br>
        1.埃特巴什码(Atbash Cipher)
        2.凯撒密码(Caesar Cipher) 
        3.ROT5/13/18/47 
        4.简单换位密码(Simple Substitution Cipher) 
        5.希尔密码(Hill Cipher) 
        6.猪圈密码(Pigpen Cipher) 
        7.波利比奥斯方阵密码（Polybius Square Cipher) 
        8.夏多密码(曲折加密)
        9.普莱菲尔密码(Playfair Cipher)
        10.维吉尼亚密码(Vigenère Cipher)
        11.自动密钥密码(Autokey Cipher)
        12.博福特密码(Beaufort Cipher)
        13.滚动密钥密码(Running Key Cipher)
        14.Porta密码(Porta Cipher)
        15.同音替换密码(Homophonic Substitution Cipher)
        16.仿射密码(Affine Cipher)
        17.培根密码(Baconian Cipher)
        18.ADFGX和ADFGVX密码(ADFG/VX Cipher)
        19.双密码(Bifid Cipher)
        20.三分密码(Trifid Cipher)
        21.四方密码(Four-Square Cipher)
        22.棋盘密码（Checkerboard Cipher)
        23.跨棋盘密码(Straddle Checkerboard Cipher)
        24.分组摩尔斯替换密码(Fractionated Morse Cipher)
        25.Bazeries密码(Bazeries Cipher)
        26.Digrafid密码(Digrafid Cipher)
        27.格朗普雷密码(Grandpré Cipher)
        28.比尔密码(Beale ciphers)
        29.键盘密码(Keyboard Cipher)
 
    其他有趣的机械密码:<br>
        1.恩尼格玛密码
        2.serpent(蛇)加密
        
    代码混淆加密:<br>
        1.asp混淆加密
        2.php混淆加密
        3.css/js混淆加密
        4.VBScript.Encode混淆加密
        5.ppencode
        6.rrencode
        7.jjencode/aaencode
        8.JSfuck
        9.jother
        10.brainfuck编程语言

### 0x01 正文

### 换位加密:
#### 1.栅栏密码(Rail-fence Cipher)

栅栏密码(Rail-fence Cipher)就是把要加密的明文分成N个一组，然后把每组的第1个字符组合，每组第2个字符组合...每组的第N(最后一个分组可能 <br>
不足N个)个字符组合，最后把他们全部连接起来就是密文，这里以2栏栅栏加密为例。 <br>
1.<br>
明文：The quick brown fox jumps over the lazy dog <br>
去空格：Thequickbrownfoxjumpsoverthelazydog <br>
分组：Th eq ui ck br ow nf ox ju mp so ve rt he la zy do g<br>
第一组：Teucbonojmsvrhlzdg <br>
第二组：hqikrwfxupoeteayo <br>
密文：Teucbonojmsvrhlzdghqikrwfxupoeteayo <br>
2.<br>
密文：T_ysK9_5rhk__uFMt}3El{nu@E <br>
明文：Th3_kEy_ls_{Kun9Fu_M@5tEr} 　 <br> 
   
### 替换加密:

#### 3.ROT5/13/18/47 

ROT5/13/18/47是一种简单的码元位置顺序替换暗码。此类编码具有可逆性，可以自我解密，主要用于应对快速浏览，或者是机器的读取。 <br>

ROT5 是 rotate by 5 places 的简写，意思是旋转5个位置，其它皆同。下面分别说说它们的编码方式： <br>

ROT5：只对数字进行编码，用当前数字往前数的第5个数字替换当前数字，例如当前为0，编码后变成5，当前为1，编码后变成6，以此类推顺序循环。 <br>

ROT13：只对字母进行编码，用当前字母往前数的第13个字母替换当前字母，例如当前为A，编码后变成N，当前为B，编码后变成O，以此类推顺序循环。 <br>

ROT18：这是一个异类，本来没有，它是将ROT5和ROT13组合在一起，为了好称呼，将其命名为ROT18。 <br>

ROT47：对数字、字母、常用符号进行编码，按照它们的ASCII值进行位置替换，用当前字符ASCII值往前数的第47位对应字符替换当前字符，例如当前为小写字母z，编码后变成大写字母K，当前为数字0，编码后变成符号_。用于ROT47编码的字符其ASCII值范围是33－126，具体可参考ASCII编码，下面以rot13以例。 <br>

明文：the quick brown fox jumps over the lazy dog <br>

密文：gur dhvpx oebja sbk whzcf bire gur ynml qbt <br>

解密地址：http://www.qqxiuzi.cn/bianma/ROT5-13-18-47.php <br>

#### 18.ADFGX和ADFGVX密码
ADFGX密码(ADFGX Cipher)是结合了改良过的Polybius方格替代密码与单行换位密码的矩阵加密密码，使用了5个合理的密文字母：A，D，F，G，X，这些 <br>
字母之所以这样选择是因为当转译成摩尔斯电码(ADFGX密码是德国军队在一战发明使用的密码)不易混淆，目的是尽可能减少转译过程的操作错误。  <br>

加密矩阵示例：  <br>

       A  D  F  G   X
      ----------------
    A | p  h  q  g   m 
    D | e  a  y  n   o 
    F | f  d  x  k   r
    G | c  v  s  z   w 
    X | b  u  t  i/j l

ADFGVX密码实际上就是ADFGX密码的扩充升级版，一样具有ADFGX密码相同的特点，加密过程也类似，不同的是密文字母增加了V，使得可以再使用10数字来替换明文  <br>

加密矩阵示例：  <br>

      A D F G V X
      -------------
    A | p h 0 q g 6
    D | 4 m e a 1 y
    F | l 2 n o f d
    G | x k r 3 c v
    V | s 5 z w 7 b
    X | j 9 u t i 8

#### 2.serpent(蛇)加密
serpent加密是一种分组加密算法 <br>
解密网站：http://serpent.online-domain-tools.com/ <br>


#### 8.JSfuck
JSFuck 可以让你只用 6 个字符[ ]( ) ! +来编写 JavaScript 程序


