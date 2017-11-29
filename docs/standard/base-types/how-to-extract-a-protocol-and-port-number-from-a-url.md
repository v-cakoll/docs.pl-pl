---
title: "Porady: wyodrębnianie protokółu i numeru portu z adresu URL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10ab05ac8b24c0658be2f27809137c6b0bd4834f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="ef2e1-102">Porady: wyodrębnianie protokółu i numeru portu z adresu URL</span><span class="sxs-lookup"><span data-stu-id="ef2e1-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="ef2e1-103">Poniższy przykład wyodrębnia protokołem i numerem portu z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef2e1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef2e1-104">Example</span></span>  
 <span data-ttu-id="ef2e1-105">W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę, aby zwrócić protokołu wprowadź dwukropek i numer portu.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="ef2e1-106">Wzorzec wyrażenia regularnego `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` może zostać zinterpretowany, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="ef2e1-107">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="ef2e1-107">Pattern</span></span>|<span data-ttu-id="ef2e1-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ef2e1-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="ef2e1-109">Rozpocznij dopasowania na początku ciąg.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="ef2e1-110">Dopasowuje co najmniej jeden znak słowa.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-110">Match one or more word characters.</span></span> <span data-ttu-id="ef2e1-111">Określ nazwę tej grupy `proto`.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="ef2e1-112">Zgodne dwukropkiem następuje dwóch ukośnikami.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="ef2e1-113">Odpowiada jedno lub więcej wystąpień (ale jak najmniejszej liczby możliwie) dowolny znak inny niż znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="ef2e1-114">Zgodne wystąpienie zero lub jeden dwukropek następuje co najmniej jeden znak cyfr.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="ef2e1-115">Określ nazwę tej grupy `port`.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="ef2e1-116">Zgodne znaku ukośnika.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="ef2e1-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Rozszerza metodę `${proto}${port}` sekwencji zastępczy łączy wartość dwie grupy o nazwie przechwytywane wzorzec wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="ef2e1-118">Jest wygodnym sposobem jawnie łączenie ciągów, pobierana z obiektu kolekcji zwrócony przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="ef2e1-119">W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody za pomocą dwóch podstawienia `${proto}` i `${port}`, aby uwzględnić przechwyconej grupy w ciągu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="ef2e1-120">Przechwycony grup można pobrać z dopasowania <xref:System.Text.RegularExpressions.GroupCollection> obiekt zamiast tego, jak przedstawiono na poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="ef2e1-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ef2e1-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef2e1-121">See Also</span></span>  
 [<span data-ttu-id="ef2e1-122">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="ef2e1-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
