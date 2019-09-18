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
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047400"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="43e2a-102">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="43e2a-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="43e2a-103">Abstrakcyjne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy stanowią podstawę dla protokołów podłączanych.</span><span class="sxs-lookup"><span data-stu-id="43e2a-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="43e2a-104">Dzięki wykorzystaniu klas specyficznych dla <xref:System.Net.WebRequest> protokołu <xref:System.Net.WebResponse>z i, aplikacja może zażądać danych z zasobu internetowego i odczytać odpowiedź bez określania używanego protokołu.</span><span class="sxs-lookup"><span data-stu-id="43e2a-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="43e2a-105">Aby można było utworzyć specyficzny <xref:System.Net.WebRequest>dla protokołu, należy zarejestrować metodę Create.</span><span class="sxs-lookup"><span data-stu-id="43e2a-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="43e2a-106">Użyj <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> metody statycznej w celu zarejestrowania elementu podrzędnego w celu obsługi zestawu żądań do określonego schematu internetowego, schematu i serwera, lub schematu, serwera i ścieżki. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="43e2a-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="43e2a-107">W większości przypadków będzie można wysyłać i odbierać dane przy użyciu metod i właściwości <xref:System.Net.WebRequest> klasy.</span><span class="sxs-lookup"><span data-stu-id="43e2a-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="43e2a-108">Jeśli jednak chcesz uzyskać dostęp do właściwości specyficznych dla protokołu, możesz rzutowanie a <xref:System.Net.WebRequest> do określonego wystąpienia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="43e2a-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="43e2a-109">Aby móc korzystać z protokołów podłączanych, <xref:System.Net.WebRequest> elementy podrzędne muszą udostępniać domyślną transakcję żądanie-odpowiedź, która nie wymaga ustawiania właściwości specyficznych dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="43e2a-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="43e2a-110">Na przykład <xref:System.Net.HttpWebRequest> Klasa, która <xref:System.Net.WebRequest> implementuje klasę `GET` dla protokołu HTTP, domyślnie zapewnia żądanie i zwraca <xref:System.Net.HttpWebResponse> wartość zawierającą Strumień zwrócony z serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="43e2a-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e2a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43e2a-111">See also</span></span>

- [<span data-ttu-id="43e2a-112">Wyprowadzanie z elementu WebRequest</span><span class="sxs-lookup"><span data-stu-id="43e2a-112">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="43e2a-113">Wyprowadzanie z elementu WebResponse</span><span class="sxs-lookup"><span data-stu-id="43e2a-113">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="43e2a-114">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43e2a-114">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="43e2a-115">Instrukcje: Rzutowanie żądania sieci Webw celu uzyskania dostępu do właściwości specyficznych dla protokołu</span><span class="sxs-lookup"><span data-stu-id="43e2a-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
