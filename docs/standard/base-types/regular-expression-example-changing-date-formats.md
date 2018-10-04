---
title: 'Przykładowe wyrażenie regularne: zmienianie formatów daty'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c26608115a22a5402d671c5f5e51c75442a0a5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48264398"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="3f3aa-102">Przykładowe wyrażenie regularne: zmienianie formatów daty</span><span class="sxs-lookup"><span data-stu-id="3f3aa-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="3f3aa-103">Poniższy przykład kodu wykorzystuje <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę, aby zastąpić dat, które mają następującą formę *mm*/*dd*/*rr* z daty mają następującą formę *dd*-*mm*-*rr*.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f3aa-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f3aa-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="3f3aa-105">Poniższy kod przedstawia sposób, w jaki `MDYToDMY` metodę można wywołać w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="3f3aa-106">Komentarze</span><span class="sxs-lookup"><span data-stu-id="3f3aa-106">Comments</span></span>  
 <span data-ttu-id="3f3aa-107">Definicję wzorca wyrażenia regularnego `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` jest interpretowane tak jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="3f3aa-108">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="3f3aa-108">Pattern</span></span>|<span data-ttu-id="3f3aa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3f3aa-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="3f3aa-110">Rozpoczyna dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="3f3aa-111">Dopasowuje co najmniej dwie cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-111">Match one or two decimal digits.</span></span> <span data-ttu-id="3f3aa-112">Jest to `month` przechwyconą grupę.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="3f3aa-113">Dopasowuje znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="3f3aa-114">Dopasowuje co najmniej dwie cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-114">Match one or two decimal digits.</span></span> <span data-ttu-id="3f3aa-115">Jest to `day` przechwyconą grupę.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="3f3aa-116">Dopasowuje znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="3f3aa-117">Dopasowuje od dwóch do czterech cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="3f3aa-118">Jest to `year` przechwyconą grupę.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="3f3aa-119">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="3f3aa-120">Wzorzec `${day}-${month}-${year}` definiuje ciąg zastępujący, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="3f3aa-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="3f3aa-121">Pattern</span></span>|<span data-ttu-id="3f3aa-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3f3aa-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="3f3aa-123">Dodaj parametry przechwycone przez `day` grupa przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="3f3aa-124">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="3f3aa-125">Dodaj parametry przechwycone przez `month` grupa przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="3f3aa-126">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="3f3aa-127">Dodaj parametry przechwycone przez `year` grupa przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3f3aa-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f3aa-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f3aa-128">See also</span></span>

- [<span data-ttu-id="3f3aa-129">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="3f3aa-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
