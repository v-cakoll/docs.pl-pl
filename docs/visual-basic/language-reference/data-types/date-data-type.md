---
title: "Date — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Date
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190b40888dc4a42075b7b6b27bdb1bd403a7efb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="8bd2c-102">Date — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd2c-102">Date Data Type (Visual Basic)</span></span>
<span data-ttu-id="8bd2c-103">Przechowuje wartości (8-bajtowych) IEEE 64-bitowe, które reprezentują z zakresu od 1 stycznia 0001 roku do 31 grudnia 9999 roku daty i godziny od 00:00:00: 00 (północ) za pośrednictwem 11:59:59.9999999 PM.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="8bd2c-104">Jednostka reprezentuje 100 nanosekundach czas, który upłynął od początku 1 stycznia 1 rok kalendarza gregoriańskiego.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="8bd2c-105">Maksymalna wartość reprezentuje 100 nanosekundach przed rozpoczęciem 1 stycznia roku 10000.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd2c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bd2c-106">Remarks</span></span>  
 <span data-ttu-id="8bd2c-107">Użyj `Date` — typ danych zawierający wartości daty, wartości godziny lub wartości daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>  
  
 <span data-ttu-id="8bd2c-108">Wartość domyślna `Date` 0:00:00 (północ) 1 stycznia 0001.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>  
  
 <span data-ttu-id="8bd2c-109">Można uzyskać bieżącą datę i godzinę z <xref:Microsoft.VisualBasic.DateAndTime> klasy.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="8bd2c-110">Wymagania dotyczące formatu</span><span class="sxs-lookup"><span data-stu-id="8bd2c-110">Format Requirements</span></span>  
 <span data-ttu-id="8bd2c-111">Musisz ją ująć `Date` literału w znaki numeru (`# #`).</span><span class="sxs-lookup"><span data-stu-id="8bd2c-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="8bd2c-112">Należy określić wartość daty w formacie M/d/rrrr, na przykład `#5/31/1993#`, lub RRRR MM-dd, na przykład `#1993-5-31#`.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="8bd2c-113">Można użyć ukośniki, określając roku najpierw.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="8bd2c-114">To wymaganie jest niezależne od ustawień regionalnych użytkownika i komputera ustawienia daty i godziny format.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>  
  
 <span data-ttu-id="8bd2c-115">Przyczyna to ograniczenie jest, że znaczenie kodu nigdy nie należy zmieniać w zależności od ustawień regionalnych, w którym aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="8bd2c-116">Załóżmy, że należy trwale kodować `Date` literału z `#3/4/1998#` i ma on oznacza 4 marca 1998.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="8bd2c-117">W ustawieniach regionalnych mm/dd/rrrr 3/4/1998 kompiluje jako planowane.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="8bd2c-118">Ale Załóżmy, że w przypadku wdrażania aplikacji w wielu krajach.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-118">But suppose you deploy your application in many countries.</span></span> <span data-ttu-id="8bd2c-119">W ustawieniach regionalnych dd/mm/rrrr literał z wpisaną na stałe będzie kompilacji do 3 kwietnia 1998.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="8bd2c-120">W ustawieniach regionalnych rrrr/mm/dd., może być nieważny literał (kwiecień 1998 0003) i spowodować błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>  
  
