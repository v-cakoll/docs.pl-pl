---
title: Metody System.String
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 569010c36296e18487eb52527d3df0cc0b97cf06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618134"
---
# <a name="systemstring-methods"></a><span data-ttu-id="e0272-102">Metody System.String</span><span class="sxs-lookup"><span data-stu-id="e0272-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e0272-103">nie obsługuje następujących <xref:System.String> metody.</span><span class="sxs-lookup"><span data-stu-id="e0272-103">does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="e0272-104">Ogólnie rzecz biorąc nieobsługiwany metody System.String</span><span class="sxs-lookup"><span data-stu-id="e0272-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="e0272-105">Nieobsługiwana <xref:System.String> metody ogólne:</span><span class="sxs-lookup"><span data-stu-id="e0272-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
-   <span data-ttu-id="e0272-106">Przeciążenia kultury (metody, które przyjmują `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).</span><span class="sxs-lookup"><span data-stu-id="e0272-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
-   <span data-ttu-id="e0272-107">Metody, które dopiero po lub utworzyć `char` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e0272-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="e0272-108">Nieobsługiwany System.String statyczne metody</span><span class="sxs-lookup"><span data-stu-id="e0272-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="e0272-109">Nieobsługiwany System.String statyczne metody</span><span class="sxs-lookup"><span data-stu-id="e0272-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="e0272-110">Nieobsługiwana System.String metod niestatycznych</span><span class="sxs-lookup"><span data-stu-id="e0272-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="e0272-111">Nieobsługiwana System.String metod niestatycznych</span><span class="sxs-lookup"><span data-stu-id="e0272-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="e0272-112">Różnice z platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e0272-112">Differences from .NET</span></span>  
  
-   <span data-ttu-id="e0272-113">Zapytania nie uwzględniać sortowania programu SQL Server, które mogą obowiązywać na serwerze i będzie stanowić porównania wrażliwość na ustawienia kulturowe, bez uwzględniania wielkości liter domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e0272-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="e0272-114">To zachowanie różni się od domyślnej, semantyka liter programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0272-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="e0272-115">Gdy `LastIndexOf` jest zwraca wartość 0, ciągiem `NULL` lub znaleziono pozycji to 0.</span><span class="sxs-lookup"><span data-stu-id="e0272-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
-   <span data-ttu-id="e0272-116">Nieoczekiwane wyniki mogą być zwracane z łączenia lub inne operacje na ciągi o stałej długości (`CHAR`, `NCHAR`), ponieważ te typy mają automatycznie dopełnienie stosowane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e0272-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
-   <span data-ttu-id="e0272-117">Ponieważ wiele metod, takich jak `Replace`, `ToLower`, `ToUpper`i indeksatora znaków, ma nie prawidłowe tłumaczenia `TEXT` lub `NTEXT` kolumn i XML, `SqlExceptions` wystąpić, jeśli zwykle translacji.</span><span class="sxs-lookup"><span data-stu-id="e0272-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="e0272-118">To zachowanie jest uważany za akceptowalne dla tych typów.</span><span class="sxs-lookup"><span data-stu-id="e0272-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="e0272-119">Jednak wszystkie operacje na ciągach musi odpowiadać wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) semantyki dla `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, i `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="e0272-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0272-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0272-120">See also</span></span>
- [<span data-ttu-id="e0272-121">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="e0272-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
