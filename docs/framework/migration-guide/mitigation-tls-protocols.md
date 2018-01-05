---
title: "Ograniczenie: protokoły TLS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53a1100e40edb700d51fe907d3dc94c6216c4ebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="db290-102">Ograniczenie: protokoły TLS</span><span class="sxs-lookup"><span data-stu-id="db290-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="db290-103">W programie .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą użyć jednego z trzech następujących protokołów: Tls1.0, Tls1.1 lub protokołu Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="db290-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="db290-104">Protokół SSL3.0 i szyfrowania RC4 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="db290-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="db290-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="db290-105">Impact</span></span>  
 <span data-ttu-id="db290-106">Ta zmiana wpływa na:</span><span class="sxs-lookup"><span data-stu-id="db290-106">This change affects:</span></span>  
  
-   <span data-ttu-id="db290-107">Dowolną aplikację, która używa protokołu SSL do komunikowania się HTTPS lub serwera gniazda przy użyciu dowolnego z następujących typów: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, i <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="db290-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
-   <span data-ttu-id="db290-108">Dowolną aplikację po stronie serwera, którego nie można uaktualnić do obsługi Tls1.0, Tls1.1 lub protokołu Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="db290-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="db290-109">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="db290-109">Mitigation</span></span>  
 <span data-ttu-id="db290-110">Ograniczenie zalecane jest uaktualnienie aplikacji po stronie serwera do Tls1.0, Tls1.1 lub protokołu Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="db290-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="db290-111">Jeśli nie jest to możliwe, czy aplikacje klienckie są dzielone, <xref:System.AppContext> klasy można zrezygnować z tej funkcji w jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="db290-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
-   <span data-ttu-id="db290-112">Programowo używając fragment kodu, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="db290-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="db290-113">Ponieważ <xref:System.Net.ServicePointManager> obiekt został zainicjowany tylko raz, definiowania tych ustawień zgodności należy najpierw jest aplikacja.</span><span class="sxs-lookup"><span data-stu-id="db290-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
-   <span data-ttu-id="db290-114">Dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="db290-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="db290-115">Należy jednak pamiętać, że rezygnacja z domyślne zachowanie nie jest zalecane, ponieważ ułatwia aplikacji mniej bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="db290-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db290-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db290-116">See Also</span></span>  
 [<span data-ttu-id="db290-117">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="db290-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
