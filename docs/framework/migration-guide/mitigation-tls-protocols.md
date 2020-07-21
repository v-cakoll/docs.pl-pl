---
title: 'Ograniczenie: protokoły TLS'
description: Dowiedz się więcej na temat wpływu i łagodzenia zmian protokołu TLS, zaczynając od .NET Framework 4,6.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: bb5aab3361663d7b5401d7e68688265fbc65b36f
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475362"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="dc02e-103">Ograniczenie: protokoły TLS</span><span class="sxs-lookup"><span data-stu-id="dc02e-103">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="dc02e-104">Począwszy od .NET Framework 4,6, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> klasy i mogą <xref:System.Net.Security.SslStream?displayProperty=nameWithType> korzystać z jednego z następujących trzech protokołów: TLS 1.0, TLS 1.1 lub TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="dc02e-104">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="dc02e-105">Protokół SSL 3.0 i szyfr RC4 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dc02e-105">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="dc02e-106">Wpływ</span><span class="sxs-lookup"><span data-stu-id="dc02e-106">Impact</span></span>  
 <span data-ttu-id="dc02e-107">Ta zmiana ma wpływ na:</span><span class="sxs-lookup"><span data-stu-id="dc02e-107">This change affects:</span></span>  
  
- <span data-ttu-id="dc02e-108">Każda aplikacja, która używa protokołu SSL do komunikowania się z serwerem HTTPS lub serwerem gniazda przy użyciu dowolnego z następujących typów: <xref:System.Net.Http.HttpClient> , <xref:System.Net.HttpWebRequest> ,, <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient> i <xref:System.Net.Security.SslStream> .</span><span class="sxs-lookup"><span data-stu-id="dc02e-108">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="dc02e-109">Wszystkie aplikacje po stronie serwera, których nie można uaktualnić do obsługi protokołów TLS 1.0, TLS 1.1 i TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="dc02e-109">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="dc02e-110">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="dc02e-110">Mitigation</span></span>  
 <span data-ttu-id="dc02e-111">Zalecane jest, aby uaktualnić aplikację po stronie serwera do protokołu TLS 1.0, TLS 1.1 lub TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="dc02e-111">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="dc02e-112">Jeśli nie jest to możliwe, lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext> można użyć klasy, aby zrezygnować z tej funkcji na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="dc02e-112">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="dc02e-113">Programowo, przy użyciu fragmentu kodu, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="dc02e-113">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="dc02e-114">Ponieważ <xref:System.Net.ServicePointManager> obiekt jest inicjowany tylko raz, zdefiniowanie tych ustawień zgodności musi być pierwszym działaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc02e-114">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="dc02e-115">Dodając następujący wiersz do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="dc02e-115">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="dc02e-116">Należy jednak pamiętać, że niezalecane jest, aby zrezygnować z zachowania domyślnego, ponieważ sprawia, że aplikacja jest mniej bezpieczna.</span><span class="sxs-lookup"><span data-stu-id="dc02e-116">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc02e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc02e-117">See also</span></span>

- [<span data-ttu-id="dc02e-118">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="dc02e-118">Application compatibility</span></span>](application-compatibility.md)
