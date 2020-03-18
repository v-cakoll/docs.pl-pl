---
title: Wykonywanie niezależnych od kultury operacji na ciągach
ms.date: 08/22/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: 183078b1f7a3eb3530fea8af06dbb59055d7d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120796"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="52921-102">Wykonywanie operacji ciągów niewrażliwych na kulturę</span><span class="sxs-lookup"><span data-stu-id="52921-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="52921-103">Większość metod platformy .NET Framework, które wykonują operacje ciągu zależne od kultury domyślnie zapewniają <xref:System.Globalization.CultureInfo> przeciążenia metody, które umożliwiają jawnie określić kultury do użycia przez przekazywanie parametru.</span><span class="sxs-lookup"><span data-stu-id="52921-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="52921-104">Te przeciążenia umożliwiają wyeliminowanie różnic kulturowych w mapowaniach przypadków i regułach sortowania oraz gwarantują wyniki niewrażliwe na kulturę.</span><span class="sxs-lookup"><span data-stu-id="52921-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="52921-105">W tej sekcji przedstawiono następujące tematy, aby zademonstrować, jak wykonywać operacje ciągów niewrażliwe na kulturę przy użyciu metod .NET Framework, które są domyślnie zależne od kultury.</span><span class="sxs-lookup"><span data-stu-id="52921-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52921-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="52921-106">In this section</span></span>  
 [<span data-ttu-id="52921-107">Wykonywanie niezależnych od kultury porównań ciągów</span><span class="sxs-lookup"><span data-stu-id="52921-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="52921-108">Opisuje sposób używania <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> i metody do wykonywania nieczułych na kulturę porównań ciągów.</span><span class="sxs-lookup"><span data-stu-id="52921-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="52921-109">Wykonywanie niezależnych od kultury zmian wielkości liter</span><span class="sxs-lookup"><span data-stu-id="52921-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="52921-110">Opisuje sposób używania <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, <xref:System.Char.ToLower%2A?displayProperty=nameWithType> i metody do wykonywania zmian wielkości liter niewrażliwe na kulturę.</span><span class="sxs-lookup"><span data-stu-id="52921-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="52921-111">Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="52921-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="52921-112">Opisuje sposób używania <xref:System.Collections.CaseInsensitiveComparer> <xref:System.Collections.CaseInsensitiveHashCodeProvider> , <xref:System.Collections.SortedList>klasy <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> , i do wykonywania operacji niewrażliwych na kulturę w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="52921-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="52921-113">Wykonywanie niezależnych od kultury operacji na ciągach w tablicach</span><span class="sxs-lookup"><span data-stu-id="52921-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="52921-114">Opisuje sposób używania <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> i metod do wykonywania operacji niewrażliwych na kulturę w tablicach.</span><span class="sxs-lookup"><span data-stu-id="52921-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52921-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="52921-115">Related sections</span></span>  
 [<span data-ttu-id="52921-116">Operacje ciągów niewrażliwe na kulturę</span><span class="sxs-lookup"><span data-stu-id="52921-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="52921-117">W tym artykule opisano, dlaczego należy pamiętać o kulturze podczas wykonywania operacji na ciągach i zawiera wskazówki dotyczące wykonywania operacji wrażliwych na kulturę i podczas wykonywania operacji niewrażliwych na kulturę.</span><span class="sxs-lookup"><span data-stu-id="52921-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="52921-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52921-118">See also</span></span>

- [<span data-ttu-id="52921-119">Sortowanie tabel wagowych (dla .NET w systemach Windows)</span><span class="sxs-lookup"><span data-stu-id="52921-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="52921-120">Domyślna tabela elementów sortowania Unicode (dla .NET Core w systemach Linux i macOS)</span><span class="sxs-lookup"><span data-stu-id="52921-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
