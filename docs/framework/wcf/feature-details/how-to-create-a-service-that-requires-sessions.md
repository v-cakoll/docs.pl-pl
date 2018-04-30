---
title: 'Instrukcje: Tworzenie usługi wymagającej użycia sesji'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9fdf104c46757c7cf41082a2a0e134527b75b238
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="10e10-102">Instrukcje: Tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="10e10-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="10e10-103">Sesje utworzyć stanu udostępnionego między co najmniej dwa punkty końcowe, które umożliwia przydatne funkcje, takie jak wywołania zwrotne, zabezpieczeń z wieloma przeskokami i skojarzenia między klientami i wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="10e10-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="10e10-104">Aby uzyskać więcej informacji o sesji w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="10e10-104">For more information about sessions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="10e10-105">Aby określić, że kontrakt wymaga jego powiązanie obsługuje sesji</span><span class="sxs-lookup"><span data-stu-id="10e10-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="10e10-106">Tworzenie kontraktu usługi z co najmniej jedną operację.</span><span class="sxs-lookup"><span data-stu-id="10e10-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="10e10-107">Na przykład sposobu tworzenia kontraktu usługi zobacz [porady: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="10e10-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="10e10-108">Modyfikowanie <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> które deklaruje kontrakt przez ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości albo:</span><span class="sxs-lookup"><span data-stu-id="10e10-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="10e10-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Jeśli tego kontraktu musi być uruchamiane w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="10e10-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="10e10-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Jeśli tego kontraktu mogą być uruchamiane w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="10e10-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="10e10-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Jeśli nie wolno uruchamiać tej Umowy w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="10e10-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="10e10-112">Konfigurowanie punktu końcowego usługi do użycia powiązania, które obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="10e10-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="10e10-113">W poniższym przykładzie konfiguracji pokazano sposób użycia <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, który obsługuje WS`-`ReliableMessaging sesji.</span><span class="sxs-lookup"><span data-stu-id="10e10-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="10e10-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="10e10-114">Example</span></span>  
 <span data-ttu-id="10e10-115">Poniższy przykładowy kod przedstawia sposób określić wymaganie poziomie umowy sesji i przy użyciu pliku konfiguracji w celu spełnienia tego wymagania z <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> powiązania.</span><span class="sxs-lookup"><span data-stu-id="10e10-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="10e10-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10e10-116">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
