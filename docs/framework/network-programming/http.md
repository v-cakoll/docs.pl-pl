---
title: HTTP
ms.date: 03/30/2017
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
ms.openlocfilehash: c8c799a50e5d63bbf411c338eb9e93f85a942bb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048008"
---
# <a name="http"></a><span data-ttu-id="e2054-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="e2054-102">HTTP</span></span>
<span data-ttu-id="e2054-103">.NET Framework zapewnia kompleksową obsługę protokołu HTTP, który stanowi większość całego <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> ruchu internetowego, z i klas.</span><span class="sxs-lookup"><span data-stu-id="e2054-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="e2054-104">Te klasy, pochodne i <xref:System.Net.WebRequest> <xref:System.Net.WebResponse>, są zwracane domyślnie, gdy metoda <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> statyczna napotka identyfikator URI, począwszy od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="e2054-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="e2054-105">W większości przypadków **WebRequest** i **WebResponse** klasy zapewniają wszystko, co jest niezbędne do żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu HTTP udostępniane jako właściwości, można typecast tych klas do **HttpWebRequest** lub **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="e2054-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="e2054-106">**HttpWebRequest** i **HttpWebResponse** hermetyzują standardową transakcję żądania i odpowiedzi HTTP i zapewnij dostęp do typowych nagłówków HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2054-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="e2054-107">Klasy te obsługują również większość funkcji HTTP 1.1, w tym tworzenie potoków, wysyłanie i odbieranie danych w fragmentach, uwierzytelnianie, preauthentication, szyfrowanie, obsługa serwera proxy, sprawdzanie poprawności certyfikatów serwera i zarządzanie połączeniami.</span><span class="sxs-lookup"><span data-stu-id="e2054-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="e2054-108">Niestandardowe nagłówki i nagłówki nie są dostarczane za pośrednictwem właściwości mogą być przechowywane i dostępne za pośrednictwem **headers** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e2054-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="e2054-109">**HttpWebRequest** jest domyślną klasą używaną przez **WebRequest** i nie musi być zarejestrowana, zanim będzie można przekazać identyfikator URI do **WebRequest.Create** metody.</span><span class="sxs-lookup"><span data-stu-id="e2054-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="e2054-110">Aplikację można automatycznie śledzić przekierowania HTTP, <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> ustawiając właściwość na **true** (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="e2054-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="e2054-111">Aplikacja przekieruje żądania, a <xref:System.Net.HttpWebResponse.ResponseUri%2A> właściwość **HttpWebResponse** będzie zawierać rzeczywisty zasób sieci Web, który odpowiedział na żądanie.</span><span class="sxs-lookup"><span data-stu-id="e2054-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="e2054-112">Jeśli ustawisz **AllowAutoRedirect** na **false,** aplikacja musi mieć możliwość obsługi przekierowań jako błędy protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2054-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="e2054-113">Aplikacje otrzymują błędy protokołu <xref:System.Net.WebException> HTTP, <xref:System.Net.WebException.Status%2A> łapiąc a z zestawem do <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="e2054-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="e2054-114">Właściwość <xref:System.Net.WebException.Response%2A> zawiera **WebResponse** wysłane przez serwer i wskazuje rzeczywisty błąd HTTP napotkany.</span><span class="sxs-lookup"><span data-stu-id="e2054-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2054-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2054-115">See also</span></span>

- [<span data-ttu-id="e2054-116">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="e2054-116">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="e2054-117">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="e2054-117">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="e2054-118">Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="e2054-118">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
