---
title: 'Instrukcje: Tworzenie usługi wymagającej użycia sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 29c2a87daaf763a50aa657c9badc002ff2fa27e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593337"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="9e6c8-102">Instrukcje: Tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="9e6c8-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="9e6c8-103">Sesje tworzą współużytkowany stan między dwoma lub więcej punktami końcowymi, które umożliwiają korzystanie z użytecznych funkcji, takich jak wywołania zwrotne, zabezpieczenia z wieloma przeskokami oraz skojarzenia między klientami a wystąpieniami usługi.</span><span class="sxs-lookup"><span data-stu-id="9e6c8-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="9e6c8-104">Aby uzyskać więcej informacji na temat sesji w aplikacjach Windows Communication Foundation (WCF), zobacz [using Sessions](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="9e6c8-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="9e6c8-105">Aby określić, że kontrakt wymaga powiązania z obsługą sesji</span><span class="sxs-lookup"><span data-stu-id="9e6c8-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="9e6c8-106">Utwórz kontrakt usługi z co najmniej jedną operacją.</span><span class="sxs-lookup"><span data-stu-id="9e6c8-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="9e6c8-107">Aby zapoznać się z przykładem sposobu tworzenia kontraktu usługi, zobacz [How to: define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9e6c8-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="9e6c8-108">Zmodyfikuj <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> , który deklaruje kontrakt, ustawiając <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> Właściwość na wartość:</span><span class="sxs-lookup"><span data-stu-id="9e6c8-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="9e6c8-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Jeśli ta umowa musi być uruchomiona w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="9e6c8-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="9e6c8-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Jeśli ten kontrakt można uruchomić w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="9e6c8-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="9e6c8-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Jeśli tego kontraktu nie można uruchomić w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="9e6c8-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="9e6c8-112">Skonfiguruj punkt końcowy usługi tak, aby korzystał z powiązania, które obsługuje sesje.</span><span class="sxs-lookup"><span data-stu-id="9e6c8-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="9e6c8-113">Poniższy przykład konfiguracji przedstawia użycie programu <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> , który obsługuje `-` sesję WS ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="9e6c8-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="9e6c8-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e6c8-114">Example</span></span>  
 <span data-ttu-id="9e6c8-115">Poniższy przykładowy kod pokazuje, jak określić wymaganie dotyczące sesji na poziomie kontraktu i użyć pliku konfiguracji do obsługi tego wymagania przy użyciu <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> powiązania.</span><span class="sxs-lookup"><span data-stu-id="9e6c8-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="9e6c8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e6c8-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
