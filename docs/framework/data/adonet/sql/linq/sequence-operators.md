---
title: Operatory sekwencji
ms.date: 03/30/2017
ms.assetid: 4d332d32-3806-4451-b7af-25af269194ae
ms.openlocfilehash: 4feca030d3c398f4286fe9d126cae884afe7945b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792685"
---
# <a name="sequence-operators"></a><span data-ttu-id="68ca1-102">Operatory sekwencji</span><span class="sxs-lookup"><span data-stu-id="68ca1-102">Sequence Operators</span></span>
<span data-ttu-id="68ca1-103">Ogólnie mówiąc, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] program nie obsługuje operatorów sekwencji, które mają co najmniej jedną z następujących jakości:</span><span class="sxs-lookup"><span data-stu-id="68ca1-103">Generally speaking, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not support sequence operators that have one or more of the following qualities:</span></span>  
  
- <span data-ttu-id="68ca1-104">Wykonaj wyrażenie lambda z parametrem index.</span><span class="sxs-lookup"><span data-stu-id="68ca1-104">Take a lambda with an index parameter.</span></span>  
  
- <span data-ttu-id="68ca1-105">Polegaj na właściwościach sekwencyjnych wierszy, takich <xref:System.Linq.Queryable.TakeWhile%2A>jak.</span><span class="sxs-lookup"><span data-stu-id="68ca1-105">Rely on the properties of sequential rows, such as <xref:System.Linq.Queryable.TakeWhile%2A>.</span></span>  
  
- <span data-ttu-id="68ca1-106">Polegaj na dowolnej implementacji środowiska CLR, takiej <xref:System.Collections.Generic.IComparer%601>jak.</span><span class="sxs-lookup"><span data-stu-id="68ca1-106">Rely on an arbitrary CLR implementation, such as <xref:System.Collections.Generic.IComparer%601>.</span></span>  
  
|<span data-ttu-id="68ca1-107">Przykłady nieobsługiwanych</span><span class="sxs-lookup"><span data-stu-id="68ca1-107">Examples of Unsupported</span></span>|  
|-----------------------------|  
|<xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.TakeWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.TakeWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SkipWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SkipWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.GroupBy%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.GroupBy%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2CSystem.Collections.Generic.IEnumerable%7B%60%602%7D%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Reverse%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%600%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.ElementAt%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Range%28System.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Repeat%60%601%28%60%600%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Contains%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%600%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%600%2C%60%600%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%601%2CSystem.Func%7B%60%601%2C%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%601%2CSystem.Func%7B%60%601%2C%60%600%2C%60%601%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SequenceEqual%2A?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="68ca1-108">Różnice od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="68ca1-108">Differences from .NET</span></span>  
 <span data-ttu-id="68ca1-109">Wszystkie obsługiwane operatory sekwencji działają zgodnie z oczekiwaniami w środowisku uruchomieniowym języka wspólnego (CLR) `Average`, z wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="68ca1-109">All supported sequence operators work as expected in the common language runtime (CLR) except for `Average`.</span></span> <span data-ttu-id="68ca1-110">`Average`Zwraca wartość tego samego typu co średnia, a w środowisku CLR `Average` zawsze zwraca <xref:System.Double> albo lub <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="68ca1-110">`Average` returns a value of the same type as the type being averaged, whereas in the CLR `Average` always returns either a <xref:System.Double> or a <xref:System.Decimal>.</span></span> <span data-ttu-id="68ca1-111">Jeśli argument źródłowy jest jawnie rzutowany na wartość typu Double/Decimal lub przerzutowanie selektora na wartość podwójną/dziesiętną, wynikowa SQL również będzie miała taką konwersję, a wynik będzie zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="68ca1-111">If the source argument is explicitly cast to double / decimal or the selector casts to double / decimal, the resulting SQL will also have such a conversion and the result will be as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ca1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68ca1-112">See also</span></span>

- [<span data-ttu-id="68ca1-113">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="68ca1-113">Data Types and Functions</span></span>](data-types-and-functions.md)
