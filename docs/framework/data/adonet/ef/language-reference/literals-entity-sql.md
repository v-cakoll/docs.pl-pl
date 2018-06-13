---
title: Literały (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 90c065dff0f81a743cd66e224885de01f6129b56
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767326"
---
# <a name="literals-entity-sql"></a>Literały (jednostka SQL)
W tym temacie opisano [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługę literały.  
  
## <a name="null"></a>Null  
 Pusty literał jest używana do reprezentowania wartość null dla dowolnego typu. Pusty literał jest zgodny z dowolnego typu.  
  
 Wartości null bez typu mogą być tworzone przez rzutowanie za pośrednictwem literału null. Aby uzyskać więcej informacji, zobacz [RZUTOWANIA](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).  
  
 Dla reguły o tym, gdzie zwolnienia zmiennoprzecinkową literałów wartości null, mogą być używane, zobacz [literałów wartości Null i wnioskowanie o typie](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boolean  
 Literałów wartości logicznych są reprezentowane przez słowa kluczowe `true` i `false`.  
  
## <a name="integer"></a>Liczba całkowita  
 Literały całkowite może być typu <xref:System.Int32> lub <xref:System.Int64>. <xref:System.Int32> Literału ciągu znaków liczbowych jest. <xref:System.Int64> Literału jest szereg liczbową znaków, wielkie litery L.  
  
## <a name="decimal"></a>Wartość dziesiętna  
 Numer stałoprzecinkowe (dziesiętna) jest ciąg znaków liczbowych, kropkę (.) i innej serii liczbową znaków, wielkie litery "M".  
  
## <a name="float-double"></a>Float, Double  
 Podwójnej precyzji liczba zmiennoprzecinkowa jest szereg cyfry, kropki (.) oraz innej serii cyfr prawdopodobnie następuje wykładnik. Opisie pojedynczego punktu numer (lub float) jest liczbą zmiennoprzecinkową podwójnej precyzji zmiennoprzecinkowa numer składnia następuje f małe litery.  
  
## <a name="string"></a>String  
 Ciąg jest ciąg znaków ujęta w znaki cudzysłowu. Cudzysłowy może być albo obu pojedynczej oferty (`'`) lub obie podwójnych cudzysłowów ("). Literały ciągu znaków może być Unicode lub z systemem innym niż Unicode. Deklarowanie literałów jako Unicode ciąg znaków, prefiks literału z wielkimi literami "N". Wartość domyślna to literałów ciągów znaków innych niż Unicode. Nie może istnieć bez spacji między N a ładunek literału ciągu, a N muszą być pisane wielkimi literami.  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DataGodzina  
 Literale datetime jest niezależna od ustawień regionalnych i składa się z części daty i czasu. Części zarówno data i godzina są obowiązkowe i nie ma wartości domyślnej.  
  
 Część daty muszą mieć format: `YYYY` - `MM` - `DD`, gdzie `YYYY` jest wartością czterocyfrowy rok zakresu od 0001 do 9999, `MM` miesiąc od 1 do 12 i `DD` jest wartość dnia, który jest prawidłowy dla danego miesiąca `MM`.  
  
 Składnik godziny musi mieć format: `HH`:`MM`[:`SS`[.fffffff]], gdzie `HH` jest wartość godziny od 0 do 23, `MM` minuty wartość od 0 do 59 `SS` jest druga wartość od 0 do 59 i fffffff ułamkowych drugiej wartości od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamkowych części sekundy są opcjonalne. Sekund są opcjonalne, chyba że określono ułamkowych części sekundy; w takim przypadku sekund są wymagane. Jeśli nie określono sekund lub ułamkowych części sekundy, wartości domyślnej równej zero zostanie użyty.  
  
 Może być dowolną liczbę spacji między DATETIME symbol i ładunek w postaci literału, ale nie nowych wierszy.  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Godzina  
 Literału czasu jest niezależne od ustawień regionalnych i składać się tylko części czasu. Składnik godziny jest obowiązkowy i nie ma wartości domyślnej. Musi mieć format gg: mm [: SS [.fffffff]], gdzie HH jest wartość godziny od 0 do 23, minuty wartość od 0 do 59, SS jest druga wartość od 0 do 59, a fffffff jest ułamek druga wartość od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamkowych części sekundy są opcjonalne. Sekund są opcjonalne, chyba że określono ułamkowych części sekundy; w takim przypadku sekund są wymagane. Jeśli sekund lub ułamków nie są określone, wartością domyślną równą zero, zostanie użyty.  
  
 Może być dowolną liczbę spacji między symbol czasu i ładunek w postaci literału, ale nie nowych wierszy.  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 Literał datetimeoffset jest niezależne od ustawień regionalnych i składać się ze część daty, godziny i część dotyczącą przesunięcia. Wszystkie daty, godziny i przesunięcia części są obowiązkowe i nie ma wartości domyślnej. Data część musi mieć format RRRR-MM-DD, gdzie RRRR jest wartością czterocyfrowy rok zakresu od 0001 do 9999, miesiąc od 1 do 12, a DD jest wartość dnia, który jest prawidłowy dla danego miesiąca. Składnik godziny musi mieć format gg: mm [: SS [.fffffff]], gdzie HH jest wartość godziny między 0 a 23, MM minuty wartość między 0 a 59, SS jest druga wartość od 0 do 59 i fffffff jest ułamkowych drugiej wartości od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamkowych części sekundy są opcjonalne. Sekund są opcjonalne, chyba że określono ułamkowych części sekundy; w takim przypadku sekund są wymagane. Jeśli sekund lub ułamków nie są określone, wartością domyślną równą zero, zostanie użyty. Części przesunięcia musi mieć format {+&#124;-} gg: mm, gdzie HH i MM mają takie samo znaczenie jak składnik godziny. Zakres przesunięcia, jednak musi należeć do zakresu od -14:00 i + 14:00  
  
 Może być dowolną liczbę spacji między DATETIMEOFFSET symbol i ładunek w postaci literału, ale nie nowych wierszy.  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  Nieprawidłowa wartość literału SQL jednostki można wykracza poza obsługiwanych zakresów dla CLR lub źródła danych. Może to spowodować wyjątek  
  
## <a name="binary"></a>plików binarnych  
 Literał ciągu binarnego jest sekwencją cyfry szesnastkowe rozdzielone apostrofy po słowie kluczowym binarnego lub symbol skrótu `X` lub `x`. Symbol skrótu `X` nie uwzględnia wielkości liter. Zero lub więcej spacji między słowem kluczowym `binary` i wartości ciągu binarnego.  
  
 Znaki szesnastkowe są również bez uwzględniania wielkości liter. Jeśli literał składa się z nieparzysta liczba cyfr szesnastkowych, literał zostaną porównane do następnego nawet szesnastkową wartością cyfrową, prefiksu literal o szesnastkowego zero cyfr. Nie ma żadnego limitu posiadanie na rozmiar ciągu binarnego.  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Identyfikator GUID  
 A `GUID` Literał reprezentuje unikatowy identyfikator globalny. Jest sekwencję utworzoną przez słowo kluczowe `GUID` następuje cyfry szesnastkowe w formularzu, znany jako *rejestru* format: 8-4-4-4-12 ujęta w apostrofy. Cyfry szesnastkowe są bez uwzględniania wielkości liter.  
  
 Może być dowolną liczbę spacji między symbol identyfikator GUID i ładunek w postaci literału, ale nie nowych wierszy.  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
