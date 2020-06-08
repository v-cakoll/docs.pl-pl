---
title: Programowanie protokołów podłączanych
description: Dowiedz się, jak klasy abstrakcyjne i WebResponse są obsługiwane przez podłączane protokoły, które umożliwiają aplikacji pobieranie danych bez określania protokołu.
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
ms.openlocfilehash: 510f616295abc13d93e0e0af5a37aca097d343e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502200"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="43912-103">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="43912-103">Programming Pluggable Protocols</span></span>
<span data-ttu-id="43912-104">Abstrakcyjne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy stanowią podstawę dla protokołów podłączanych.</span><span class="sxs-lookup"><span data-stu-id="43912-104">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="43912-105">Dzięki wykorzystaniu klas specyficznych dla protokołu z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> , aplikacja może zażądać danych z zasobu internetowego i odczytać odpowiedź bez określania używanego protokołu.</span><span class="sxs-lookup"><span data-stu-id="43912-105">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="43912-106">Aby można było utworzyć specyficzny dla protokołu <xref:System.Net.WebRequest> , należy zarejestrować metodę Create.</span><span class="sxs-lookup"><span data-stu-id="43912-106">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="43912-107">Użyj metody statycznej <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> w celu zarejestrowania <xref:System.Net.WebRequest> elementu podrzędnego w celu obsługi zestawu żądań do określonego schematu internetowego, schematu i serwera, lub schematu, serwera i ścieżki.</span><span class="sxs-lookup"><span data-stu-id="43912-107">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="43912-108">W większości przypadków będzie można wysyłać i odbierać dane przy użyciu metod i właściwości <xref:System.Net.WebRequest> klasy.</span><span class="sxs-lookup"><span data-stu-id="43912-108">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="43912-109">Jeśli jednak chcesz uzyskać dostęp do właściwości specyficznych dla protokołu, możesz rzutowanie a <xref:System.Net.WebRequest> do określonego wystąpienia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="43912-109">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="43912-110">Aby móc korzystać z protokołów podłączanych, <xref:System.Net.WebRequest> elementy podrzędne muszą udostępniać domyślną transakcję żądanie-odpowiedź, która nie wymaga ustawiania właściwości specyficznych dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="43912-110">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="43912-111">Na przykład <xref:System.Net.HttpWebRequest> Klasa, która implementuje <xref:System.Net.WebRequest> klasę dla protokołu HTTP, `GET` Domyślnie zapewnia żądanie i zwraca wartość <xref:System.Net.HttpWebResponse> zawierającą Strumień zwrócony z serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="43912-111">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43912-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43912-112">See also</span></span>

- [<span data-ttu-id="43912-113">Wyprowadzanie z elementu WebRequest</span><span class="sxs-lookup"><span data-stu-id="43912-113">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="43912-114">Wyprowadzanie z elementu WebResponse</span><span class="sxs-lookup"><span data-stu-id="43912-114">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="43912-115">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43912-115">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="43912-116">Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu</span><span class="sxs-lookup"><span data-stu-id="43912-116">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
