---
title: "Instrukcje: Tworzenie usługi wymagającej użycia sesji"
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
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e238598ccd33d9e6e77a2d09ea3b19fdefcefbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="69c1f-102">Instrukcje: Tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="69c1f-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="69c1f-103">Sesje utworzyć stanu udostępnionego między co najmniej dwa punkty końcowe, które umożliwia przydatne funkcje, takie jak wywołania zwrotne, zabezpieczeń z wieloma przeskokami i skojarzenia między klientami i wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="69c1f-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="69c1f-104">Sesje w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="69c1f-104"> sessions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="69c1f-105">Aby określić, że kontrakt wymaga jego powiązanie obsługuje sesji</span><span class="sxs-lookup"><span data-stu-id="69c1f-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="69c1f-106">Tworzenie kontraktu usługi z co najmniej jedną operację.</span><span class="sxs-lookup"><span data-stu-id="69c1f-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="69c1f-107">Na przykład sposobu tworzenia kontraktu usługi zobacz [porady: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="69c1f-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="69c1f-108">Modyfikowanie <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> które deklaruje kontrakt przez ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości albo:</span><span class="sxs-lookup"><span data-stu-id="69c1f-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="69c1f-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Jeśli tego kontraktu musi być uruchamiane w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="69c1f-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="69c1f-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Jeśli tego kontraktu mogą być uruchamiane w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="69c1f-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="69c1f-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Jeśli nie wolno uruchamiać tej Umowy w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="69c1f-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="69c1f-112">Konfigurowanie punktu końcowego usługi do użycia powiązania, które obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="69c1f-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="69c1f-113">W poniższym przykładzie konfiguracji pokazano sposób użycia <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, który obsługuje WS`-`ReliableMessaging sesji.</span><span class="sxs-lookup"><span data-stu-id="69c1f-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="69c1f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="69c1f-114">Example</span></span>  
 <span data-ttu-id="69c1f-115">Poniższy przykładowy kod przedstawia sposób określić wymaganie poziomie umowy sesji i przy użyciu pliku konfiguracji w celu spełnienia tego wymagania z <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> powiązania.</span><span class="sxs-lookup"><span data-stu-id="69c1f-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="69c1f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69c1f-116">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
