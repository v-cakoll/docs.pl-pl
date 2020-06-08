---
title: HTTP
description: Zapoznaj się z kompleksową obsługą protokołu HTTP, którą zapewnia .NET Framework przy użyciu klas HttpWebRequest i HttpWebResponse.
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
ms.openlocfilehash: ffb7a5d027ef7691d03caf0ac45d4a3dd9bdb652
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502421"
---
# <a name="http"></a><span data-ttu-id="cd782-103">HTTP</span><span class="sxs-lookup"><span data-stu-id="cd782-103">HTTP</span></span>
<span data-ttu-id="cd782-104">.NET Framework zapewnia kompleksową pomoc techniczną dla protokołu HTTP, która stanowi większość całego ruchu internetowego z <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> klasami i.</span><span class="sxs-lookup"><span data-stu-id="cd782-104">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="cd782-105">Klasy pochodne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> , są zwracane domyślnie za każdym razem, gdy metoda statyczna <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> napotka identyfikator URI rozpoczynający się od ciągu "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="cd782-105">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="cd782-106">W większości przypadków klasy **WebRequest** i **WebResponse** zapewniają wszystko, co jest niezbędne do wykonania żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu HTTP udostępnianych jako właściwości, można rzutowanie te klasy do **HttpWebRequest** lub **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="cd782-106">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="cd782-107">**HttpWebRequest** i **HttpWebResponse** hermetyzują standardową transakcję http żądanie i odpowiedź i zapewniają dostęp do typowych nagłówków HTTP.</span><span class="sxs-lookup"><span data-stu-id="cd782-107">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="cd782-108">Te klasy obsługują również większość funkcji protokołu HTTP 1,1, w tym przetwarzanie potokowe, wysyłanie i pobieranie danych w fragmentach, uwierzytelnianiu, wstępnemu uwierzytelnianiu, szyfrowaniu, obsłudze serwera proxy, weryfikacji certyfikatu serwera i zarządzaniu połączeniami.</span><span class="sxs-lookup"><span data-stu-id="cd782-108">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="cd782-109">Niestandardowe nagłówki i nagłówki, które nie są przekazywane za pomocą właściwości, mogą być przechowywane w i dostępne za pomocą właściwości **Headers** .</span><span class="sxs-lookup"><span data-stu-id="cd782-109">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="cd782-110">**HttpWebRequest** jest domyślną klasą używaną przez **WebRequest** i nie musi być zarejestrowana przed przekazaniem identyfikatora URI do metody **WebRequest. Create** .</span><span class="sxs-lookup"><span data-stu-id="cd782-110">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="cd782-111">Można sprawić, aby aplikacja automatycznie przekierowała protokół HTTP przez ustawienie <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> dla właściwości **wartości true** (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="cd782-111">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="cd782-112">Aplikacja będzie przekierowywać żądania, a <xref:System.Net.HttpWebResponse.ResponseUri%2A> Właściwość **HttpWebResponse** będzie zawierać rzeczywisty zasób sieci Web, który odpowiedział na żądanie.</span><span class="sxs-lookup"><span data-stu-id="cd782-112">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="cd782-113">Jeśli ustawisz **AllowAutoRedirect** na **false**, aplikacja musi być w stanie obsłużyć przekierowania jako błędy protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="cd782-113">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="cd782-114">Aplikacje odbierają błędy protokołu HTTP przez przechwycenie <xref:System.Net.WebException> z <xref:System.Net.WebException.Status%2A> zestawem do <xref:System.Net.WebExceptionStatus> .</span><span class="sxs-lookup"><span data-stu-id="cd782-114">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="cd782-115"><xref:System.Net.WebException.Response%2A>Właściwość zawiera **WebResponse** wysyłany przez serwer i wskazuje rzeczywisty błąd http.</span><span class="sxs-lookup"><span data-stu-id="cd782-115">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd782-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd782-116">See also</span></span>

- [<span data-ttu-id="cd782-117">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="cd782-117">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="cd782-118">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="cd782-118">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="cd782-119">Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="cd782-119">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