## <a name="workarounds"></a><span data-ttu-id="8bd2c-121">Rozwiązania</span><span class="sxs-lookup"><span data-stu-id="8bd2c-121">Workarounds</span></span>  
 <span data-ttu-id="8bd2c-122">Aby przekonwertować `Date` literał format ustawień regionalnych, lub formatu niestandardowego, podaj literał do <xref:Microsoft.VisualBasic.Strings.Format%2A> funkcja Określanie formatu daty wstępnie zdefiniowanych lub zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="8bd2c-123">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-123">The following example demonstrates this.</span></span>  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 <span data-ttu-id="8bd2c-124">Alternatywnie można użyć jednej przeciążone konstruktory <xref:System.DateTime> struktury gromadzi wartość daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="8bd2c-125">Poniższy przykład tworzy wartość do reprezentowania 31 maja 1993 na 12:14 po południu.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a><span data-ttu-id="8bd2c-126">Format godziny</span><span class="sxs-lookup"><span data-stu-id="8bd2c-126">Hour Format</span></span>  
 <span data-ttu-id="8bd2c-127">Można określić wartość czasu w formacie 12-godzinnym lub 24-godzinnym, na przykład `#1:15:30 PM#` lub `#13:15:30#`.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="8bd2c-128">Jednak jeśli nie określisz, minuty i sekundy, należy określić AM lub PM.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>  
  
## <a name="date-and-time-defaults"></a><span data-ttu-id="8bd2c-129">Data i godzina ustawienia domyślne</span><span class="sxs-lookup"><span data-stu-id="8bd2c-129">Date and Time Defaults</span></span>  
 <span data-ttu-id="8bd2c-130">Jeśli nie obejmują datę w daty/godziny literału, Visual Basic ustawia część daty wartości 1 stycznia 0001.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="8bd2c-131">Jeśli nie zostanie uwzględniony czas w literale daty/godziny, Visual Basic ustawia składnik godziny z wartości na początek dnia, to znaczy północy (0: 00:00).</span><span class="sxs-lookup"><span data-stu-id="8bd2c-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="8bd2c-132">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="8bd2c-132">Type Conversions</span></span>  
 <span data-ttu-id="8bd2c-133">W przypadku przekonwertowania `Date` do wartości `String` typu, Visual Basic renderuje datę ustawioną format daty krótkiej określony przez ustawienia regionalne czasu wykonywania i renderowania czasu zgodnie z formatu godziny (12-godzinnym lub 24-godzinnym) określone przez Ustawienia regionalne czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="8bd2c-134">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="8bd2c-134">Programming Tips</span></span>  
  
-   <span data-ttu-id="8bd2c-135">**Zagadnienia dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="8bd2c-135">**Interop Considerations.**</span></span> <span data-ttu-id="8bd2c-136">Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typy w innych środowiskach daty i godziny nie są zgodne z programem Visual Basic `Date` typu.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="8bd2c-137">Jeśli argument daty/godziny jest przekazywany do takich składników, Zadeklaruj ją jako `Double` zamiast `Date` w nowego języka Visual Basic code, a za pomocą metody konwersji <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> i <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="8bd2c-138">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="8bd2c-138">**Type Characters.**</span></span> <span data-ttu-id="8bd2c-139">`Date`nie ma znak literalny typu ani znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="8bd2c-140">Jednak kompilator traktuje literały ujęta w znaki numeru (`# #`) jako `Date`.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>  
  
-   <span data-ttu-id="8bd2c-141">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="8bd2c-141">**Framework Type.**</span></span> <span data-ttu-id="8bd2c-142">Danego typu w programie .NET Framework jest <xref:System.DateTime?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bd2c-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bd2c-143">Example</span></span>  
 <span data-ttu-id="8bd2c-144">Zmienna lub stała `Date` — typ danych zawiera zarówno daty i czasu.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="8bd2c-145">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="8bd2c-145">The following example illustrates this.</span></span>  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bd2c-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bd2c-146">See Also</span></span>  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [<span data-ttu-id="8bd2c-147">Typy danych</span><span class="sxs-lookup"><span data-stu-id="8bd2c-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="8bd2c-148">Ciągi formatujące standardowa Data i godzina</span><span class="sxs-lookup"><span data-stu-id="8bd2c-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [<span data-ttu-id="8bd2c-149">Niestandardowa data i godzina ciągi formatujące</span><span class="sxs-lookup"><span data-stu-id="8bd2c-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [<span data-ttu-id="8bd2c-150">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="8bd2c-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="8bd2c-151">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="8bd2c-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="8bd2c-152">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="8bd2c-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
