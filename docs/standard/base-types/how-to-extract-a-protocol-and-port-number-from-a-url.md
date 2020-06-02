---
title: 'Instrukcje: Wyodrębnianie protokołu i numeru portu z adresu URL'
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
ms.openlocfilehash: 48f2bf5c0d9af0a3fc286561ba978f86d1f11ac8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290490"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="567ad-102">Instrukcje: Wyodrębnianie protokołu i numeru portu z adresu URL</span><span class="sxs-lookup"><span data-stu-id="567ad-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="567ad-103">Poniższy przykład wyodrębnia protokołu i numeru portu z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="567ad-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="567ad-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="567ad-104">Example</span></span>  
 <span data-ttu-id="567ad-105">W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody do zwrócenia protokołu, po którym następuje dwukropek i numer portu.</span><span class="sxs-lookup"><span data-stu-id="567ad-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="567ad-106">Wzorzec wyrażenia regularnego `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` może być interpretowany jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="567ad-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="567ad-107">Wzorce</span><span class="sxs-lookup"><span data-stu-id="567ad-107">Pattern</span></span>|<span data-ttu-id="567ad-108">Opis</span><span class="sxs-lookup"><span data-stu-id="567ad-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="567ad-109">Rozpocznij dopasowanie na początku ciągu.</span><span class="sxs-lookup"><span data-stu-id="567ad-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="567ad-110">Dopasowuje co najmniej jeden znak słowa.</span><span class="sxs-lookup"><span data-stu-id="567ad-110">Match one or more word characters.</span></span> <span data-ttu-id="567ad-111">Nadaj nazwę tej grupie `proto` .</span><span class="sxs-lookup"><span data-stu-id="567ad-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="567ad-112">Dopasowuje dwukropek, po którym następuje dwa znaki ukośnika.</span><span class="sxs-lookup"><span data-stu-id="567ad-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="567ad-113">Dopasowuje jedno lub więcej wystąpień (ale jak najszybciej) dowolnego znaku, który jest inny niż znak kreski ułamkowej.</span><span class="sxs-lookup"><span data-stu-id="567ad-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="567ad-114">Dopasowanie do zera lub jednego wystąpienia dwukropka, po którym następuje jeden lub więcej znaków cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="567ad-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="567ad-115">Nadaj nazwę tej grupie `port` .</span><span class="sxs-lookup"><span data-stu-id="567ad-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="567ad-116">Dopasowuje znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="567ad-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="567ad-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Metoda rozszerza `${proto}${port}` sekwencję zamiany, która łączy wartość dwóch nazwanych grup przechwytywanych we wzorcu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="567ad-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="567ad-118">Jest to wygodna alternatywa do jawnego łączenia ciągów pobranych z obiektu kolekcji zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="567ad-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="567ad-119">W przykładzie zastosowano <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę z dwoma podstawiami, `${proto}` a w `${port}` celu uwzględnienia przechwyconych grup w ciągu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="567ad-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="567ad-120">Przechwycone grupy można pobrać z <xref:System.Text.RegularExpressions.GroupCollection> obiektu dopasowania zamiast tego, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="567ad-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="567ad-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="567ad-121">See also</span></span>

- [<span data-ttu-id="567ad-122">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="567ad-122">.NET Regular Expressions</span></span>](regular-expressions.md)
