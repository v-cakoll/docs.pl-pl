---
title: Date — Typ danych
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
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="d1d78-102">Date — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1d78-102">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="d1d78-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span><span class="sxs-lookup"><span data-stu-id="d1d78-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="d1d78-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span><span class="sxs-lookup"><span data-stu-id="d1d78-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="d1d78-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span><span class="sxs-lookup"><span data-stu-id="d1d78-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1d78-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1d78-106">Remarks</span></span>

<span data-ttu-id="d1d78-107">Use the `Date` data type to contain date values, time values, or date and time values.</span><span class="sxs-lookup"><span data-stu-id="d1d78-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="d1d78-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span><span class="sxs-lookup"><span data-stu-id="d1d78-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="d1d78-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span><span class="sxs-lookup"><span data-stu-id="d1d78-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="d1d78-110">Format Requirements</span><span class="sxs-lookup"><span data-stu-id="d1d78-110">Format Requirements</span></span>

<span data-ttu-id="d1d78-111">You must enclose a `Date` literal within number signs (`# #`).</span><span class="sxs-lookup"><span data-stu-id="d1d78-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="d1d78-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span><span class="sxs-lookup"><span data-stu-id="d1d78-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="d1d78-113">You can use slashes when specifying the year first.</span><span class="sxs-lookup"><span data-stu-id="d1d78-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="d1d78-114">This requirement is independent of your locale and your computer's date and time format settings.</span><span class="sxs-lookup"><span data-stu-id="d1d78-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="d1d78-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span><span class="sxs-lookup"><span data-stu-id="d1d78-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="d1d78-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span><span class="sxs-lookup"><span data-stu-id="d1d78-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="d1d78-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span><span class="sxs-lookup"><span data-stu-id="d1d78-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="d1d78-118">But suppose you deploy your application in many countries/regions.</span><span class="sxs-lookup"><span data-stu-id="d1d78-118">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="d1d78-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span><span class="sxs-lookup"><span data-stu-id="d1d78-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="d1d78-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span><span class="sxs-lookup"><span data-stu-id="d1d78-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="d1d78-121">Workarounds</span><span class="sxs-lookup"><span data-stu-id="d1d78-121">Workarounds</span></span>

<span data-ttu-id="d1d78-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span><span class="sxs-lookup"><span data-stu-id="d1d78-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="d1d78-123">The following example demonstrates this.</span><span class="sxs-lookup"><span data-stu-id="d1d78-123">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="d1d78-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span><span class="sxs-lookup"><span data-stu-id="d1d78-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="d1d78-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span><span class="sxs-lookup"><span data-stu-id="d1d78-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="d1d78-126">Hour Format</span><span class="sxs-lookup"><span data-stu-id="d1d78-126">Hour Format</span></span>

<span data-ttu-id="d1d78-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span><span class="sxs-lookup"><span data-stu-id="d1d78-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="d1d78-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span><span class="sxs-lookup"><span data-stu-id="d1d78-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="d1d78-129">Date and Time Defaults</span><span class="sxs-lookup"><span data-stu-id="d1d78-129">Date and Time Defaults</span></span>

<span data-ttu-id="d1d78-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span><span class="sxs-lookup"><span data-stu-id="d1d78-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="d1d78-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span><span class="sxs-lookup"><span data-stu-id="d1d78-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="d1d78-132">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="d1d78-132">Type Conversions</span></span>

<span data-ttu-id="d1d78-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span><span class="sxs-lookup"><span data-stu-id="d1d78-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="d1d78-134">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="d1d78-134">Programming Tips</span></span>

- <span data-ttu-id="d1d78-135">**Interop Considerations.**</span><span class="sxs-lookup"><span data-stu-id="d1d78-135">**Interop Considerations.**</span></span> <span data-ttu-id="d1d78-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span><span class="sxs-lookup"><span data-stu-id="d1d78-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="d1d78-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d1d78-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="d1d78-138">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="d1d78-138">**Type Characters.**</span></span> <span data-ttu-id="d1d78-139">`Date` has no literal type character or identifier type character.</span><span class="sxs-lookup"><span data-stu-id="d1d78-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="d1d78-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span><span class="sxs-lookup"><span data-stu-id="d1d78-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="d1d78-141">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="d1d78-141">**Framework Type.**</span></span> <span data-ttu-id="d1d78-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span><span class="sxs-lookup"><span data-stu-id="d1d78-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="d1d78-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1d78-143">Example</span></span>

<span data-ttu-id="d1d78-144">A variable or constant of the `Date` data type holds both the date and the time.</span><span class="sxs-lookup"><span data-stu-id="d1d78-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="d1d78-145">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="d1d78-145">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="d1d78-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1d78-146">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="d1d78-147">Typy danych</span><span class="sxs-lookup"><span data-stu-id="d1d78-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d1d78-148">Standardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="d1d78-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="d1d78-149">Niestandardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="d1d78-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="d1d78-150">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="d1d78-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d1d78-151">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="d1d78-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="d1d78-152">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="d1d78-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
