---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 168bd57652aca5f3c1b61c90abea5288bd1a6719
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="a3602-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="a3602-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="a3602-103">`comContracts` Sekcja konfiguracji zawiera elementy, które pozwalają określić różne właściwości kontraktu usługi integracji COM +.</span><span class="sxs-lookup"><span data-stu-id="a3602-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="a3602-104">Określanie Namespace i kontraktu</span><span class="sxs-lookup"><span data-stu-id="a3602-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="a3602-105">Kontrakty usług integracji COM + są obecnie ograniczone do przestrzeni nazw "http://tempuri.org", a Nazwa kontraktu pochodzi od obsługi interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="a3602-105">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="a3602-106">Można jednak określić alternatywne przy użyciu `comContracts` sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a3602-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="a3602-107">Na przykład można użyć następującej konfiguracji do określenia nazwy przestrzeni nazw i kontraktu kontraktu usługi, a także opcję, aby wymusić użycie na powiązaniach sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="a3602-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
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
  
 <span data-ttu-id="a3602-108">Podczas inicjowania usługi określonych przestrzeni nazw i nazwy kontraktów są stosowane do opisów wygenerowanego usługi.</span><span class="sxs-lookup"><span data-stu-id="a3602-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="a3602-109">Ta sekcja jest pusta, inicjowanie usługi zastosowanie domyślną nazwę przestrzeni nazw i kontraktu pobranych z identyfikatorem obsługi interfejsu COM</span><span class="sxs-lookup"><span data-stu-id="a3602-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="a3602-110">Ponadto można użyć [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element, aby określić metod modelu COM +, które są dostępne, gdy interfejs składnika COM + jest udostępniany jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a3602-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="a3602-111">Można również użyć [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) do określenia możliwy do utrwalenia typów używanych w integracji.</span><span class="sxs-lookup"><span data-stu-id="a3602-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="a3602-112">Ponadto można użyć [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element, aby dołączyć użytkownika zdefiniowanych typów (UDT), które mają być uwzględniane w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="a3602-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3602-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3602-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="a3602-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="a3602-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="a3602-115">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="a3602-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="a3602-116">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="a3602-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="a3602-117">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="a3602-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="a3602-118">Współdziałanie z aplikacjami COM +</span><span class="sxs-lookup"><span data-stu-id="a3602-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="a3602-119">Porady: Konfigurowanie ustawień usług COM +</span><span class="sxs-lookup"><span data-stu-id="a3602-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
