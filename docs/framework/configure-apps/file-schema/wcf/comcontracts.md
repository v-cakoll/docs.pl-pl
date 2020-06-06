---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69919477"
---
# \<comContracts>
<span data-ttu-id="84a53-101">`comContracts`Sekcja konfiguracji zawiera elementy, które pozwalają określić różne właściwości kontraktu usługi integracji modelu com+.</span><span class="sxs-lookup"><span data-stu-id="84a53-101">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="84a53-102">Określanie przestrzeni nazw i kontraktu</span><span class="sxs-lookup"><span data-stu-id="84a53-102">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="84a53-103">Kontrakty usługi integracji modelu COM+ są obecnie ograniczone do `http://tempuri.org` przestrzeni nazw, a nazwa kontraktu pochodzi od pomocniczego interfejsu com.</span><span class="sxs-lookup"><span data-stu-id="84a53-103">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="84a53-104">Można jednak określić alternatywy przy użyciu `comContracts` sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="84a53-104">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="84a53-105">Można na przykład użyć poniższej konfiguracji, aby określić przestrzeń nazw i nazwę kontraktu dla kontraktu usługi, a także opcję wymuszać użycie na powiązaniach sesji.</span><span class="sxs-lookup"><span data-stu-id="84a53-105">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="84a53-106">Po zainicjowaniu usługi określone nazwy obszarów nazw i kontraktów są stosowane do opisów wygenerowanych usług.</span><span class="sxs-lookup"><span data-stu-id="84a53-106">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="84a53-107">Gdy ta sekcja jest pusta, Inicjalizacja usługi stosuje domyślną przestrzeń nazw i nazwę kontraktu pobraną z pomocniczego identyfikatora interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="84a53-107">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="84a53-108">Ponadto można użyć [\<exposedMethod>](exposedmethod.md) elementu, aby określić metody modelu COM+, które są dostępne, gdy interfejs składnika modelu com+ jest uwidoczniony jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="84a53-108">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="84a53-109">Można również użyć, [\<persistableTypes>](persistabletypes.md) Aby określić typy utrwalane używane w integracji.</span><span class="sxs-lookup"><span data-stu-id="84a53-109">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="84a53-110">Na koniec można użyć elementu, [\<userDefinedType>](userdefinedtype.md) Aby uwzględnić typy zdefiniowane przez użytkownika (UDT), które mają zostać uwzględnione w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="84a53-110">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a53-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84a53-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [<span data-ttu-id="84a53-112">Integrowanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="84a53-112">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="84a53-113">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="84a53-113">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
