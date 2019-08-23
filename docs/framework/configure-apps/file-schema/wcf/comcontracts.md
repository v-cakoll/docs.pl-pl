---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919477"
---
# <a name="comcontracts"></a><span data-ttu-id="ffc7b-101">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="ffc7b-101">\<comContracts></span></span>
<span data-ttu-id="ffc7b-102">Sekcja `comContracts` konfiguracji zawiera elementy, które pozwalają określić różne właściwości kontraktu usługi integracji modelu com+.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="ffc7b-103">Określanie przestrzeni nazw i kontraktu</span><span class="sxs-lookup"><span data-stu-id="ffc7b-103">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="ffc7b-104">Kontrakty usługi integracji modelu COM+ są obecnie ograniczone `http://tempuri.org` do przestrzeni nazw, a nazwa kontraktu pochodzi od pomocniczego interfejsu com.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="ffc7b-105">Można jednak określić alternatywy przy użyciu `comContracts` sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="ffc7b-106">Można na przykład użyć poniższej konfiguracji, aby określić przestrzeń nazw i nazwę kontraktu dla kontraktu usługi, a także opcję wymuszać użycie na powiązaniach sesji.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="ffc7b-107">Po zainicjowaniu usługi określone nazwy obszarów nazw i kontraktów są stosowane do opisów wygenerowanych usług.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="ffc7b-108">Gdy ta sekcja jest pusta, Inicjalizacja usługi stosuje domyślną przestrzeń nazw i nazwę kontraktu pobraną z pomocniczego identyfikatora interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="ffc7b-109">Ponadto można użyć [ \<elementu exposedMethod >](exposedmethod.md) , aby określić metody modelu COM+, które są dostępne, gdy interfejs składnika modelu com+ jest uwidoczniony jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-109">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="ffc7b-110">Można również użyć [ \<> persistableTypes](persistabletypes.md) do określenia typów trwałych używanych w ramach integracji.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-110">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="ffc7b-111">Na koniec można użyć [ \<elementu userDefinedType >](userdefinedtype.md) , aby uwzględnić typy zdefiniowane przez użytkownika (UDT), które mają być uwzględnione w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="ffc7b-111">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc7b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffc7b-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="ffc7b-113">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="ffc7b-113">\<exposedMethod></span></span>](exposedmethod.md)
- [<span data-ttu-id="ffc7b-114">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="ffc7b-114">\<persistableTypes></span></span>](persistabletypes.md)
- [<span data-ttu-id="ffc7b-115">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="ffc7b-115">\<userDefinedType></span></span>](userdefinedtype.md)
- [<span data-ttu-id="ffc7b-116">\<comContract></span><span class="sxs-lookup"><span data-stu-id="ffc7b-116">\<comContract></span></span>](comcontract.md)
- [<span data-ttu-id="ffc7b-117">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="ffc7b-117">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="ffc7b-118">Instrukcje: Konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="ffc7b-118">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
