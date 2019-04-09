---
title: 'Środki zaradcze: Protokoły TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70fab3dc418e3eb92e39a7c2b1365e8582b81834
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125097"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="e6268-102">Środki zaradcze: Protokoły TLS</span><span class="sxs-lookup"><span data-stu-id="e6268-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="e6268-103">Począwszy od programu .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą użyć jednego z następujących trzech protokołów: Tls1.0, Tls1.1 lub protokołu Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="e6268-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="e6268-104">Protokół SSL3.0 i szyfrowania RC4 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e6268-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e6268-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="e6268-105">Impact</span></span>  
 <span data-ttu-id="e6268-106">Ta zmiana ma wpływ na:</span><span class="sxs-lookup"><span data-stu-id="e6268-106">This change affects:</span></span>  
  
-   <span data-ttu-id="e6268-107">Dowolną aplikację, która używa protokołu SSL do komunikacji HTTPS lub serwera gniazda przy użyciu dowolnej z następujących typów: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, i <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="e6268-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
-   <span data-ttu-id="e6268-108">Dowolnej aplikacji po stronie serwera, którego nie można uaktualnić do obsługi Tls1.0, Tls1.1 lub protokołu Tls 1.2...</span><span class="sxs-lookup"><span data-stu-id="e6268-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e6268-109">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="e6268-109">Mitigation</span></span>  
 <span data-ttu-id="e6268-110">Zalecane środki zaradcze jest uaktualnienie aplikacji po stronie serwera do Tls1.0, Tls1.1 lub protokołu Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="e6268-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="e6268-111">Jeśli nie jest to możliwe, czy działają aplikacje klienckie <xref:System.AppContext> klasy można zrezygnować z tej funkcji w jednej z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="e6268-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
-   <span data-ttu-id="e6268-112">Programowo korzystając z fragmentu kodu, podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="e6268-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="e6268-113">Ponieważ <xref:System.Net.ServicePointManager> obiekt jest zainicjowany tylko raz, definiowania tych ustawień zgodności musi być pierwszą rzeczą, którą aplikacja wykonuje.</span><span class="sxs-lookup"><span data-stu-id="e6268-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
-   <span data-ttu-id="e6268-114">Dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="e6268-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="e6268-115">Należy jednak pamiętać, że rezygnacja z domyślnym zachowaniem jest niezalecane, ponieważ dzięki niemu aplikacja mniej bezpieczna opcja.</span><span class="sxs-lookup"><span data-stu-id="e6268-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6268-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6268-116">See also</span></span>

- [<span data-ttu-id="e6268-117">Zmiany przekierowania</span><span class="sxs-lookup"><span data-stu-id="e6268-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
