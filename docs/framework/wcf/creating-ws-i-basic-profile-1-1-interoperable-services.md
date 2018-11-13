---
title: Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: f32308a17e2934b6884140307074f97e6b51f5f9
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982857"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="4bd0c-102">Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I</span><span class="sxs-lookup"><span data-stu-id="4bd0c-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="4bd0c-103">Aby skonfigurować punkt końcowy usługi WCF do współdziałać z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] obsługi klientów w sieci Web:</span><span class="sxs-lookup"><span data-stu-id="4bd0c-103">To configure a WCF service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="4bd0c-104">Użyj <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ powiązania punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="4bd0c-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="4bd0c-105">Nie używaj wywołania zwrotnego i funkcje kontraktu sesji lub zachowania transakcji do punktu końcowego usługi</span><span class="sxs-lookup"><span data-stu-id="4bd0c-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="4bd0c-106">Opcjonalnie można włączyć obsługę protokołu HTTPS i uwierzytelniania klienta na poziomie transportu w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="4bd0c-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="4bd0c-107">Poniższe funkcje <xref:System.ServiceModel.BasicHttpBinding> klasy wymagają funkcji równoważenia obciążenia po przekroczeniu WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="4bd0c-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="4bd0c-108">Kodowanie komunikatu mechanizmu optymalizacji transmisji (MTOM) komunikatu w wartości clientauthtrustmode <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4bd0c-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4bd0c-109">Pozostaw tę właściwość jako wartość domyślną, czyli <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> nieużywanie MTOM.</span><span class="sxs-lookup"><span data-stu-id="4bd0c-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="4bd0c-110">Zabezpieczenia w wartości clientauthtrustmode wiadomości <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> wartość zapewnia obsługę protokołu WS-Security zgodne z protokołu WS-I Basic 1.0 profilu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4bd0c-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="4bd0c-111">Pozostaw tę właściwość jako wartość domyślną, czyli <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nieużywanie WS-Security.</span><span class="sxs-lookup"><span data-stu-id="4bd0c-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="4bd0c-112">Aby udostępnić metadanych dla usługi WCF [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], użyj narzędzia generowania klienta usługi sieci Web: [narzędzia języka opisu usługi sieci Web (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [narzędzia odnajdywania usług sieci Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)i `Add Web Reference` funkcja w programie Visual Studio; należy włączyć publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="4bd0c-112">To make the metadata for a WCF service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="4bd0c-113">Aby uzyskać więcej informacji, zobacz [publikowanie punktów końcowych metadanych](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="4bd0c-113">For more information, see [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bd0c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bd0c-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4bd0c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4bd0c-115">Description</span></span>  
 <span data-ttu-id="4bd0c-116">Poniższy przykład kodu demonstruje sposób dodawania punktu końcowego WCF, która jest zgodna z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sieci Web obsługi klientów w kodzie, a także w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4bd0c-116">The following example code demonstrates how to add a WCF endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4bd0c-117">Kod</span><span class="sxs-lookup"><span data-stu-id="4bd0c-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4bd0c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4bd0c-118">See Also</span></span>  
 [<span data-ttu-id="4bd0c-119">Współdziałanie z usługami ASP.NET w sieci Web</span><span class="sxs-lookup"><span data-stu-id="4bd0c-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
