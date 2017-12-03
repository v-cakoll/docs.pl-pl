---
title: "Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I"
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
helpviewer_keywords: configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 500e57b36bbbdd1d23e6efb2c50421e3e134bcb3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="5f25a-102">Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I</span><span class="sxs-lookup"><span data-stu-id="5f25a-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="5f25a-103">Aby skonfigurować [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] punktu końcowego usługi do współdziałać z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] obsługi klientów w sieci Web:</span><span class="sxs-lookup"><span data-stu-id="5f25a-103">To configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="5f25a-104">Użyj <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typu powiązanie dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5f25a-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="5f25a-105">Nie używaj wywołania zwrotnego i funkcje kontraktu sesji lub transakcji zachowania punktu końcowego usługi</span><span class="sxs-lookup"><span data-stu-id="5f25a-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="5f25a-106">Opcjonalnie można włączyć obsługę uwierzytelniania klienta na poziomie transportu dla powiązania i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5f25a-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="5f25a-107">Poniższe funkcje <xref:System.ServiceModel.BasicHttpBinding> klasy wymagają funkcji poza WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="5f25a-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="5f25a-108">Kodowanie komunikatu mechanizmu optymalizacji transmisji (MTOM) komunikatu kontrolowane przez <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5f25a-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5f25a-109">Pozostaw tę właściwość na wartość domyślną, która jest <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> aby nie używać mechanizmu MTOM.</span><span class="sxs-lookup"><span data-stu-id="5f25a-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="5f25a-110">Kontrolowane przez zabezpieczenia wiadomości <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> wartość zapewnia obsługę WS-Security zgodne z WS-I Basic 1.0 profil zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5f25a-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="5f25a-111">Pozostaw tę właściwość na wartość domyślną, która jest <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nieużywanie WS-Security.</span><span class="sxs-lookup"><span data-stu-id="5f25a-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="5f25a-112">Aby uzyskać metadanych [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dostępnych usług do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], użyj narzędzia generowania klienta usługi sieci Web: [narzędzia języka opisu usługi sieci Web (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [narzędzia odnajdywania usług sieci Web ( DISCO.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979)i `Add Web Reference` w narzędziu [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; należy włączyć publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="5f25a-112">To make the metadata for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Services Discovery Tool (Disco.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979), and the `Add Web Reference` feature in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; you must enable metadata publication.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="5f25a-113">[Publikowania punkty końcowe metadanych](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="5f25a-113"> [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f25a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f25a-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5f25a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5f25a-115">Description</span></span>  
 <span data-ttu-id="5f25a-116">Poniższy przykładowy kod przedstawia sposób dodawania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] punktu końcowego, który jest zgodny z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sieci Web obsługi klientów w kodzie i alternatywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5f25a-116">The following example code demonstrates how to add a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5f25a-117">Kod</span><span class="sxs-lookup"><span data-stu-id="5f25a-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5f25a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f25a-118">See Also</span></span>  
 [<span data-ttu-id="5f25a-119">Współdziałanie z usługami sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5f25a-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
