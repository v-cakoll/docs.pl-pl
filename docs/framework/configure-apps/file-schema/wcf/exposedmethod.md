---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855309"
---
# <a name="exposedmethod"></a><span data-ttu-id="89db9-101">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="89db9-101">\<exposedMethod></span></span>
<span data-ttu-id="89db9-102">Reprezentuje metodę COM+, która jest uwidaczniana, gdy interfejs składnika modelu COM+ jest udostępniany jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="89db9-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
<span data-ttu-id="89db9-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="89db9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="89db9-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="89db9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="89db9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="89db9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="89db9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="89db9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="89db9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<exposedMethods >** ](exposedmethods.md)</span><span class="sxs-lookup"><span data-stu-id="89db9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)</span></span>\
<span data-ttu-id="89db9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<exposedMethod >**</span><span class="sxs-lookup"><span data-stu-id="89db9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89db9-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="89db9-109">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89db9-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="89db9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89db9-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="89db9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89db9-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="89db9-112">Attributes</span></span>  
  
|<span data-ttu-id="89db9-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="89db9-113">Attribute</span></span>|<span data-ttu-id="89db9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="89db9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89db9-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="89db9-115">name</span></span>|<span data-ttu-id="89db9-116">Ciąg, który zawiera metodę COM+, która jest uwidaczniana, gdy interfejs składnika modelu COM+ jest ujawniony jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="89db9-116">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89db9-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="89db9-117">Child Elements</span></span>  
 <span data-ttu-id="89db9-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="89db9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89db9-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="89db9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="89db9-120">Element</span><span class="sxs-lookup"><span data-stu-id="89db9-120">Element</span></span>|<span data-ttu-id="89db9-121">Opis</span><span class="sxs-lookup"><span data-stu-id="89db9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89db9-122">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="89db9-122">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="89db9-123">Kolekcja elementów exposedMethod >. [ \<](exposedmethod.md)</span><span class="sxs-lookup"><span data-stu-id="89db9-123">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89db9-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89db9-124">Remarks</span></span>  
 <span data-ttu-id="89db9-125">Narzędzie konfiguracji integracji modelu COM+ (ComSvcConfig. exe) może służyć do dodawania określonych metod z interfejsu COM, które mają być wyświetlane w wygenerowanym kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="89db9-125">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="89db9-126">Na przykład można użyć poniższego polecenia, aby dodać trzy nazwane metody z `IFinances` interfejsu com `ItemOrders`na. Składnik finansowy do wygenerowanego kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="89db9-126">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="89db9-127">Po uruchomieniu również programu ComSvcConfig. exe program generuje następujący kontrakt usługi, zawierający wymienione wcześniej metody jako [ \<elementy exposedMethod >](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="89db9-127">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="89db9-128">W czasie inicjalizacji usługi środowisko uruchomieniowe próbuje wygenerować kontrakt usługi przez odzwierciedlenie i dodanie tylko metod uwzględnionych na liście [ \<elementów exposedMethod >](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="89db9-128">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="89db9-129">Ślad jest generowany dla każdej metody interfejsu, która nie jest uwzględniona w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="89db9-129">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89db9-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89db9-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="89db9-131">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="89db9-131">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="89db9-132">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="89db9-132">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="89db9-133">Instrukcje: Konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="89db9-133">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
