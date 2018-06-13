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
ms.openlocfilehash: 8d2d5bf67368e445123fce43afe07065a31b1f30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568072"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="162fa-102">Przykładowe wyrażenie regularne: zmienianie formatów daty</span><span class="sxs-lookup"><span data-stu-id="162fa-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="162fa-103">Poniższy przykład kodu wykorzystuje <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę, aby zastąpić daty, które mają następującą postać *mm*/*dd*/*rr* z daty mieć postać *dd*-*mm*-*rr*.</span><span class="sxs-lookup"><span data-stu-id="162fa-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="162fa-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="162fa-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="162fa-105">Poniższy kod przedstawia sposób `MDYToDMY` metodę można wywołać w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="162fa-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="162fa-106">Komentarze</span><span class="sxs-lookup"><span data-stu-id="162fa-106">Comments</span></span>  
 <span data-ttu-id="162fa-107">Wzorzec wyrażenia regularnego `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` jest interpretowany, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="162fa-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="162fa-108">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="162fa-108">Pattern</span></span>|<span data-ttu-id="162fa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="162fa-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="162fa-110">Rozpoczyna dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="162fa-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="162fa-111">Odpowiada jednej lub dwóch miejsc dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="162fa-111">Match one or two decimal digits.</span></span> <span data-ttu-id="162fa-112">Jest to `month` przechwyconej grupy.</span><span class="sxs-lookup"><span data-stu-id="162fa-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="162fa-113">Zgodne ukośnik.</span><span class="sxs-lookup"><span data-stu-id="162fa-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="162fa-114">Odpowiada jednej lub dwóch miejsc dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="162fa-114">Match one or two decimal digits.</span></span> <span data-ttu-id="162fa-115">Jest to `day` przechwyconej grupy.</span><span class="sxs-lookup"><span data-stu-id="162fa-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="162fa-116">Zgodne ukośnik.</span><span class="sxs-lookup"><span data-stu-id="162fa-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="162fa-117">Zgodny z dwóch do czterech cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="162fa-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="162fa-118">Jest to `year` przechwyconej grupy.</span><span class="sxs-lookup"><span data-stu-id="162fa-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="162fa-119">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="162fa-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="162fa-120">Wzorzec `${day}-${month}-${year}` definiuje ciąg zastępczy, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="162fa-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="162fa-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="162fa-121">Pattern</span></span>|<span data-ttu-id="162fa-122">Opis</span><span class="sxs-lookup"><span data-stu-id="162fa-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="162fa-123">Dodaj ciąg przechwycone przez `day` Przechwytywanie grupy.</span><span class="sxs-lookup"><span data-stu-id="162fa-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="162fa-124">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="162fa-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="162fa-125">Dodaj ciąg przechwycone przez `month` Przechwytywanie grupy.</span><span class="sxs-lookup"><span data-stu-id="162fa-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="162fa-126">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="162fa-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="162fa-127">Dodaj ciąg przechwycone przez `year` Przechwytywanie grupy.</span><span class="sxs-lookup"><span data-stu-id="162fa-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="162fa-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="162fa-128">See Also</span></span>  
 [<span data-ttu-id="162fa-129">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="162fa-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
