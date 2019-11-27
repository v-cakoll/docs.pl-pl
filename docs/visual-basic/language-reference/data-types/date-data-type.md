---
title: Date, typ danych
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
ms.openlocfilehash: 972df72874753a0f1213f3a4942468c59e3913ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344028"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="91d52-102">Date — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91d52-102">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="91d52-103">Zawiera wartości IEEE 64-bit (8-bajtowe), które reprezentują daty od 1 stycznia roku 0,001 do 31 grudnia roku 9999 i godziny od 12:00:00 AM (północy) do 11:59:59.9999999 PM.</span><span class="sxs-lookup"><span data-stu-id="91d52-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="91d52-104">Każdy przyrost reprezentuje 100 nanosekund czasu, który upłynął od początku 1 stycznia roku 1 w kalendarzu gregoriańskim.</span><span class="sxs-lookup"><span data-stu-id="91d52-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="91d52-105">Wartość maksymalna reprezentuje 100 nanosekund przed początkiem 1 stycznia roku 10000.</span><span class="sxs-lookup"><span data-stu-id="91d52-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="91d52-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91d52-106">Remarks</span></span>

<span data-ttu-id="91d52-107">Użyj `Date` typ danych, aby zawierać wartości daty, wartości godzinowe lub wartości daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="91d52-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="91d52-108">Wartość domyślna `Date` to 0:00:00 (północ) 1 stycznia 0001.</span><span class="sxs-lookup"><span data-stu-id="91d52-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="91d52-109">Bieżącą datę i godzinę można uzyskać z klasy <xref:Microsoft.VisualBasic.DateAndTime>.</span><span class="sxs-lookup"><span data-stu-id="91d52-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="91d52-110">Wymagania dotyczące formatu</span><span class="sxs-lookup"><span data-stu-id="91d52-110">Format Requirements</span></span>

<span data-ttu-id="91d52-111">W znakach liczbowych (`# #`) należy ująć literał `Date`.</span><span class="sxs-lookup"><span data-stu-id="91d52-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="91d52-112">Należy określić wartość daty w formacie M/d/rrrr, na przykład `#5/31/1993#`lub RRRR-MM-DD, na przykład `#1993-5-31#`.</span><span class="sxs-lookup"><span data-stu-id="91d52-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="91d52-113">Możesz użyć ukośników, aby określić rok jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="91d52-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="91d52-114">Ten wymóg jest niezależny od ustawień regionalnych i formatu daty i godziny na komputerze.</span><span class="sxs-lookup"><span data-stu-id="91d52-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="91d52-115">Przyczyną tego ograniczenia jest fakt, że znaczenie kodu nigdy nie zmienia się w zależności od ustawień regionalnych, w których działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="91d52-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="91d52-116">Załóżmy, że twardy kod `Date` literał `#3/4/1998#` i jego znaczenie będzie miało wartość 4 marca 1998.</span><span class="sxs-lookup"><span data-stu-id="91d52-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="91d52-117">W ustawieniach regionalnych, które wykorzystują mm/dd/rrrr, 3/4/1998 kompiluje się zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="91d52-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="91d52-118">Należy jednak wdrożyć aplikację w wielu krajach/regionach.</span><span class="sxs-lookup"><span data-stu-id="91d52-118">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="91d52-119">W ustawieniach regionalnych, które używają dd/mm/rrrr, zakodowany literał zostałby skompilowany do 3 kwietnia 1998.</span><span class="sxs-lookup"><span data-stu-id="91d52-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="91d52-120">W ustawieniach regionalnych, które używają rrrr/mm/dd, literał byłby nieprawidłowy (kwiecień 1998, 0003) i powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="91d52-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="91d52-121">Rozwiązania</span><span class="sxs-lookup"><span data-stu-id="91d52-121">Workarounds</span></span>

