---
title: Literały (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: bff9b1907d3424dc2e3df80480b6ab12f5ab9261
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760665"
---
# <a name="literals-entity-sql"></a>Literały (jednostka SQL)
W tym temacie opisano [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Obsługa literałów.  
  
## <a name="null"></a>Null  
 Literał null jest używana do reprezentowania wartość null dla dowolnego typu. Literał null jest zgodny z dowolnego typu.  
  
 Wpisane wartości null, mogą być tworzone przez rzutowanie nad literałem o wartości null. Aby uzyskać więcej informacji, zobacz [RZUTOWANIA](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).  
  
 Dla reguły o tym, gdzie bezpłatne liczb zmiennoprzecinkowych literały null może być używany, zobacz [literały Null i wnioskowanie o typie](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boolean  
 Stałe logiczne są reprezentowane przez słowa kluczowe `true` i `false`.  
  
## <a name="integer"></a>Liczba całkowita  
 Literały całkowite mogą być typu <xref:System.Int32> lub <xref:System.Int64>. <xref:System.Int32> To seria znaków literału. <xref:System.Int64> Literał jest szereg znaki numeryczne wielkie L.  
  
## <a name="decimal"></a>Wartość dziesiętna  
 Stałoprzecinkowa liczba (dziesiętna) jest szereg cyfry, kropki (.) i innej serii znaki numeryczne wielkie litery "M".  
  
## <a name="float-double"></a>Float, Double  
 Podwójnej precyzji liczba zmiennoprzecinkowa jest szereg cyfry, kropki (.) oraz innej serii znaki numeryczne, prawdopodobnie następuje wykładnik. Jednym zakresie liczby (lub float) jest zmiennoprzecinkową podwójnej precyzji moment zmiennoprzecinkowa numer składni następuje mała litera f.  
  
## <a name="string"></a>String  
 Ciąg jest ciąg znaków, ujęte w znaki cudzysłowu. Oferty mogą być albo obu pojedynczej oferty (`'`) lub obu podwójne cudzysłowy ("). Literały ciągów znaków może być Unicode lub innego niż Unicode. Aby zadeklarować ciąg znaków literału jako Unicode, prefiks literału z wielkimi literami "N". Wartość domyślna to literały ciągów znaków standardu Unicode. Może istnieć bez spacji między N a ładunek literału ciągu i N muszą być pisane dużą literą.  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DataGodzina  
 Literał daty / godziny jest niezależna od ustawień regionalnych i składa się z części daty i godziny. Części daty i godziny są obowiązkowe, a nie znajdują się domyślne wartości.  
  
 Część daty, musi mieć format: `YYYY` - `MM` - `DD`, gdzie `YYYY` jest wartością rok czterocyfrowej z zakresu od 0001 do 9999, `MM` miesiąca od 1 do 12 i `DD` jest wartość dnia, który jest prawidłowy w danym miesiącu `MM`.  
  
 Składnik godziny musi mieć format: `HH`:`MM`[:`SS`[.fffffff]], gdzie `HH` to wartość godziny w zakresie od 0 do 23, `MM` jest minuty wartość z zakresu od 0 do 59 `SS` jest druga wartość od 0 do 59 i fffffff ułamkowe drugiej wartości od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamków sekund jest opcjonalne. Sekundy są opcjonalne, chyba że określono ułamków sekund; w tym przypadku sekund są wymagane. Jeśli nie określono sekund lub ułamków sekund, wartość domyślna równa zero zostanie użyty.  
  
 Może być dowolną liczbę spacji między symbol daty/godziny i ładunek w postaci literału, ale nie nowe wiersze.  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Godzina  
 Literału czasu jest niezależne od ustawień regionalnych, składa się z tylko część czas. Składnik godziny jest obowiązkowy i nie ma wartości domyślnej. Musi on mieć format gg: mm [: SS [.fffffff]], gdzie HH jest wartość godziny w zakresie od 0 do 23, minuty wartości od 0 do 59, SS jest druga wartość od 0 do 59, a fffffff jest część druga wartość od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamków sekund jest opcjonalne. Sekundy są opcjonalne, chyba że określono ułamków sekund; w tym przypadku sekund są wymagane. Gdy nie są określone jako ułamki lub sekundach, wartość domyślna równa zero zostanie użyty.  
  
 Może być dowolną liczbę spacji między symbol czasu i ładunek w postaci literału, ale nie nowe wiersze.  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 Literał datetimeoffset jest niezależne od ustawień regionalnych, składa się z część daty, składnik godziny i części przesunięcia. Wszystkie daty, godziny i przesunięcia części są obowiązkowe, a nie znajdują się domyślne wartości. Data część musi mieć format RRRR-MM-DD, rrrr przypadku wartość rok czterocyfrowej z zakresu od 0001 do 9999, miesiąc od 1 do 12, a DD jest wartość dnia, który jest prawidłowy w danym miesiącu. Składnik godziny musi mieć format gg: mm [: SS [.fffffff]], gdzie HH jest wartość godziny od 0 do 23, m-minutowego wartość z zakresu od 0 do 59, SS jest druga wartość od 0 do 59 i fffffff jest ułamkowe drugiej wartości od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamków sekund jest opcjonalne. Sekundy są opcjonalne, chyba że określono ułamków sekund; w tym przypadku sekund są wymagane. Gdy nie są określone jako ułamki lub sekundach, wartość domyślna równa zero zostanie użyty. Części przesunięcia musi mieć format {+&#124;-} gg: mm, gdzie HH i MM mają takie samo znaczenie jak składnik godziny. Zakres przesunięcia, jednak musi należeć do zakresu od -14:00 a + 14:00  
  
 Może być dowolną liczbę spacji między DATETIMEOFFSET symbol i ładunek w postaci literału, ale nie nowe wiersze.  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  Nieprawidłowa wartość literału jednostki SQL można wykracza poza obsługiwanych zakresów dla środowiska CLR lub źródła danych. Może to prowadzić do wyjątku  
  
## <a name="binary"></a>plików binarnych  
 Literał ciągu binarnego jest sekwencją cyfry szesnastkowe rozdzielone pojedynczego apostrofu, po słowie kluczowym binarne lub symbol skrótu `X` lub `x`. Symbol skrótu `X` jest uwzględniana wielkość liter. Zero lub więcej spacji między słowem kluczowym `binary` i wartość ciągu binarnego.  
  
 Znaki szesnastkowe są również bez uwzględniania wielkości liter. Jeśli literał składa się z nieparzysta liczba cyfr szesnastkowych, literału mają zostać wyrównane do kolejną cyfrą szesnastkową nawet przez dodanie przedrostka właściwość literal o szesnastkowego cyfra zero. Nie ma żadnego formalne limitu rozmiaru ciąg binarny.  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Guid  
 A `GUID` Literał reprezentuje unikatowy identyfikator globalny. Jest sekwencją utworzone przez słowo kluczowe `GUID` i cyfry szesnastkowe w formularzu, znane jako *rejestru* formatu: 8-4-4-4-12 ujęta w apostrofy. Cyfry szesnastkowe jest rozróżniana wielkość liter.  
  
 Może być dowolną liczbę spacji między symbol identyfikator GUID i ładunek w postaci literału, ale nie nowe wiersze.  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
