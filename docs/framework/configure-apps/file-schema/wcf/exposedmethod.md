---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 032139b714aa11079c7ee8610c332e404b3981ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918998"
---
# <a name="exposedmethod"></a><span data-ttu-id="4e565-101">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="4e565-101">\<exposedMethod></span></span>
<span data-ttu-id="4e565-102">Reprezentuje metodę COM+, która jest uwidaczniana, gdy interfejs składnika modelu COM+ jest udostępniany jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4e565-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="4e565-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4e565-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4e565-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="4e565-104">\<comContracts></span></span>  
<span data-ttu-id="4e565-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="4e565-105">\<comContract></span></span>  
<span data-ttu-id="4e565-106">\<Metody ></span><span class="sxs-lookup"><span data-stu-id="4e565-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e565-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e565-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e565-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e565-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4e565-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e565-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e565-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e565-110">Attributes</span></span>  
  
|<span data-ttu-id="4e565-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4e565-111">Attribute</span></span>|<span data-ttu-id="4e565-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4e565-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e565-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="4e565-113">name</span></span>|<span data-ttu-id="4e565-114">Ciąg, który zawiera metodę COM+, która jest uwidaczniana, gdy interfejs składnika modelu COM+ jest ujawniony jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4e565-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e565-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e565-115">Child Elements</span></span>  
 <span data-ttu-id="4e565-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="4e565-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e565-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e565-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4e565-118">Element</span><span class="sxs-lookup"><span data-stu-id="4e565-118">Element</span></span>|<span data-ttu-id="4e565-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4e565-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e565-120">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="4e565-120">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="4e565-121">Kolekcja elementów exposedMethod >. [ \<](exposedmethod.md)</span><span class="sxs-lookup"><span data-stu-id="4e565-121">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e565-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e565-122">Remarks</span></span>  
 <span data-ttu-id="4e565-123">Narzędzie konfiguracji integracji modelu COM+ (ComSvcConfig. exe) może służyć do dodawania określonych metod z interfejsu COM, które mają być wyświetlane w wygenerowanym kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="4e565-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="4e565-124">Na przykład można użyć poniższego polecenia, aby dodać trzy nazwane metody z `IFinances` interfejsu com `ItemOrders`na. Składnik finansowy do wygenerowanego kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="4e565-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="4e565-125">Po uruchomieniu również programu ComSvcConfig. exe program generuje następujący kontrakt usługi, zawierający wymienione wcześniej metody jako [ \<elementy exposedMethod >](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="4e565-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="4e565-126">W czasie inicjalizacji usługi środowisko uruchomieniowe próbuje wygenerować kontrakt usługi przez odzwierciedlenie i dodanie tylko metod uwzględnionych na liście [ \<elementów exposedMethod >](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="4e565-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="4e565-127">Ślad jest generowany dla każdej metody interfejsu, która nie jest uwzględniona w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="4e565-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e565-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e565-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="4e565-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="4e565-129">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="4e565-130">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="4e565-130">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="4e565-131">Instrukcje: Konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="4e565-131">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
