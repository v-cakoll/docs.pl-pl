---
title: Zwracane wartości dla funkcji CStr
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
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406390"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="5275d-102">Zwracane wartości dla funkcji CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5275d-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="5275d-103">W poniższej tabeli opisano wartości zwracane dla `CStr` różnych typów danych `expression` .</span><span class="sxs-lookup"><span data-stu-id="5275d-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="5275d-104">Jeśli `expression` Typ jest</span><span class="sxs-lookup"><span data-stu-id="5275d-104">If `expression` type is</span></span>|<span data-ttu-id="5275d-105">`CStr`typu</span><span class="sxs-lookup"><span data-stu-id="5275d-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="5275d-106">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="5275d-106">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="5275d-107">Ciąg zawierający wartość "true" lub "false".</span><span class="sxs-lookup"><span data-stu-id="5275d-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="5275d-108">Date, typ danych</span><span class="sxs-lookup"><span data-stu-id="5275d-108">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="5275d-109">Ciąg zawierający `Date` wartość (Data i godzina) w formacie daty krótkiej systemu.</span><span class="sxs-lookup"><span data-stu-id="5275d-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="5275d-110">Typy danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="5275d-110">Numeric Data Types</span></span>](../../programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="5275d-111">Ciąg reprezentujący liczbę.</span><span class="sxs-lookup"><span data-stu-id="5275d-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="5275d-112">CStr i Data</span><span class="sxs-lookup"><span data-stu-id="5275d-112">CStr and Date</span></span>  
 <span data-ttu-id="5275d-113">`Date`Typ zawsze zawiera informacje o dacie i godzinie.</span><span class="sxs-lookup"><span data-stu-id="5275d-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="5275d-114">Na potrzeby konwersji typów Visual Basic uznaje, że 1/1/0001 (1 stycznia roku 1) jest *wartością neutralną* dla daty oraz 00:00:00 (północy) jako wartość neutralną czasu.</span><span class="sxs-lookup"><span data-stu-id="5275d-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="5275d-115">`CStr`nie uwzględnia neutralnych wartości w ciągu będącym wynikiem.</span><span class="sxs-lookup"><span data-stu-id="5275d-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="5275d-116">Na przykład w przypadku konwersji `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 am"; informacje o dacie są pomijane.</span><span class="sxs-lookup"><span data-stu-id="5275d-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="5275d-117">Jednak informacje o dacie są nadal obecne w pierwotnej `Date` wartości i mogą być odzyskiwane za pomocą funkcji, takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .</span><span class="sxs-lookup"><span data-stu-id="5275d-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5275d-118">`CStr`Funkcja wykonuje konwersję w oparciu o bieżące ustawienia kultury dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5275d-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="5275d-119">Aby uzyskać ciąg reprezentujący liczbę w określonej kulturze, użyj `ToString(IFormatProvider)` metody Number.</span><span class="sxs-lookup"><span data-stu-id="5275d-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="5275d-120">Na przykład, użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na `String` .</span><span class="sxs-lookup"><span data-stu-id="5275d-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5275d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5275d-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="5275d-122">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="5275d-122">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="5275d-123">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="5275d-123">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="5275d-124">Date, typ danych</span><span class="sxs-lookup"><span data-stu-id="5275d-124">Date Data Type</span></span>](../data-types/date-data-type.md)
