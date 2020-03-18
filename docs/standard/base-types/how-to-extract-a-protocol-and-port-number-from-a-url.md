---
title: 'Porady: wyodrębnianie protokółu i numeru portu z adresu URL'
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
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
ms.openlocfilehash: f2704e3fb5ceb68609a475d52e11030177ad760b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138721"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="e619a-102">Porady: wyodrębnianie protokółu i numeru portu z adresu URL</span><span class="sxs-lookup"><span data-stu-id="e619a-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="e619a-103">Poniższy przykład wyodrębnia protokół i numer portu z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="e619a-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e619a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e619a-104">Example</span></span>  
 <span data-ttu-id="e619a-105">W przykładzie <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> użyto metody do zwrócenia protokołu, po którym następuje dwukropek, po którym następuje numer portu.</span><span class="sxs-lookup"><span data-stu-id="e619a-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="e619a-106">Wzorzec `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` wyrażenia regularnego można interpretować w sposób pokazany w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e619a-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="e619a-107">Wzorce</span><span class="sxs-lookup"><span data-stu-id="e619a-107">Pattern</span></span>|<span data-ttu-id="e619a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e619a-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="e619a-109">Rozpocznij dopasowanie na początku ciągu.</span><span class="sxs-lookup"><span data-stu-id="e619a-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="e619a-110">Dopasowuje co najmniej jeden znak słowa.</span><span class="sxs-lookup"><span data-stu-id="e619a-110">Match one or more word characters.</span></span> <span data-ttu-id="e619a-111">Nazwij `proto`tę grupę .</span><span class="sxs-lookup"><span data-stu-id="e619a-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="e619a-112">Dopasuj dwukropek, po którym następują dwa znaki ukośnika.</span><span class="sxs-lookup"><span data-stu-id="e619a-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="e619a-113">Dopasuj jedno lub więcej wystąpień (ale jak najmniej) dowolnego znaku innego niż znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="e619a-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="e619a-114">Dopasuj zero lub jedno wystąpienie dwukropka, po którym następuje jeden lub więcej znaków cyfr.</span><span class="sxs-lookup"><span data-stu-id="e619a-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="e619a-115">Nazwij `port`tę grupę .</span><span class="sxs-lookup"><span data-stu-id="e619a-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="e619a-116">Dopasuj znacznik ukośnika.</span><span class="sxs-lookup"><span data-stu-id="e619a-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="e619a-117">Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> rozwija sekwencję `${proto}${port}` wymiany, która łączy wartość dwóch nazwanych grup przechwyconych we wzorcu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="e619a-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="e619a-118">Jest wygodną alternatywą jawnie łączenie ciągów pobranych z obiektu kolekcji zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="e619a-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e619a-119">W przykładzie <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> użyto metody z dwoma podstawieniami `${proto}` i `${port}`, aby uwzględnić przechwycone grupy w ciągu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e619a-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="e619a-120">Przechwycone grupy można <xref:System.Text.RegularExpressions.GroupCollection> pobrać z obiektu dopasowania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e619a-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e619a-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e619a-121">See also</span></span>

- [<span data-ttu-id="e619a-122">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="e619a-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
