---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69fbce3f312833c374a4c2615a15359d9c2db3a7
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="a13a7-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="a13a7-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="a13a7-103">`comContracts` Sekcja konfiguracji zawiera elementy, które pozwalają określić różne właściwości kontraktu usługi integracji COM +.</span><span class="sxs-lookup"><span data-stu-id="a13a7-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="a13a7-104">Określanie Namespace i kontraktu</span><span class="sxs-lookup"><span data-stu-id="a13a7-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="a13a7-105">Kontrakty usług integracji COM + są obecnie ograniczone do "http://tempuri.org" przestrzeni nazw i nazwy kontraktu jest pochodną obsługi interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="a13a7-105">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="a13a7-106">Można jednak określić alternatywne przy użyciu `comContracts` sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a13a7-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="a13a7-107">Na przykład można użyć następującej konfiguracji do określenia nazwy przestrzeni nazw i kontraktu kontraktu usługi, a także opcję, aby wymusić użycie na powiązaniach sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="a13a7-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="a13a7-108">Podczas inicjowania usługi określonych przestrzeni nazw i nazwy kontraktów są stosowane do opisów wygenerowanego usługi.</span><span class="sxs-lookup"><span data-stu-id="a13a7-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="a13a7-109">Ta sekcja jest pusta, inicjowanie usługi zastosowanie domyślną nazwę przestrzeni nazw i kontraktu pobranych z identyfikatorem obsługi interfejsu COM</span><span class="sxs-lookup"><span data-stu-id="a13a7-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="a13a7-110">Ponadto można użyć [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element, aby określić metod modelu COM +, które są dostępne, gdy interfejs składnika COM + jest udostępniany jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a13a7-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="a13a7-111">Można również użyć [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) do określenia możliwy do utrwalenia typów używanych w integracji.</span><span class="sxs-lookup"><span data-stu-id="a13a7-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="a13a7-112">Ponadto można użyć [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element, aby dołączyć użytkownika zdefiniowanych typów (UDT), które mają być uwzględniane w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="a13a7-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a13a7-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a13a7-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="a13a7-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="a13a7-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="a13a7-115">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="a13a7-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="a13a7-116">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="a13a7-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="a13a7-117">\<comContract></span><span class="sxs-lookup"><span data-stu-id="a13a7-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="a13a7-118">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="a13a7-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="a13a7-119">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="a13a7-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
