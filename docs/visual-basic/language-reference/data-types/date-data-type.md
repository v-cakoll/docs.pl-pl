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
ms.openlocfilehash: 32bd0912b0bae3340cffed010fc67431d0efb376
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027755"
---
# <a name="date-data-type-visual-basic"></a>Date — Typ danych (Visual Basic)
Przechowuje wartości (8-bajtową) IEEE 64-bitowych, które reprezentują w zakresie od 1 stycznia 0001 roku do 31 grudnia 9999 roku daty i godziny od 0:00:00: 00 (północ) za pośrednictwem 11:59:59.9999999 PM. Każdy przyrost reprezentuje 100 nanosekund czas, który upłynął od początku 1 stycznia 1 roku w kalendarzu gregoriańskim. Maksymalna wartość reprezentuje 100 nanosekund przed rozpoczęciem 1 stycznia roku 10000.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Date` typu danych, które zawierają wartości dat, wartości czasu lub wartości daty i godziny.  
  
 Wartość domyślna `Date` wynosi 0:00:00 (północ), 1 stycznia 0001.  
  
 Możesz uzyskać bieżącą datę i godzinę, z <xref:Microsoft.VisualBasic.DateAndTime> klasy.  
  
## <a name="format-requirements"></a>Wymagania dotyczące formatu  
 Należy ująć `Date` literału w ramach krzyżyki (`# #`). Należy określić wartość daty w formacie M/d/rrrr, na przykład `#5/31/1993#`, lub RRRR MM-dd, na przykład `#1993-5-31#`. Podczas określania roku najpierw, można używać ukośników.  To wymaganie jest niezależne od ustawień regionalnych użytkownika i komputera ustawienia daty i godziny formatu.  
  
 Przyczyną tego ograniczenia to, że znaczenie kod nigdy nie należy zmieniać w zależności od ustawień regionalnych, w którym aplikacja jest uruchomiona. Załóżmy, że należy trwale kodować `Date` literału `#3/4/1998#` i ma on oznacza 4 marca 1998 r. W ustawieniach regionalnych, który używa mm/dd/rrrr 3/4/1998 kompiluje, jak planowane. Jednak Załóżmy, że możesz wdrożyć aplikację w wielu krajach. W ustawieniach regionalnych, który używa dd/mm/rrrr literał swoje zakodowane będzie kompilacji do 3 kwietnia 1998 r. W ustawieniach regionalnych, który używa rrrr/mm/dd, literał byłyby nieprawidłowe (kwiecień 1998 0003) i spowodują błąd kompilatora.  
  
## <a name="workarounds"></a>Rozwiązania  
 Aby przekonwertować `Date` literał format ustawień regionalnych lub formatu niestandardowego, podaj literału do <xref:Microsoft.VisualBasic.Strings.Format%2A> funkcji, określając format daty wstępnie zdefiniowanych lub zdefiniowanych przez użytkownika. Poniższy przykład przedstawia to.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Alternatywnie możesz użyć jednej z przeciążenia konstruktorów z <xref:System.DateTime> struktury, aby zestawić wartości daty i godziny. Poniższy przykład tworzy wartość do reprezentowania 31 maja 1993 o 12:14 po południu.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>Format godziny  
 Można określić wartość godziny w formacie 12-godzinny lub 24-godzinnym, na przykład `#1:15:30 PM#` lub `#13:15:30#`. Jednakże jeśli nie określisz, minuty lub sekundy, należy określić AM lub PM.  
  
## <a name="date-and-time-defaults"></a>Daty i godziny wartości domyślne  
 Jeśli wartość typu date nie zostanie uwzględniony w daty/godziny literału, Visual Basic ustawia składnik daty z wartości na 1 stycznia 0001. Jeśli nie zostanie uwzględniony czas w literał daty/godziny, Visual Basic ustawia składnik godziny z wartości na początku dnia, oznacza to, o północy (0: 00:00).  
  
## <a name="type-conversions"></a>Konwersje typu  
 Po skonwertowaniu `Date` wartość `String` typu, Visual Basic powoduje wyświetlenie daty zgodnie z formatu daty krótkiej, określony przez ustawienia regionalne czasu wykonywania i renderowania czas zgodnie z format godziny (12-godzinny lub 24-godzinny), określony przez Ustawienia regionalne czasu wykonywania.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Uwagi dotyczące współdziałania.** Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać, że typy w innych środowiskach daty/godziny, nie są zgodne z języka Visual Basic `Date` typu. Jeśli przekazujesz argumentu daty/godziny do takiego składnika, Zadeklaruj go jako `Double` zamiast `Date` Twojego nowego języka Visual Basic w kodzie oraz użyć metody konwersji <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> i <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.  
  
-   **Znaki typu.** `Date` nie ma znak literalny typu lub znak typu identyfikator. Jednak kompilator traktuje literały ujęty w znaki cyfry (`# #`) jako `Date`.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.DateTime?displayProperty=nameWithType> struktury.  
  
## <a name="example"></a>Przykład  
 Zmienną lub stałą `Date` — typ danych przechowuje daty i godziny. Ilustruje to poniższy przykład.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Standardowe ciągi formatujące datę i godzinę](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [Niestandardowe ciągi formatujące datę i godzinę](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
