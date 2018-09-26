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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0c99e63f09d756bfff8cced846c2fe0f61722b8c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078451"
---
# <a name="http"></a><span data-ttu-id="5cfdc-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="5cfdc-102">HTTP</span></span>
<span data-ttu-id="5cfdc-103">Program .NET Framework oferuje kompleksowe wsparcie dla protokołu HTTP, co sprawia, że większość cały ruch z Internetu za pomocą <xref:System.Net.HttpWebRequest> i <xref:System.Net.HttpWebResponse> klasy.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="5cfdc-104">Te klasy pochodne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, zwracane są domyślnie zawsze wtedy, gdy metoda statyczna <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> napotka przez identyfikator URI rozpoczynający się od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="5cfdc-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="5cfdc-105">W większości przypadków **WebRequest** i **elementu WebResponse** klasy zapewnia wszystko co jest niezbędne do utworzenia żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu HTTP, widoczne jako właściwości, możesz rzutowanie typu te klasy **HttpWebRequest** lub **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="5cfdc-106">**HttpWebRequest** i **HttpWebResponse** hermetyzują standardowy transakcji żądań i odpowiedzi HTTP i zapewniają dostęp do wspólnych nagłówków HTTP.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="5cfdc-107">W ramach tych zajęć również obsługiwać większość funkcje protokołu HTTP 1.1, w tym przetwarzanie potokowe, wysyłania i odbierania danych w fragmentów, uwierzytelnianie, wstępnego uwierzytelniania, szyfrowanie, obsługa serwera proxy, weryfikacji certyfikatu serwera i zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="5cfdc-108">Przechowywane w i dostępne za pośrednictwem niestandardowych nagłówków i nagłówki nie są dostarczane za pośrednictwem właściwości **nagłówki** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="5cfdc-109">**HttpWebRequest** jest używany przez domyślną klasę **WebRequest** i nie musi zostać zarejestrowany, aby przekazać identyfikator URI, który ma **WebRequest.Create** metody.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="5cfdc-110">Można uczynić aplikację automatycznie podążał za przekierowaniami HTTP, ustawiając <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> właściwości **true** (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5cfdc-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="5cfdc-111">Aplikacja będzie przekierowywać żądania oraz <xref:System.Net.HttpWebResponse.ResponseUri%2A> właściwość **HttpWebResponse** będzie zawierać rzeczywistego zasobu sieci Web, która odpowiedział na żądanie.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="5cfdc-112">Jeśli ustawisz **AllowAutoRedirect** do **false**, aplikacja musi być w stanie obsłużyć przekierowań jako błędy protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="5cfdc-113">Aplikacje otrzymywać komunikaty o błędach protokołu HTTP przez Przechwytywanie <xref:System.Net.WebException> z <xref:System.Net.WebException.Status%2A> równa <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="5cfdc-114"><xref:System.Net.WebException.Response%2A> Właściwość zawiera **elementu WebResponse** wysłanych przez serwer i wskazuje rzeczywiste Napotkano błąd HTTP.</span><span class="sxs-lookup"><span data-stu-id="5cfdc-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cfdc-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cfdc-115">See Also</span></span>  
 [<span data-ttu-id="5cfdc-116">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="5cfdc-116">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="5cfdc-117">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="5cfdc-117">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="5cfdc-118">Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="5cfdc-118">How to: Access HTTP-Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
