---
title: '&lt;exposedMethod&gt;'
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 2a26ca90f6a66592c246cc9e5aef50cfa53b4bdd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747385"
---
# <a name="ltexposedmethodgt"></a><span data-ttu-id="28b69-102">&lt;exposedMethod&gt;</span><span class="sxs-lookup"><span data-stu-id="28b69-102">&lt;exposedMethod&gt;</span></span>
<span data-ttu-id="28b69-103">Reprezentuje metodę COM +, która jest widoczna gdy interfejs składnika COM + jest udostępniany jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="28b69-103">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="28b69-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28b69-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28b69-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="28b69-105">\<comContracts></span></span>  
<span data-ttu-id="28b69-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="28b69-106">\<comContract></span></span>  
<span data-ttu-id="28b69-107">\<metody ></span><span class="sxs-lookup"><span data-stu-id="28b69-107">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b69-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="28b69-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28b69-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28b69-109">Attributes and Elements</span></span>  
 <span data-ttu-id="28b69-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28b69-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28b69-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28b69-111">Attributes</span></span>  
  
|<span data-ttu-id="28b69-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28b69-112">Attribute</span></span>|<span data-ttu-id="28b69-113">Opis</span><span class="sxs-lookup"><span data-stu-id="28b69-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28b69-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="28b69-114">name</span></span>|<span data-ttu-id="28b69-115">Ciąg, który zawiera metodę COM +, która jest widoczna gdy interfejs składnika COM + jest udostępniany jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="28b69-115">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28b69-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28b69-116">Child Elements</span></span>  
 <span data-ttu-id="28b69-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="28b69-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28b69-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28b69-118">Parent Elements</span></span>  
  
|<span data-ttu-id="28b69-119">Element</span><span class="sxs-lookup"><span data-stu-id="28b69-119">Element</span></span>|<span data-ttu-id="28b69-120">Opis</span><span class="sxs-lookup"><span data-stu-id="28b69-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28b69-121">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="28b69-121">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="28b69-122">Kolekcja [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="28b69-122">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28b69-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28b69-123">Remarks</span></span>  
 <span data-ttu-id="28b69-124">COM + integration narzędzia do konfiguracji (ComSvcConfig.exe) można dodać konkretnych metod z interfejsem COM na kontrakt usługi wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="28b69-124">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="28b69-125">Na przykład służy następujące polecenie do dodania trzy metody o nazwie z `IFinances` interfejsu COM na `ItemOrders`. Składnik finansowych wygenerowanego serwisowej.</span><span class="sxs-lookup"><span data-stu-id="28b69-125">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="28b69-126">Po uruchomieniu również ComSvcConfig.exe, następnie generuje następujące kontraktu usługi wyświetlania opisanych powyżej metod jako [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="28b69-126">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 <span data-ttu-id="28b69-127">Podczas inicjowania usługi środowiska wykonawczego prób wygenerowania kontrakt usługi odzwierciedlające za pośrednictwem i Dodawanie metody uwzględnione na liście [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="28b69-127">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="28b69-128">Śledzenie jest tworzony dla każdej metody interfejsu, który nie znajduje się na kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="28b69-128">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b69-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28b69-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [<span data-ttu-id="28b69-130">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="28b69-130">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="28b69-131">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="28b69-131">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="28b69-132">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="28b69-132">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
