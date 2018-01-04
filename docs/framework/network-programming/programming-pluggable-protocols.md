---
title: "Protokoły podłączany programowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c97b64c9e042706fedabac435b8982aed65a8be4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="3634c-102">Protokoły podłączany programowania</span><span class="sxs-lookup"><span data-stu-id="3634c-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="3634c-103">Abstract <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy podanie podłączany protokołów podstawowym.</span><span class="sxs-lookup"><span data-stu-id="3634c-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="3634c-104">Przez wyprowadzanie klasy specyficzne dla protokołu z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, aplikacji można dane żądania z zasobu internetowego i bez określania protokołu używanego do odczytu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3634c-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="3634c-105">Przed utworzeniem oparte na protokole <xref:System.Net.WebRequest>, należy zarejestrować jego metody Create.</span><span class="sxs-lookup"><span data-stu-id="3634c-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="3634c-106">Użyj statycznych <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> metody <xref:System.Net.WebRequest> zarejestrować <xref:System.Net.WebRequest> elementów podrzędnych do obsługi żądań do określonego schematu Internet, schemat i serwer lub do schematu, serwera i ścieżki zestawu.</span><span class="sxs-lookup"><span data-stu-id="3634c-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="3634c-107">W większości przypadków będzie mógł wysyłać i odbierać dane przy użyciu metody i właściwości <xref:System.Net.WebRequest> klasy.</span><span class="sxs-lookup"><span data-stu-id="3634c-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="3634c-108">Jednak jeśli potrzebujesz dostępu do właściwości specyficzne dla protokołu, użytkownik może rzutowanie typu <xref:System.Net.WebRequest> określonego wystąpienia klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="3634c-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="3634c-109">Aby móc korzystać z protokołów podłączane z <xref:System.Net.WebRequest> descendants musi podać transakcji żądanie i odpowiedź domyślna, która nie wymaga właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="3634c-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="3634c-110">Na przykład <xref:System.Net.HttpWebRequest> klasy, która implementuje <xref:System.Net.WebRequest> klasy do obsługi protokołu HTTP, zapewnia `GET` żądanie domyślnie i zwraca <xref:System.Net.HttpWebResponse> zawierający strumienia zwrócone z serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3634c-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3634c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3634c-111">See Also</span></span>  
 [<span data-ttu-id="3634c-112">Wyprowadzanie z elementu WebRequest</span><span class="sxs-lookup"><span data-stu-id="3634c-112">Deriving from WebRequest</span></span>](../../../docs/framework/network-programming/deriving-from-webrequest.md)  
 [<span data-ttu-id="3634c-113">Wyprowadzanie z elementu WebResponse</span><span class="sxs-lookup"><span data-stu-id="3634c-113">Deriving from WebResponse</span></span>](../../../docs/framework/network-programming/deriving-from-webresponse.md)  
 [<span data-ttu-id="3634c-114">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3634c-114">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="3634c-115">Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu</span><span class="sxs-lookup"><span data-stu-id="3634c-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
