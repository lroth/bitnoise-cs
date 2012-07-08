CSS/LESS
==================
1. Używamy less do dynamicznych arkuszów css (http://lesscss.org/)

2. Rozbijamy pliki less na logiczną strukturę np.
   - reset.less     #reset
   - variables.less #zmienne takie jak kolory, czcionki, gradienty itp. (http://lesscss.org/#-variables)
   - mixins.less    #funkcje takie jak zaokraglenia, cienie, gradienty itp. (http://lesscss.org/#-parametric-mixins)
   - layout.less    #layout  struktura
   - typo.less      #typografia
   - sprites.less   #sprajty wszystko co graficzne - ikony itp.
   itd. logiczny podział - tabele osobno, formularze osobno itp. Dodatkowo jeśli jakiś konkretny moduł wymaga indywidualnego stylowania
   zamykamy to w osobnym pliku z odpowiednim namespace np #magazines (zagnieżdzamy klasy http://lesscss.org/#-nested-rules)

3. Staramy się nie powielać cssów tylko stosować mixiny (http://lesscss.org/#-mixins)

4. Elementy warte skomentowania komentujemy jako single-line, less wycina je przy kompilacji (http://lesscss.org/#-comments)

5. Style w less wcinamy na 4 spacje

6. Klasy nazywamy z podkreślnikami (class="my_class"), id poprzez camel case (id="fooBar")