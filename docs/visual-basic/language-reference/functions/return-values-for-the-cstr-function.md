---
title: Zwracane wartości dla funkcji CStr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930047"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="2c3a4-102">Zwracane wartości dla funkcji CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c3a4-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="2c3a4-103">W poniższej tabeli opisano wartości zwracane dla `CStr` różnych `expression`typów danych.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="2c3a4-104">Jeśli `expression` typ jest</span><span class="sxs-lookup"><span data-stu-id="2c3a4-104">If `expression` type is</span></span>|<span data-ttu-id="2c3a4-105">`CStr`typu</span><span class="sxs-lookup"><span data-stu-id="2c3a4-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="2c3a4-106">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="2c3a4-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="2c3a4-107">Ciąg zawierający wartość "true" lub "false".</span><span class="sxs-lookup"><span data-stu-id="2c3a4-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="2c3a4-108">Date, typ danych</span><span class="sxs-lookup"><span data-stu-id="2c3a4-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="2c3a4-109">Ciąg zawierający `Date` wartość (Data i godzina) w formacie daty krótkiej systemu.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="2c3a4-110">Typy danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="2c3a4-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="2c3a4-111">Ciąg reprezentujący liczbę.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="2c3a4-112">CStr i Data</span><span class="sxs-lookup"><span data-stu-id="2c3a4-112">CStr and Date</span></span>  
 <span data-ttu-id="2c3a4-113">`Date` Typ zawsze zawiera informacje o dacie i godzinie.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="2c3a4-114">Na potrzeby konwersji typów Visual Basic uznaje, że 1/1/0001 (1 stycznia roku 1) jest *wartością neutralną* dla daty oraz 00:00:00 (północy) jako wartość neutralną czasu.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="2c3a4-115">`CStr`nie uwzględnia neutralnych wartości w ciągu będącym wynikiem.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="2c3a4-116">Na przykład w przypadku konwersji `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 am"; informacje o dacie są pomijane.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="2c3a4-117">Jednak informacje o dacie są nadal obecne w pierwotnej `Date` wartości i mogą być odzyskiwane za pomocą funkcji, takich jak. <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A></span><span class="sxs-lookup"><span data-stu-id="2c3a4-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c3a4-118">`CStr` Funkcja wykonuje konwersję w oparciu o bieżące ustawienia kultury dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="2c3a4-119">Aby uzyskać ciąg reprezentujący liczbę w określonej kulturze, użyj `ToString(IFormatProvider)` metody Number.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="2c3a4-120">Na przykład, użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na `String`.</span><span class="sxs-lookup"><span data-stu-id="2c3a4-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3a4-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c3a4-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="2c3a4-122">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="2c3a4-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="2c3a4-123">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="2c3a4-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="2c3a4-124">Date, typ danych</span><span class="sxs-lookup"><span data-stu-id="2c3a4-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
