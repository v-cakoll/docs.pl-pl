---
title: Programowanie protokołów podłączanych
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 74dd44e704836b209366a7975d08a43375318e90
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190791"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="4eef5-102">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="4eef5-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="4eef5-103">Abstrakcyjna <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy zapewniają base podłączanych protokołów.</span><span class="sxs-lookup"><span data-stu-id="4eef5-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="4eef5-104">Przez wyprowadzanie klasy związane z Protokołem z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, aplikacja może dane żądania z zasobem internetowym i uzyskać odpowiedzi bez protokołu używanego do określania.</span><span class="sxs-lookup"><span data-stu-id="4eef5-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="4eef5-105">Aby można było utworzyć związane z protokołem <xref:System.Net.WebRequest>, należy zarejestrować jego metody Create.</span><span class="sxs-lookup"><span data-stu-id="4eef5-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="4eef5-106">Używa się statycznej <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> metody <xref:System.Net.WebRequest> zarejestrować <xref:System.Net.WebRequest> zależne do obsługi zestawu żądań do określonego schematu Internet, schemat i serwer lub do schematu, serwera i ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4eef5-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="4eef5-107">W większości przypadków będzie wysyłać i odbierać dane przy użyciu metod i właściwości <xref:System.Net.WebRequest> klasy.</span><span class="sxs-lookup"><span data-stu-id="4eef5-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="4eef5-108">Jednak jeśli potrzebujesz dostępu do właściwości specyficznych dla protokołu, użytkownik może rzutowanie typu <xref:System.Net.WebRequest> do określonego wystąpienia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="4eef5-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="4eef5-109">Aby móc korzystać z protokołów podłączanych swoje <xref:System.Net.WebRequest> elementy podrzędne należy podać transakcji żądań i odpowiedzi domyślnej, która nie wymaga ustawiania właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="4eef5-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="4eef5-110">Na przykład <xref:System.Net.HttpWebRequest> klasy, która implementuje <xref:System.Net.WebRequest> klasy do obsługi protokołu HTTP, zapewnia `GET` żądanie domyślnie i zwraca <xref:System.Net.HttpWebResponse> zawierający Strumień zwrócony z serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4eef5-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eef5-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4eef5-111">See Also</span></span>  
 [<span data-ttu-id="4eef5-112">Wyprowadzanie z elementu WebRequest</span><span class="sxs-lookup"><span data-stu-id="4eef5-112">Deriving from WebRequest</span></span>](../../../docs/framework/network-programming/deriving-from-webrequest.md)  
 [<span data-ttu-id="4eef5-113">Wyprowadzanie z elementu WebResponse</span><span class="sxs-lookup"><span data-stu-id="4eef5-113">Deriving from WebResponse</span></span>](../../../docs/framework/network-programming/deriving-from-webresponse.md)  
 [<span data-ttu-id="4eef5-114">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4eef5-114">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="4eef5-115">Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu</span><span class="sxs-lookup"><span data-stu-id="4eef5-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
