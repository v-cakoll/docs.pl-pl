---
title: 'Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039536"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="768f0-102">Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest</span><span class="sxs-lookup"><span data-stu-id="768f0-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="768f0-103">W tym przykładzie tworzy wystąpienie <xref:System.Net.WebRequest> globalnego serwera proxy, które umożliwi każdemu używanie serwera proxy do komunikowania się z Internetem.</span><span class="sxs-lookup"><span data-stu-id="768f0-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="768f0-104">W przykładzie przyjęto założenie, `webproxy` że serwer proxy ma nazwę i że komunikuje się na porcie 80, standardowym porcie HTTP.</span><span class="sxs-lookup"><span data-stu-id="768f0-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="768f0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="768f0-105">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="768f0-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="768f0-106">Compiling the Code</span></span>

<span data-ttu-id="768f0-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="768f0-107">This example requires:</span></span>

- <span data-ttu-id="768f0-108">[ `using` Dyrektywa](../../csharp/language-reference/keywords/using-directive.md) C# dla **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="768f0-108">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="768f0-109">Instrukcja Języka Visual [ `Imports` Basic](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla **System.Net** obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="768f0-109">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="768f0-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="768f0-110">See also</span></span>

- [<span data-ttu-id="768f0-111">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="768f0-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="768f0-112">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="768f0-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
