---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 91eafa46aa73b5e6d359fcbe48f098f9f8a4d0f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174515"
---
# <a name="exposedmethod"></a><span data-ttu-id="3faed-101">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="3faed-101">\<exposedMethod></span></span>
<span data-ttu-id="3faed-102">Reprezentuje metodę COM +, która jest widoczna gdy interfejs składnika COM + jest widoczny jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3faed-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="3faed-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3faed-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3faed-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="3faed-104">\<comContracts></span></span>  
<span data-ttu-id="3faed-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="3faed-105">\<comContract></span></span>  
<span data-ttu-id="3faed-106">\<metody ></span><span class="sxs-lookup"><span data-stu-id="3faed-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3faed-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3faed-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3faed-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3faed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3faed-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3faed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3faed-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3faed-110">Attributes</span></span>  
  
|<span data-ttu-id="3faed-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3faed-111">Attribute</span></span>|<span data-ttu-id="3faed-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3faed-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3faed-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="3faed-113">name</span></span>|<span data-ttu-id="3faed-114">Ciąg, który zawiera metodę COM +, która jest widoczna gdy interfejs składnika COM + jest widoczny jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3faed-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3faed-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3faed-115">Child Elements</span></span>  
 <span data-ttu-id="3faed-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="3faed-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3faed-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3faed-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3faed-118">Element</span><span class="sxs-lookup"><span data-stu-id="3faed-118">Element</span></span>|<span data-ttu-id="3faed-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3faed-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3faed-120">\<exposedMethods></span><span class="sxs-lookup"><span data-stu-id="3faed-120">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="3faed-121">Kolekcja [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="3faed-121">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3faed-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3faed-122">Remarks</span></span>  
 <span data-ttu-id="3faed-123">COM + integracja narzędzie konfiguracji (ComSvcConfig.exe) może służyć do dodawania konkretnych metod z interfejsem COM żeby pojawiły się na kontrakt usługi wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="3faed-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="3faed-124">Na przykład służy następujące polecenie do dodania trzy metody o nazwie z `IFinances` interfejsu COM na `ItemOrders`. Składnik finansowych umową serwisową wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="3faed-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="3faed-125">Po uruchomieniu również ComSvcConfig.exe, następnie generuje następujące kontraktu usługi, wyświetlanie listy opisanych powyżej metod jako [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="3faed-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="3faed-126">Podczas inicjowania usługi, środowisko uruchomieniowe spróbuje go wygenerować kontraktu usługi odzwierciedlający za pośrednictwem i dodając tylko te metody, które są uwzględnione na liście [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="3faed-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="3faed-127">Śledzenie jest tworzony dla każdej metody interfejsu, który nie znajduje się na kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="3faed-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3faed-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3faed-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="3faed-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="3faed-129">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="3faed-130">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="3faed-130">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="3faed-131">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="3faed-131">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
