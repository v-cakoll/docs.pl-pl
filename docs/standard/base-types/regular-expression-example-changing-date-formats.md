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
ms.openlocfilehash: 358e26957747073fec9dfe9eb0d404cb438afaf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084181"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="2c92a-102">Przykładowe wyrażenie regularne: zmienianie formatów daty</span><span class="sxs-lookup"><span data-stu-id="2c92a-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="2c92a-103">Poniższy przykład kodu <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> używa metody do zastąpienia dat, które mają formularz *mm*/*dd*/*yy* z datami, które mają formularz *dd*-*mm*-*yy*.</span><span class="sxs-lookup"><span data-stu-id="2c92a-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c92a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c92a-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="2c92a-105">Poniższy kod pokazuje, `MDYToDMY` jak można wywołać metodę w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c92a-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="2c92a-106">Komentarze</span><span class="sxs-lookup"><span data-stu-id="2c92a-106">Comments</span></span>  
 <span data-ttu-id="2c92a-107">Wzorzec `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2c92a-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="2c92a-108">Wzorce</span><span class="sxs-lookup"><span data-stu-id="2c92a-108">Pattern</span></span>|<span data-ttu-id="2c92a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2c92a-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="2c92a-110">Rozpoczyna dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="2c92a-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="2c92a-111">Dopasuj jedną lub dwie cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="2c92a-111">Match one or two decimal digits.</span></span> <span data-ttu-id="2c92a-112">Jest to `month` przechwycona grupa.</span><span class="sxs-lookup"><span data-stu-id="2c92a-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="2c92a-113">Dopasuj znacznik ukośnika.</span><span class="sxs-lookup"><span data-stu-id="2c92a-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="2c92a-114">Dopasuj jedną lub dwie cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="2c92a-114">Match one or two decimal digits.</span></span> <span data-ttu-id="2c92a-115">Jest to `day` przechwycona grupa.</span><span class="sxs-lookup"><span data-stu-id="2c92a-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="2c92a-116">Dopasuj znacznik ukośnika.</span><span class="sxs-lookup"><span data-stu-id="2c92a-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="2c92a-117">Dopasuj od dwóch do czterech cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="2c92a-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="2c92a-118">Jest to `year` przechwycona grupa.</span><span class="sxs-lookup"><span data-stu-id="2c92a-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="2c92a-119">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="2c92a-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="2c92a-120">Deseń `${day}-${month}-${year}` definiuje ciąg zastępczy, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2c92a-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="2c92a-121">Wzorce</span><span class="sxs-lookup"><span data-stu-id="2c92a-121">Pattern</span></span>|<span data-ttu-id="2c92a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2c92a-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="2c92a-123">Dodaj ciąg przechwycony `day` przez grupę przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="2c92a-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="2c92a-124">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="2c92a-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="2c92a-125">Dodaj ciąg przechwycony `month` przez grupę przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="2c92a-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="2c92a-126">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="2c92a-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="2c92a-127">Dodaj ciąg przechwycony `year` przez grupę przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="2c92a-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c92a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c92a-128">See also</span></span>

- [<span data-ttu-id="2c92a-129">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="2c92a-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
