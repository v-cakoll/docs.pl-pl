---
title: HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f72a77e19d04c0dd55887628033f7c975ac3ff25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="http"></a><span data-ttu-id="55c84-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="55c84-102">HTTP</span></span>
<span data-ttu-id="55c84-103">.NET Framework zapewnia kompleksowe obsługę protokołu HTTP, dzięki czemu większość cały ruch internetowy, z <xref:System.Net.HttpWebRequest> i <xref:System.Net.HttpWebResponse> klasy.</span><span class="sxs-lookup"><span data-stu-id="55c84-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="55c84-104">Te klasy wyprowadzone z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, zwracane są domyślnie zawsze, gdy metody statycznej <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> napotka przez identyfikator URI rozpoczynający się od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="55c84-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="55c84-105">W większości przypadków **WebRequest** i **WebResponse** klasy podać wszystko jest to niezbędne do zapewnienia żądania, ale jeśli potrzebny jest dostęp do funkcji specyficzne dla protokołu HTTP udostępniony jako właściwości, można rzutowanie typu te klasy do **HttpWebRequest** lub **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="55c84-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="55c84-106">**HttpWebRequest** i **HttpWebResponse** hermetyzują standardowy transakcji żądanie i odpowiedź HTTP i zapewnienia dostępu do typowych nagłówków HTTP.</span><span class="sxs-lookup"><span data-stu-id="55c84-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="55c84-107">Te klasy również obsługiwać większość funkcje protokołu HTTP 1.1, w tym przetwarzanie potokowe, wysyłania i odbierania danych w fragmentów, uwierzytelniania wstępnego uwierzytelniania, szyfrowania, obsługi serwera proxy, weryfikacji certyfikatu serwera i zarządzanie połączeniami.</span><span class="sxs-lookup"><span data-stu-id="55c84-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="55c84-108">Przechowywane w i dostępne za pośrednictwem niestandardowe nagłówki i nagłówki nie są realizowane za pośrednictwem właściwości **nagłówki** właściwości.</span><span class="sxs-lookup"><span data-stu-id="55c84-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="55c84-109">**HttpWebRequest** jest używany przez domyślną klasę **WebRequest** i nie musi być zarejestrowane przed można przekazać identyfikatora URI do **WebRequest.Create** metody.</span><span class="sxs-lookup"><span data-stu-id="55c84-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="55c84-110">Umożliwia aplikacji wykonaj przekierowania HTTP automatycznie przez ustawienie <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> właściwości **true** (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="55c84-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="55c84-111">Aplikacja będzie przekierowywać żądania i <xref:System.Net.HttpWebResponse.ResponseUri%2A> właściwość **HttpWebResponse** będzie zawierać rzeczywiste zasobu sieci Web, który odpowiedział na żądanie.</span><span class="sxs-lookup"><span data-stu-id="55c84-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="55c84-112">Jeśli ustawisz **AllowAutoRedirect** do **false**, aplikacja musi mieć możliwość obsługi przekierowania jako błędy protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="55c84-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="55c84-113">Aplikacje odbierać błędy protokołu HTTP przez <xref:System.Net.WebException> z <xref:System.Net.WebException.Status%2A> ustawioną <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="55c84-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="55c84-114"><xref:System.Net.WebException.Response%2A> Właściwość zawiera **WebResponse** wysyłane przez serwer i wskazuje rzeczywiste wystąpił błąd protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="55c84-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c84-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55c84-115">See Also</span></span>  
 [<span data-ttu-id="55c84-116">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="55c84-116">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="55c84-117">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="55c84-117">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="55c84-118">Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="55c84-118">How to: Access HTTP-Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
