---
title: 'Instrukcje: Włączanie żądania sieci webdo komunikacji z Internetem za pomocą serwera proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039536"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="00af7-102">Instrukcje: Włączanie żądania sieci webdo komunikacji z Internetem za pomocą serwera proxy</span><span class="sxs-lookup"><span data-stu-id="00af7-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="00af7-103">W tym przykładzie jest tworzone globalne wystąpienie serwera proxy, które umożliwi <xref:System.Net.WebRequest> do komunikacji z Internetem przy użyciu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="00af7-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="00af7-104">W przykładzie przyjęto założenie, że serwer proxy ma nazwę `webproxy` i że komunikuje się z portem 80, standardowym portem HTTP.</span><span class="sxs-lookup"><span data-stu-id="00af7-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="00af7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="00af7-105">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="00af7-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="00af7-106">Compiling the Code</span></span>

<span data-ttu-id="00af7-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="00af7-107">This example requires:</span></span>

- <span data-ttu-id="00af7-108">C# [Dyrektywa`using`](../../csharp/language-reference/keywords/using-directive.md) dla przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="00af7-108">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="00af7-109">Visual Basic [`Imports` instrukcji](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="00af7-109">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="00af7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00af7-110">See also</span></span>

- [<span data-ttu-id="00af7-111">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="00af7-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="00af7-112">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="00af7-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
