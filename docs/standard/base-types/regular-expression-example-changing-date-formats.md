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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084181"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="86113-102">Przykładowe wyrażenie regularne: zmienianie formatów daty</span><span class="sxs-lookup"><span data-stu-id="86113-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="86113-103">Poniższy przykład kodu używa metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>, aby zastąpić daty, które mają postać *mm*/*DD*/*yy* z datami, które mają postać *DD*-*mm*-*RR*.</span><span class="sxs-lookup"><span data-stu-id="86113-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86113-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="86113-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="86113-105">Poniższy kod pokazuje, jak Metoda `MDYToDMY` może być wywoływana w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86113-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="86113-106">Komentarze</span><span class="sxs-lookup"><span data-stu-id="86113-106">Comments</span></span>  
 <span data-ttu-id="86113-107">`\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="86113-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="86113-108">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="86113-108">Pattern</span></span>|<span data-ttu-id="86113-109">Opis</span><span class="sxs-lookup"><span data-stu-id="86113-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="86113-110">Rozpoczyna dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="86113-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="86113-111">Dopasowuje jedną lub dwie cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="86113-111">Match one or two decimal digits.</span></span> <span data-ttu-id="86113-112">To jest Grupa przechwycona `month`.</span><span class="sxs-lookup"><span data-stu-id="86113-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="86113-113">Dopasowuje znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="86113-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="86113-114">Dopasowuje jedną lub dwie cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="86113-114">Match one or two decimal digits.</span></span> <span data-ttu-id="86113-115">To jest Grupa przechwycona `day`.</span><span class="sxs-lookup"><span data-stu-id="86113-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="86113-116">Dopasowuje znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="86113-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="86113-117">Dopasowuje od dwóch do czterech cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="86113-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="86113-118">To jest Grupa przechwycona `year`.</span><span class="sxs-lookup"><span data-stu-id="86113-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="86113-119">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="86113-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="86113-120">Wzorzec `${day}-${month}-${year}` definiuje ciąg zamienny, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="86113-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="86113-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="86113-121">Pattern</span></span>|<span data-ttu-id="86113-122">Opis</span><span class="sxs-lookup"><span data-stu-id="86113-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="86113-123">Dodaj ciąg przechwytywany przez grupę przechwytywania `day`.</span><span class="sxs-lookup"><span data-stu-id="86113-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="86113-124">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="86113-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="86113-125">Dodaj ciąg przechwytywany przez grupę przechwytywania `month`.</span><span class="sxs-lookup"><span data-stu-id="86113-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="86113-126">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="86113-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="86113-127">Dodaj ciąg przechwytywany przez grupę przechwytywania `year`.</span><span class="sxs-lookup"><span data-stu-id="86113-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86113-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86113-128">See also</span></span>

- [<span data-ttu-id="86113-129">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="86113-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
