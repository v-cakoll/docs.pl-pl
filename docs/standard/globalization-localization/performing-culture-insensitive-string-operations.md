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
ms.openlocfilehash: 79ff899e2964ae2c1e90b7178616c612dddf6d86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287509"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="26ea5-102">Wykonywanie operacji na ciągach niewrażliwych na kulturę</span><span class="sxs-lookup"><span data-stu-id="26ea5-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="26ea5-103">Większość .NET Framework metod, które wykonują operacje na ciągach zależnych od kultury, domyślnie udostępnia przeciążenia metod, które umożliwiają jawne określenie kultury do użycia przez przekazanie <xref:System.Globalization.CultureInfo> parametru.</span><span class="sxs-lookup"><span data-stu-id="26ea5-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="26ea5-104">Te przeciążenia pozwalają wyeliminować wahania kulturowe w odniesieniu do mapowań i reguł sortowania, a następnie zagwarantować wyniki niewrażliwe na kulturę.</span><span class="sxs-lookup"><span data-stu-id="26ea5-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="26ea5-105">Ta sekcja zawiera następujące tematy przedstawiające sposób wykonywania operacji na ciągach niewrażliwych na kulturę przy użyciu metod .NET Framework, które domyślnie są zależne od kultury.</span><span class="sxs-lookup"><span data-stu-id="26ea5-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26ea5-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="26ea5-106">In this section</span></span>  
 [<span data-ttu-id="26ea5-107">Wykonywanie niezależnych od kultury porównań ciągów</span><span class="sxs-lookup"><span data-stu-id="26ea5-107">Performing Culture-Insensitive String Comparisons</span></span>](performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="26ea5-108">Opisuje sposób użycia <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metod i do wykonywania porównania ciągów niewrażliwych na kulturę.</span><span class="sxs-lookup"><span data-stu-id="26ea5-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="26ea5-109">Wykonywanie niezależnych od kultury zmian wielkości liter</span><span class="sxs-lookup"><span data-stu-id="26ea5-109">Performing Culture-Insensitive Case Changes</span></span>](performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="26ea5-110">Opisuje sposób używania <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType> metod,, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> do wykonywania zmian wielkości liter bez uwzględniania kultur.</span><span class="sxs-lookup"><span data-stu-id="26ea5-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="26ea5-111">Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="26ea5-111">Performing Culture-Insensitive String Operations in Collections</span></span>](performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="26ea5-112">Opisuje sposób używania <xref:System.Collections.CaseInsensitiveComparer> , klasy, <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.SortedList> <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> i <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> do wykonywania operacji niewrażliwych na kulturę w kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="26ea5-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="26ea5-113">Wykonywanie niezależnych od kultury operacji na ciągach w tablicach</span><span class="sxs-lookup"><span data-stu-id="26ea5-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="26ea5-114">Opisuje sposób użycia <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metod i do wykonywania operacji niewrażliwych na kulturę w tablicach.</span><span class="sxs-lookup"><span data-stu-id="26ea5-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="26ea5-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="26ea5-115">Related sections</span></span>  
 [<span data-ttu-id="26ea5-116">Operacje na ciągach nieuwzględniających kultur</span><span class="sxs-lookup"><span data-stu-id="26ea5-116">Culture-Insensitive String Operations</span></span>](culture-insensitive-string-operations.md)  
 <span data-ttu-id="26ea5-117">W tym artykule opisano, dlaczego należy pamiętać o kulturze podczas wykonywania operacji na ciągach i przedstawiono wskazówki dotyczące sytuacji, w których należy wykonać operacje zależne od kultury i kiedy wykonywać operacje niewrażliwe na kulturę.</span><span class="sxs-lookup"><span data-stu-id="26ea5-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="26ea5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26ea5-118">See also</span></span>

- [<span data-ttu-id="26ea5-119">Sortowanie tabel wag (dla platformy .NET w systemach Windows)</span><span class="sxs-lookup"><span data-stu-id="26ea5-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="26ea5-120">Domyślna tabela elementów sortowania Unicode (dla platformy .NET Core w systemie Linux i macOS)</span><span class="sxs-lookup"><span data-stu-id="26ea5-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
