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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048008"
---
# <a name="http"></a><span data-ttu-id="feafb-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="feafb-102">HTTP</span></span>
<span data-ttu-id="feafb-103">.NET Framework zapewnia kompleksową pomoc techniczną dla protokołu HTTP, która stanowi większość całego ruchu internetowego z <xref:System.Net.HttpWebRequest> klasami i. <xref:System.Net.HttpWebResponse></span><span class="sxs-lookup"><span data-stu-id="feafb-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="feafb-104">Klasy pochodne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, są zwracane domyślnie za każdym razem, gdy metoda <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> statyczna napotka identyfikator URI rozpoczynający się od ciągu "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="feafb-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="feafb-105">W większości przypadków klasy **WebRequest** i **WebResponse** zapewniają wszystko, co jest niezbędne do wykonania żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu HTTP udostępnianych jako właściwości, można rzutowanie te klasy na **HttpWebRequest** lub **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="feafb-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="feafb-106">**HttpWebRequest** i **HttpWebResponse** hermetyzują standardową transakcję http żądanie i odpowiedź i zapewniają dostęp do typowych nagłówków HTTP.</span><span class="sxs-lookup"><span data-stu-id="feafb-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="feafb-107">Te klasy obsługują również większość funkcji protokołu HTTP 1,1, w tym przetwarzanie potokowe, wysyłanie i pobieranie danych w fragmentach, uwierzytelnianiu, wstępnemu uwierzytelnianiu, szyfrowaniu, obsłudze serwera proxy, weryfikacji certyfikatu serwera i zarządzaniu połączeniami.</span><span class="sxs-lookup"><span data-stu-id="feafb-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="feafb-108">Niestandardowe nagłówki i nagłówki, które nie są przekazywane za pomocą właściwości, mogą być przechowywane w i dostępne za pomocą właściwości **Headers** .</span><span class="sxs-lookup"><span data-stu-id="feafb-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="feafb-109">**HttpWebRequest** jest domyślną klasą używaną przez **WebRequest** i nie musi być zarejestrowana przed przekazaniem identyfikatora URI do metody **WebRequest. Create** .</span><span class="sxs-lookup"><span data-stu-id="feafb-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="feafb-110">Można sprawić, aby aplikacja automatycznie przekierowała protokół HTTP przez ustawienie <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> dla właściwości **wartości true** (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="feafb-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="feafb-111">Aplikacja będzie przekierowywać żądania, a <xref:System.Net.HttpWebResponse.ResponseUri%2A> Właściwość **HttpWebResponse** będzie zawierać rzeczywisty zasób sieci Web, który odpowiedział na żądanie.</span><span class="sxs-lookup"><span data-stu-id="feafb-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="feafb-112">Jeśli ustawisz **AllowAutoRedirect** na **false**, aplikacja musi być w stanie obsłużyć przekierowania jako błędy protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="feafb-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="feafb-113">Aplikacje odbierają błędy protokołu HTTP przez przechwycenie <xref:System.Net.WebException> <xref:System.Net.WebException.Status%2A> z zestawem <xref:System.Net.WebExceptionStatus>do.</span><span class="sxs-lookup"><span data-stu-id="feafb-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="feafb-114">Właściwość zawiera WebResponse wysyłany przez serwer i wskazuje rzeczywisty błąd http. <xref:System.Net.WebException.Response%2A></span><span class="sxs-lookup"><span data-stu-id="feafb-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feafb-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="feafb-115">See also</span></span>

- [<span data-ttu-id="feafb-116">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="feafb-116">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="feafb-117">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="feafb-117">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="feafb-118">Instrukcje: Dostęp do właściwości specyficznych dla protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="feafb-118">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
