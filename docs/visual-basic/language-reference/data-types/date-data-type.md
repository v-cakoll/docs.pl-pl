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
ms.openlocfilehash: ee966cdfcc957f1164c73f577fa668b203a82113
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630118"
---
# <a name="date-data-type-visual-basic"></a>Date — Typ danych (Visual Basic)

Zawiera wartości IEEE 64-bit (8-bajtowe), które reprezentują daty od 1 stycznia roku 0,001 do 31 grudnia roku 9999 i godziny od 12:00:00 AM (północy) do 11:59:59.9999999 PM. Każdy przyrost reprezentuje 100 nanosekund czasu, który upłynął od początku 1 stycznia roku 1 w kalendarzu gregoriańskim. Wartość maksymalna reprezentuje 100 nanosekund przed początkiem 1 stycznia roku 10000.

## <a name="remarks"></a>Uwagi

Użyj typu `Date` danych, aby zawierać wartości daty, wartości godzinowe lub wartości daty i godziny.

Wartość `Date` domyślna to 0:00:00 (północ) 1 stycznia 0001.

Bieżącą datę i godzinę można uzyskać z <xref:Microsoft.VisualBasic.DateAndTime> klasy.

## <a name="format-requirements"></a>Wymagania dotyczące formatu

Należy ująć `Date` literał w znakach liczbowych (`# #`). Należy określić wartość daty w formacie M/d/rrrr, na przykład `#5/31/1993#`, lub rrrr-mm-dd, na przykład. `#1993-5-31#` Możesz użyć ukośników, aby określić rok jako pierwszy.  Ten wymóg jest niezależny od ustawień regionalnych i formatu daty i godziny na komputerze.

Przyczyną tego ograniczenia jest fakt, że znaczenie kodu nigdy nie zmienia się w zależności od ustawień regionalnych, w których działa aplikacja. Załóżmy, że twardy kod `Date` `#3/4/1998#` literału i jego znaczenie ma być 4 marca 1998. W ustawieniach regionalnych, które wykorzystują mm/dd/rrrr, 3/4/1998 kompiluje się zgodnie z oczekiwaniami. Należy jednak wdrożyć aplikację w wielu krajach/regionach. W ustawieniach regionalnych, które używają dd/mm/rrrr, zakodowany literał zostałby skompilowany do 3 kwietnia 1998. W ustawieniach regionalnych, które używają rrrr/mm/dd, literał byłby nieprawidłowy (kwiecień 1998, 0003) i powoduje błąd kompilatora.

## <a name="workarounds"></a>Rozwiązania

Aby przekonwertować `Date` literał na format ustawień regionalnych lub do formatu niestandardowego, podaj literał <xref:Microsoft.VisualBasic.Strings.Format%2A> do funkcji, określając wstępnie zdefiniowany lub zdefiniowany przez użytkownika format daty. Poniższy przykład ilustruje to.

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

Alternatywnie można użyć jednego ze przeciążonych konstruktorów <xref:System.DateTime> struktury do złożenia wartości daty i godziny. Poniższy przykład tworzy wartość reprezentującą 31 maja 1993 w dniu 12:14.

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a>Format godziny

Możesz określić wartość czasu w formacie 12-godzinnym lub 24-godzinnym, na przykład `#1:15:30 PM#` lub. `#13:15:30#` Jeśli jednak nie określisz minut lub sekund, musisz określić wartość AM lub PM.

## <a name="date-and-time-defaults"></a>Wartości domyślne daty i godziny

Jeśli nie dołączysz daty w literale Data/godzina, Visual Basic ustawia część daty z wartości na 1 stycznia 0,001. Jeśli nie dołączysz czasu do literału daty/godziny, Visual Basic ustawia część czasu wartości na początku dnia, czyli północy (0:00:00).

## <a name="type-conversions"></a>Konwersje typu

W przypadku przekonwertowania `Date` wartości `String` na typ, Visual Basic renderuje datę zgodnie z formatem daty krótkiej określonym przez ustawienia regionalne czasu wykonywania i renderuje godzinę zgodnie z formatem czasu (12-godzinnym lub 24-godzinnym) określonym przez Ustawienia regionalne czasu wykonywania.

## <a name="programming-tips"></a>Porady dla programistów

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli korzystasz z składników niepisanych dla .NET Framework, na przykład obiektów automatyzacji lub com, pamiętaj, że typy daty i godziny w innych środowiskach nie są zgodne z typem Visual Basic `Date` . Jeśli przekazujesz argument `Double` daty/godziny do takiego składnika, zadeklaruj go jako `Date` zamiast w nowym kodzie Visual Basic i użyj metod <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> konwersji i <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.

- **Znaki typu.** `Date`nie ma znaku typu literału lub znaku typu identyfikatora. Jednak kompilator traktuje literały ujęte w znaki liczbowe (`# #`) jako `Date`.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.DateTime?displayProperty=nameWithType> strukturą.

## <a name="example"></a>Przykład

Zmienna lub stała `Date` typu danych przechowuje zarówno datę, jak i godzinę. Ilustruje to poniższy przykład.

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a>Zobacz także

- <xref:System.DateTime?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
