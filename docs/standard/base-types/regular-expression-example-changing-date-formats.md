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
ms.openlocfilehash: 4290bf0d6ee9deec8129c5f4f6092eedb08345f0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276182"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="950c1-102">Przykładowe wyrażenie regularne: zmienianie formatów daty</span><span class="sxs-lookup"><span data-stu-id="950c1-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="950c1-103">Poniższy przykład kodu używa <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody, aby zastąpić daty, które mają postać *mm* / *DD* / *yy* z datami, które mają postać *DD* - *mm* - *RR*.</span><span class="sxs-lookup"><span data-stu-id="950c1-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="950c1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="950c1-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="950c1-105">Poniższy kod pokazuje, jak `MDYToDMY` Metoda może być wywoływana w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="950c1-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="950c1-106">Komentarze</span><span class="sxs-lookup"><span data-stu-id="950c1-106">Comments</span></span>  
 <span data-ttu-id="950c1-107">Wzorzec wyrażenia regularnego `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` jest interpretowany jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="950c1-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="950c1-108">Wzorce</span><span class="sxs-lookup"><span data-stu-id="950c1-108">Pattern</span></span>|<span data-ttu-id="950c1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="950c1-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="950c1-110">Rozpoczyna dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="950c1-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="950c1-111">Dopasowuje jedną lub dwie cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="950c1-111">Match one or two decimal digits.</span></span> <span data-ttu-id="950c1-112">To jest `month` Grupa przechwycona.</span><span class="sxs-lookup"><span data-stu-id="950c1-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="950c1-113">Dopasowuje znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="950c1-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="950c1-114">Dopasowuje jedną lub dwie cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="950c1-114">Match one or two decimal digits.</span></span> <span data-ttu-id="950c1-115">To jest `day` Grupa przechwycona.</span><span class="sxs-lookup"><span data-stu-id="950c1-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="950c1-116">Dopasowuje znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="950c1-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="950c1-117">Dopasowuje od dwóch do czterech cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="950c1-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="950c1-118">To jest `year` Grupa przechwycona.</span><span class="sxs-lookup"><span data-stu-id="950c1-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="950c1-119">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="950c1-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="950c1-120">Wzorzec `${day}-${month}-${year}` definiuje ciąg zamienny, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="950c1-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="950c1-121">Wzorce</span><span class="sxs-lookup"><span data-stu-id="950c1-121">Pattern</span></span>|<span data-ttu-id="950c1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="950c1-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="950c1-123">Dodaj ciąg przechwytywany przez `day` grupę przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="950c1-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="950c1-124">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="950c1-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="950c1-125">Dodaj ciąg przechwytywany przez `month` grupę przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="950c1-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="950c1-126">Dodaj łącznik.</span><span class="sxs-lookup"><span data-stu-id="950c1-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="950c1-127">Dodaj ciąg przechwytywany przez `year` grupę przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="950c1-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="950c1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="950c1-128">See also</span></span>

- [<span data-ttu-id="950c1-129">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="950c1-129">.NET Regular Expressions</span></span>](regular-expressions.md)
