---
title: Środki zaradcze Protokoły TLS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e98b447028ef9fa96233a71133aa82184d83cec8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779157"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="f730f-102">Środki zaradcze Protokoły TLS</span><span class="sxs-lookup"><span data-stu-id="f730f-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="f730f-103">Począwszy od .NET Framework 4,6, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> klasy i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> mogą korzystać z jednego z trzech następujących protokołów: TLS 1.0, TLS 1.1 lub TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="f730f-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="f730f-104">Protokół SSL 3.0 i szyfr RC4 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f730f-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f730f-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="f730f-105">Impact</span></span>  
 <span data-ttu-id="f730f-106">Ta zmiana ma wpływ na:</span><span class="sxs-lookup"><span data-stu-id="f730f-106">This change affects:</span></span>  
  
- <span data-ttu-id="f730f-107">Każda aplikacja, która używa protokołu SSL do komunikowania się z serwerem HTTPS lub serwerem gniazda przy użyciu dowolnego z następujących <xref:System.Net.Http.HttpClient>typów <xref:System.Net.HttpWebRequest>: <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>,, <xref:System.Net.Security.SslStream>i.</span><span class="sxs-lookup"><span data-stu-id="f730f-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="f730f-108">Wszystkie aplikacje po stronie serwera, których nie można uaktualnić do obsługi protokołów TLS 1.0, TLS 1.1 i TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="f730f-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f730f-109">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="f730f-109">Mitigation</span></span>  
 <span data-ttu-id="f730f-110">Zalecane jest, aby uaktualnić aplikację po stronie serwera do protokołu TLS 1.0, TLS 1.1 lub TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="f730f-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="f730f-111">Jeśli nie jest to możliwe, lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext> można użyć klasy, aby zrezygnować z tej funkcji na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="f730f-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="f730f-112">Programowo, przy użyciu fragmentu kodu, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="f730f-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="f730f-113"><xref:System.Net.ServicePointManager> Ponieważ obiekt jest inicjowany tylko raz, zdefiniowanie tych ustawień zgodności musi być pierwszym działaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f730f-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="f730f-114">Dodając następujący wiersz do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="f730f-114">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="f730f-115">Należy jednak pamiętać, że niezalecane jest, aby zrezygnować z zachowania domyślnego, ponieważ sprawia, że aplikacja jest mniej bezpieczna.</span><span class="sxs-lookup"><span data-stu-id="f730f-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f730f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f730f-116">See also</span></span>

- [<span data-ttu-id="f730f-117">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="f730f-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
