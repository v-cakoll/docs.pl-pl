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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a08e97b02e2f60422132e97e2f3f7d4d2d5b8ec4
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479705"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="5ad86-102">Porady: wyodrębnianie protokółu i numeru portu z adresu URL</span><span class="sxs-lookup"><span data-stu-id="5ad86-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="5ad86-103">Poniższy przykład wyodrębnia protokół i numer portu z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="5ad86-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ad86-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ad86-104">Example</span></span>  
 <span data-ttu-id="5ad86-105">W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę, aby zwrócić protokołu następuje dwukropek i numer portu.</span><span class="sxs-lookup"><span data-stu-id="5ad86-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="5ad86-106">Definicję wzorca wyrażenia regularnego `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` mogą być interpretowane, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5ad86-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="5ad86-107">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="5ad86-107">Pattern</span></span>|<span data-ttu-id="5ad86-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5ad86-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="5ad86-109">Rozpoczyna dopasowanie na początku ciągu.</span><span class="sxs-lookup"><span data-stu-id="5ad86-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="5ad86-110">Dopasowuje co najmniej jeden znak słowa.</span><span class="sxs-lookup"><span data-stu-id="5ad86-110">Match one or more word characters.</span></span> <span data-ttu-id="5ad86-111">Określ nazwę tej grupy `proto`.</span><span class="sxs-lookup"><span data-stu-id="5ad86-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="5ad86-112">Dopasowuje dwukropek następuje dwóch znaków ukośnika.</span><span class="sxs-lookup"><span data-stu-id="5ad86-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="5ad86-113">Dopasowuje jedno lub więcej wystąpień (ale możliwie) dowolny znak inny niż znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="5ad86-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="5ad86-114">Dopasowuje zero lub jeden wystąpienie średnikami, na którym następuje co najmniej jeden znak cyfry.</span><span class="sxs-lookup"><span data-stu-id="5ad86-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="5ad86-115">Określ nazwę tej grupy `port`.</span><span class="sxs-lookup"><span data-stu-id="5ad86-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="5ad86-116">Dopasowuje znak ukośnika.</span><span class="sxs-lookup"><span data-stu-id="5ad86-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="5ad86-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Rozszerza metoda `${proto}${port}` sekwencji zastąpienie łączy wartości z dwóch grup o nazwie przechwycone we wzorcu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="5ad86-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="5ad86-118">Jest wygodne alternatywa jawnie łączenia ciągów pobierana z obiektu kolekcji zwrócony przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ad86-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="5ad86-119">W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody za pomocą dwóch podstawienia `${proto}` i `${port}`, aby uwzględnić przechwyconych grupach w ciągu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="5ad86-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="5ad86-120">Możesz pobrać przechwyconych grupach z dopasowania <xref:System.Text.RegularExpressions.GroupCollection> zamiast tego, co ilustruje poniższy kod obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ad86-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5ad86-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ad86-121">See also</span></span>

- [<span data-ttu-id="5ad86-122">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="5ad86-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