<span data-ttu-id="91d52-122">Aby skonwertować `Date` literał do formatu ustawień regionalnych lub do formatu niestandardowego, podaj literał do funkcji <xref:Microsoft.VisualBasic.Strings.Format%2A>, określając wstępnie zdefiniowany lub zdefiniowany przez użytkownika format daty.</span><span class="sxs-lookup"><span data-stu-id="91d52-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="91d52-123">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="91d52-123">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="91d52-124">Alternatywnie można użyć jednego z przeciążonych konstruktorów struktury <xref:System.DateTime> do złożenia wartości daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="91d52-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="91d52-125">Poniższy przykład tworzy wartość reprezentującą 31 maja 1993 w dniu 12:14.</span><span class="sxs-lookup"><span data-stu-id="91d52-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="91d52-126">Format godziny</span><span class="sxs-lookup"><span data-stu-id="91d52-126">Hour Format</span></span>

<span data-ttu-id="91d52-127">Możesz określić wartość czasu w formacie 12-godzinnym lub 24-godzinnym, na przykład `#1:15:30 PM#` lub `#13:15:30#`.</span><span class="sxs-lookup"><span data-stu-id="91d52-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="91d52-128">Jeśli jednak nie określisz minut lub sekund, musisz określić wartość AM lub PM.</span><span class="sxs-lookup"><span data-stu-id="91d52-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="91d52-129">Wartości domyślne daty i godziny</span><span class="sxs-lookup"><span data-stu-id="91d52-129">Date and Time Defaults</span></span>

<span data-ttu-id="91d52-130">Jeśli nie dołączysz daty w literale Data/godzina, Visual Basic ustawia część daty z wartości na 1 stycznia 0,001.</span><span class="sxs-lookup"><span data-stu-id="91d52-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="91d52-131">Jeśli nie dołączysz czasu do literału daty/godziny, Visual Basic ustawia część czasu wartości na początku dnia, czyli północy (0:00:00).</span><span class="sxs-lookup"><span data-stu-id="91d52-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="91d52-132">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="91d52-132">Type Conversions</span></span>

<span data-ttu-id="91d52-133">Jeśli przekonwertujesz wartość `Date` na typ `String`, Visual Basic renderuje datę zgodnie z formatem daty krótkiej określonym przez ustawienia regionalne czasu wykonywania i renderuje godzinę zgodnie z formatem czasu (12-godzinnym lub 24-godzinnym) określonym przez ustawienia regionalne czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="91d52-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="91d52-134">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="91d52-134">Programming Tips</span></span>

- <span data-ttu-id="91d52-135">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="91d52-135">**Interop Considerations.**</span></span> <span data-ttu-id="91d52-136">Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że typy daty i godziny w innych środowiskach nie są zgodne z typem `Date` Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="91d52-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="91d52-137">Jeśli przekazujesz argument daty/godziny do takiego składnika, zadeklaruj go jako `Double` zamiast `Date` w nowym kodzie Visual Basic i użyj metod konwersji <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> i <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91d52-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="91d52-138">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="91d52-138">**Type Characters.**</span></span> <span data-ttu-id="91d52-139">`Date` nie ma znaku typu literału lub typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="91d52-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="91d52-140">Jednak kompilator traktuje literały ujęte w znaki liczbowe (`# #`) jako `Date`.</span><span class="sxs-lookup"><span data-stu-id="91d52-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="91d52-141">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="91d52-141">**Framework Type.**</span></span> <span data-ttu-id="91d52-142">Odpowiedni typ w .NET Framework jest strukturą <xref:System.DateTime?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91d52-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="91d52-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="91d52-143">Example</span></span>

<span data-ttu-id="91d52-144">Zmienna lub stała typu danych `Date` przechowuje zarówno datę, jak i godzinę.</span><span class="sxs-lookup"><span data-stu-id="91d52-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="91d52-145">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="91d52-145">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="91d52-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91d52-146">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="91d52-147">Typy danych</span><span class="sxs-lookup"><span data-stu-id="91d52-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="91d52-148">Standardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="91d52-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="91d52-149">Niestandardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="91d52-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="91d52-150">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="91d52-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="91d52-151">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="91d52-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="91d52-152">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="91d52-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
