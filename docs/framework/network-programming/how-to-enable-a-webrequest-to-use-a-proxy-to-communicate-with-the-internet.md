---
title: 'Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest'
description: Dowiedz się, jak utworzyć globalne wystąpienie serwera proxy, aby umożliwić każdemu elementowi WebRequest korzystanie z serwera proxy w celu komunikowania się z Internetem w .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 0fc33cea3f5a7fe4669b110e53e71afdb9561c23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502538"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="75bbd-103">Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest</span><span class="sxs-lookup"><span data-stu-id="75bbd-103">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="75bbd-104">Ten przykład tworzy globalne wystąpienie serwera proxy, które umożliwi <xref:System.Net.WebRequest> Korzystanie z serwera proxy do komunikowania się z Internetem.</span><span class="sxs-lookup"><span data-stu-id="75bbd-104">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="75bbd-105">W przykładzie przyjęto założenie, że serwer proxy ma nazwę `webproxy` i komunikuje się z portem 80, standardowy port HTTP.</span><span class="sxs-lookup"><span data-stu-id="75bbd-105">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="75bbd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="75bbd-106">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="75bbd-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="75bbd-107">Compiling the Code</span></span>

<span data-ttu-id="75bbd-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="75bbd-108">This example requires:</span></span>

- <span data-ttu-id="75bbd-109">[ `using` Dyrektywa](../../csharp/language-reference/keywords/using-directive.md) języka C# dla przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="75bbd-109">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="75bbd-110">[ `Imports` Instrukcja](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic dla przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="75bbd-110">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="75bbd-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75bbd-111">See also</span></span>

- [<span data-ttu-id="75bbd-112">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="75bbd-112">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="75bbd-113">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="75bbd-113">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
