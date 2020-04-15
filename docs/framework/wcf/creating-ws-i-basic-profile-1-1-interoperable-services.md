---
title: Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: fd7828cccb1a19a17e899525d863021d3670fbdd
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389764"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="6e867-102">Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I</span><span class="sxs-lookup"><span data-stu-id="6e867-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="6e867-103">Aby skonfigurować punkt końcowy usługi WCF jako interoperacyjny z klientami usługi sieci Web ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="6e867-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="6e867-104">Użyj <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typu jako typ powiązania dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="6e867-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="6e867-105">Nie należy używać funkcji wywołania zwrotnego i umowy sesji ani zachowań transakcji w punkcie końcowym usługi</span><span class="sxs-lookup"><span data-stu-id="6e867-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="6e867-106">Opcjonalnie można włączyć obsługę https i uwierzytelniania klienta na poziomie transportu na powiązanie.</span><span class="sxs-lookup"><span data-stu-id="6e867-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="6e867-107">Następujące funkcje <xref:System.ServiceModel.BasicHttpBinding> klasy wymagają funkcjonalności poza profilem podstawowym WS-I 1.1:</span><span class="sxs-lookup"><span data-stu-id="6e867-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="6e867-108">Kodowanie komunikatów mechanizmu optymalizacji transmisji wiadomości <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> (MTOM) kontrolowane przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="6e867-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6e867-109">Pozostaw tę właściwość według <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> wartości domyślnej, która nie ma używać MTOM.</span><span class="sxs-lookup"><span data-stu-id="6e867-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="6e867-110">Zabezpieczenia wiadomości kontrolowane <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> przez wartość zapewnia ws-security wsparcie zgodne z WS-I Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="6e867-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="6e867-111">Pozostaw tę właściwość według <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> wartości domyślnej, która nie ma używać programu WS-Security.</span><span class="sxs-lookup"><span data-stu-id="6e867-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="6e867-112">Aby udostępnić metadane usługi WCF ASP.NET, użyj narzędzi do generowania klienta usługi [sieci Web: Narzędzia języka opisu usług sieci Web (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Narzędzie odnajdowania usług sieci Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)i funkcja **Dodaj odwołanie do sieci Web** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e867-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="6e867-113">Włącz publikację metadanych.</span><span class="sxs-lookup"><span data-stu-id="6e867-113">Enable metadata publication.</span></span> <span data-ttu-id="6e867-114">Aby uzyskać więcej informacji, zobacz [Publikowanie punktów końcowych metadanych](publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="6e867-114">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e867-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e867-115">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6e867-116">Opis</span><span class="sxs-lookup"><span data-stu-id="6e867-116">Description</span></span>  
 <span data-ttu-id="6e867-117">Poniższy przykładowy kod pokazuje, jak dodać punkt końcowy WCF, który jest zgodny z ASP.NET klientami usługi sieci Web w kodzie i, alternatywnie, w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6e867-117">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6e867-118">Code</span><span class="sxs-lookup"><span data-stu-id="6e867-118">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6e867-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e867-119">See also</span></span>

- [<span data-ttu-id="6e867-120">Współdziałanie z usługami ASP.NET w sieci Web</span><span class="sxs-lookup"><span data-stu-id="6e867-120">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
