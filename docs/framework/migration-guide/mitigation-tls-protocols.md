---
title: 'Ograniczenie: protokoły TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 45225d73ac60564d3e22c73270faab6b4e04d697
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457840"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="09bee-102">Ograniczenie: protokoły TLS</span><span class="sxs-lookup"><span data-stu-id="09bee-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="09bee-103">Począwszy od .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą używać jednego z następujących trzech protokołów: Tls1.0, Tls1.1 lub Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="09bee-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="09bee-104">Protokół SSL3.0 i szyfr RC4 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="09bee-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="09bee-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="09bee-105">Impact</span></span>  
 <span data-ttu-id="09bee-106">Ta zmiana dotyczy:</span><span class="sxs-lookup"><span data-stu-id="09bee-106">This change affects:</span></span>  
  
- <span data-ttu-id="09bee-107">Każda aplikacja, która używa protokołu SSL do rozmów z serwerem HTTPS <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest>lub <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient>serwerem gniazd przy użyciu dowolnego z następujących typów: , , , i <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="09bee-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="09bee-108">Każda aplikacja po stronie serwera, których nie można uaktualnić do obsługi tls1.0, Tls1.1 lub Tls 1.2..</span><span class="sxs-lookup"><span data-stu-id="09bee-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="09bee-109">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="09bee-109">Mitigation</span></span>  
 <span data-ttu-id="09bee-110">Zalecane ograniczenie jest uaktualnienie aplikacji po stronie sever do Tls1.0, Tls1.1 lub Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="09bee-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="09bee-111">Jeśli nie jest to możliwe lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext> klasa może służyć do rezygnacji z tej funkcji na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="09bee-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="09bee-112">Programowo, używając fragmentu kodu, takiego jak następujące:</span><span class="sxs-lookup"><span data-stu-id="09bee-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="09bee-113">Ponieważ <xref:System.Net.ServicePointManager> obiekt jest inicjowany tylko raz, definiowanie tych ustawień zgodności musi być pierwszą rzeczą, jaką robi aplikacja.</span><span class="sxs-lookup"><span data-stu-id="09bee-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="09bee-114">Dodając następujący wiersz do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="09bee-114">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="09bee-115">Należy jednak pamiętać, że rezygnacja z domyślnego zachowania nie jest zalecane, ponieważ sprawia, że aplikacja mniej bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="09bee-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09bee-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09bee-116">See also</span></span>

- [<span data-ttu-id="09bee-117">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="09bee-117">Application compatibility</span></span>](application-compatibility.md)
