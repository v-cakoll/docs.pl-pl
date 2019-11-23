---
title: Literały (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: e07dd3217e133fff98beb11ecad47e1474e4974a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319663"
---
# <a name="literals-entity-sql"></a>Literały (Entity SQL)
W tym temacie opisano obsługę [!INCLUDE[esql](../../../../../../includes/esql-md.md)] literałów.  
  
## <a name="null"></a>Null  
 Literał null jest używany do reprezentowania wartości null dla dowolnego typu. Literał o wartości null jest zgodny z dowolnym typem.  
  
 Wpisane wartości null mogą być tworzone przez rzutowanie w postaci literału o wartości null. Aby uzyskać więcej informacji, zobacz [Cast](cast-entity-sql.md).  
  
 Aby uzyskać reguły dotyczące miejsca, w którym można używać bezpłatnych zmiennoprzecinkowych literałów null, zobacz [literały null i wnioskowanie typów](null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boolean  
 Literały logiczne są reprezentowane przez słowa kluczowe `true` i `false`.  
  
## <a name="integer"></a>Liczba całkowita  
 Literały całkowite mogą być typu <xref:System.Int32> lub <xref:System.Int64>. Literał <xref:System.Int32> jest serią znaków numerycznych. Literał <xref:System.Int64> to seria znaków liczbowych, po których następuje Wielka litera L.  
  
## <a name="decimal"></a>Wartość dziesiętna  
 Liczba stałych punktów (Decimal) to seria znaków numerycznych, kropki (.) i kolejnej serii znaków liczbowych, po których występuje wielkie litery "M".  
  
## <a name="float-double"></a>Float, Double  
 Liczba zmiennoprzecinkowa o podwójnej precyzji to seria znaków liczbowych, kropki (.) i kolejnej serii znaków numerycznych, które mogą być stosowane w wykładniku. Liczba zmiennoprzecinkowa o pojedynczej precyzji (lub zmiennoprzecinkowa) to składnia liczb zmiennoprzecinkowych o podwójnej precyzji, po której następuje mała litera f.  
  
## <a name="string"></a>String  
 Ciąg jest serią znaków ujętych w znaki cudzysłowu. Cudzysłowy mogą być zarówno pojedynczymi cudzysłowami (`'`), jak i podwójnych cudzysłowów ("). Literały ciągu znaków mogą być w formacie Unicode lub innym niż Unicode. Aby zadeklarować literał ciągu znaków jako Unicode, poprzedź literał literałem "N". Wartość domyślna to literały ciągu znaków inne niż Unicode. Nie może zawierać spacji między znakiem N i ładunkiem literału ciągu, a N musi być wielką literą.  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DataGodzina  
 Literał DateTime jest niezależny od ustawień regionalnych i składa się z części daty i części czasu. Części daty i godziny są obowiązkowe i nie ma wartości domyślnych.  
  
 Część daty musi mieć format: `YYYY`-`MM`-`DD`, gdzie `YYYY` jest wartością czterech cyfr rocznie z zakresu od 0,001 do 9999, `MM` jest miesiąc między 1 a 12, a `DD` to wartość dnia obowiązująca dla danego miesiąca `MM`.  
  
 Część godziny musi mieć format: `HH`:`MM`[:`SS`[. fffffff]], gdzie `HH` jest wartością godziny z przedziału od 0 do 23, `MM` jest wartością minutową z zakresu od 0 do 59, `SS` to druga wartość z zakresu od 0 do 59, a fffffff to ułamkowa druga wartość z zakresu od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamki sekund są opcjonalne. Sekundy są opcjonalne, chyba że określono ułamki sekund; w takim przypadku wymagane są sekundy. Gdy nie określono sekund lub ułamków sekund, zamiast tego zostanie użyta wartość domyślna zero.  
  
 Między symbolem DATETIME i ładunkiem literału może być dowolna liczba spacji, ale nie ma żadnych nowych wierszy.  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Time  
 Literał czasu jest niezależny od ustawień regionalnych i składa się tylko z części czasu. Część czasu jest obowiązkowa i nie ma wartości domyślnej. Musi mieć format gg: MM [: SS [. fffffff]], gdzie HH jest wartością godzinową z zakresu od 0 do 23, MM jest wartością minuty z przedziału od 0 do 59, SS jest drugą wartością z zakresu od 0 do 59, a fffffff jest drugą wartością ułamkową z zakresu od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamki sekund są opcjonalne. Sekundy są opcjonalne, chyba że określono ułamki sekund; w takim przypadku wymagane są sekundy. Gdy nie określono sekund lub ułamków, zamiast tego zostanie użyta wartość domyślna zero.  
  
 Między symbolem czasu a ładunkiem literału może być dowolna liczba spacji, ale nie ma żadnych nowych wierszy.  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 Literał DateTimeOffset jest niezależny od ustawień regionalnych i składa się z części daty, części czasu i przesunięcia. Wszystkie części daty, godziny i przesunięcia są obowiązkowe i nie ma wartości domyślnych. Część daty musi mieć format RRRR-MM-DD, gdzie RRRR jest wartością czterech cyfr rok w przedziale od 0,001 do 9999, MM to miesiąc z przedziału od 1 do 12, a DD to wartość dnia, która jest ważna dla danego miesiąca. Część godziny musi mieć format gg: MM [: SS [. fffffff]], gdzie HH jest wartością godzinową z zakresu od 0 do 23, MM jest wartością minuty z przedziału od 0 do 59, SS jest drugą wartością z zakresu od 0 do 59, a fffffff to ułamkowa druga wartość z zakresu od 0 do 9999999. Wszystkie zakresy wartości są włącznie. Ułamki sekund są opcjonalne. Sekundy są opcjonalne, chyba że określono ułamki sekund; w takim przypadku wymagane są sekundy. Gdy nie określono sekund lub ułamków, zamiast tego zostanie użyta wartość domyślna zero. Część przesunięcia musi mieć format {+&#124;-} hh: mm, gdzie HH i mm mają takie samo znaczenie jak w części czasu. Zakres przesunięcia musi jednak zawierać się w przedziale od-14:00 do + 14:00  
  
 Między symbolem DATETIMEOFFSET a ładunkiem literału może być dowolna liczba spacji, ale nie ma żadnych nowych wierszy.  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> Prawidłowa wartość literału Entity SQL może przypadać poza obsługiwane zakresy dla środowiska CLR lub źródła danych. Może to spowodować powstanie wyjątku  
  
## <a name="binary"></a>plików binarnych  
 Binarny literał ciągu jest sekwencją cyfr szesnastkowych, które są rozdzielane pojedynczymi cudzysłowami po słowie kluczowym słowo kluczowe lub symbolem skrótu `X` lub `x`. Symbol skrótu `X` nie uwzględnia wielkości liter. Między słowem kluczowym `binary` i wartością ciągu binarnego jest dozwolona zero lub więcej spacji.  
  
 W znakach szesnastkowych również jest rozróżniana wielkość liter. Jeśli literał składa się z nieparzystej liczby cyfr szesnastkowych, literał zostanie wyrównany do następnej parzystej cyfry szesnastkowej przez prefiks literału z szesnastkową cyfrą zero. Brak formalnego limitu rozmiaru ciągu binarnego.  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Guid  
 Literał `GUID` reprezentuje globalnie unikatowy identyfikator. Jest to sekwencja utworzona za pomocą słowa kluczowego `GUID`, a następnie cyfry szesnastkowe w formularzu znanym jako format *rejestru* : 8-4-4-4-12 ujęte w apostrofy. W przypadku cyfr szesnastkowych wielkość liter nie jest rozróżniana.  
  
 Między symbolem GUID a ładunkiem literału może być dowolna liczba spacji, ale nie ma żadnych nowych wierszy.  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
