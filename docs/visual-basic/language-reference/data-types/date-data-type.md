---
title: Date — Typ danych (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: b7827206d6e145b559d9716df5ec4a98ac4ea0b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591823"
---
# <a name="date-data-type-visual-basic"></a>Date — Typ danych (Visual Basic)
Przechowuje wartości (8-bajtowych) IEEE 64-bitowe, które reprezentują z zakresu od 1 stycznia 0001 roku do 31 grudnia 9999 roku daty i godziny od 00:00:00: 00 (północ) za pośrednictwem 11:59:59.9999999 PM. Jednostka reprezentuje 100 nanosekundach czas, który upłynął od początku 1 stycznia 1 rok kalendarza gregoriańskiego. Maksymalna wartość reprezentuje 100 nanosekundach przed rozpoczęciem 1 stycznia roku 10000.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Date` — typ danych zawierający wartości daty, wartości godziny lub wartości daty i godziny.  
  
 Wartość domyślna `Date` 0:00:00 (północ) 1 stycznia 0001.  
  
 Można uzyskać bieżącą datę i godzinę z <xref:Microsoft.VisualBasic.DateAndTime> klasy.  
  
## <a name="format-requirements"></a>Wymagania dotyczące formatu  
 Musisz ją ująć `Date` literału w znaki numeru (`# #`). Należy określić wartość daty w formacie M/d/rrrr, na przykład `#5/31/1993#`, lub RRRR MM-dd, na przykład `#1993-5-31#`. Można użyć ukośniki, określając roku najpierw.  To wymaganie jest niezależne od ustawień regionalnych użytkownika i komputera ustawienia daty i godziny format.  
  
 Przyczyna to ograniczenie jest, że znaczenie kodu nigdy nie należy zmieniać w zależności od ustawień regionalnych, w którym aplikacja jest uruchomiona. Załóżmy, że należy trwale kodować `Date` literału z `#3/4/1998#` i ma on oznacza 4 marca 1998. W ustawieniach regionalnych mm/dd/rrrr 3/4/1998 kompiluje jako planowane. Ale Załóżmy, że w przypadku wdrażania aplikacji w wielu krajach. W ustawieniach regionalnych dd/mm/rrrr literał z wpisaną na stałe będzie kompilacji do 3 kwietnia 1998. W ustawieniach regionalnych rrrr/mm/dd., może być nieważny literał (kwiecień 1998 0003) i spowodować błąd kompilatora.  
  
## <a name="workarounds"></a>Rozwiązania  
 Aby przekonwertować `Date` literał format ustawień regionalnych, lub formatu niestandardowego, podaj literał do <xref:Microsoft.VisualBasic.Strings.Format%2A> funkcja Określanie formatu daty wstępnie zdefiniowanych lub zdefiniowanych przez użytkownika. W poniższym przykładzie pokazano to.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Alternatywnie można użyć jednej przeciążone konstruktory <xref:System.DateTime> struktury gromadzi wartość daty i godziny. Poniższy przykład tworzy wartość do reprezentowania 31 maja 1993 na 12:14 po południu.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>Format godziny  
 Można określić wartość czasu w formacie 12-godzinnym lub 24-godzinnym, na przykład `#1:15:30 PM#` lub `#13:15:30#`. Jednak jeśli nie określisz, minuty i sekundy, należy określić AM lub PM.  
  
## <a name="date-and-time-defaults"></a>Data i godzina ustawienia domyślne  
 Jeśli nie obejmują datę w daty/godziny literału, Visual Basic ustawia część daty wartości 1 stycznia 0001. Jeśli nie zostanie uwzględniony czas w literale daty/godziny, Visual Basic ustawia składnik godziny z wartości na początek dnia, to znaczy północy (0: 00:00).  
  
## <a name="type-conversions"></a>Konwersje typu  
 W przypadku przekonwertowania `Date` do wartości `String` typu, Visual Basic renderuje datę ustawioną format daty krótkiej określony przez ustawienia regionalne czasu wykonywania i renderowania czasu zgodnie z formatu godziny (12-godzinnym lub 24-godzinnym) określone przez Ustawienia regionalne czasu wykonywania.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Zagadnienia dotyczące współdziałania.** Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typy w innych środowiskach daty i godziny nie są zgodne z programem Visual Basic `Date` typu. Jeśli argument daty/godziny jest przekazywany do takich składników, Zadeklaruj ją jako `Double` zamiast `Date` w nowego języka Visual Basic code, a za pomocą metody konwersji <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> i <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.  
  
-   **Znaki typu.** `Date` nie ma znak literalny typu ani znak typu identyfikator. Jednak kompilator traktuje literały ujęta w znaki numeru (`# #`) jako `Date`.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.DateTime?displayProperty=nameWithType> struktury.  
  
## <a name="example"></a>Przykład  
 Zmienna lub stała `Date` — typ danych zawiera zarówno daty i czasu. Ilustruje to poniższy przykład.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Standardowe ciągi formatujące datę i godzinę](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [Niestandardowe ciągi formatujące datę i godzinę](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
