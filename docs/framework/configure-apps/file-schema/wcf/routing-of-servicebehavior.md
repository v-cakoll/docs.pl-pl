---
title: <routing> dla <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: b7a9be18395ef8878900d754b5aa5afdeee0cff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783061"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="b8b39-102">\<Routing > z \<serviceBehavior ></span><span class="sxs-lookup"><span data-stu-id="b8b39-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="b8b39-103">Udostępnia wykonawczej usługa routingu umożliwia dynamiczne modyfikowanie konfiguracji routingu.</span><span class="sxs-lookup"><span data-stu-id="b8b39-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="b8b39-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8b39-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8b39-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b8b39-105">\<behaviors></span></span>  
<span data-ttu-id="b8b39-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b8b39-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b8b39-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b8b39-107">\<behavior></span></span>  
<span data-ttu-id="b8b39-108">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="b8b39-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b39-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8b39-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8b39-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b8b39-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b8b39-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b8b39-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8b39-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b8b39-112">Attributes</span></span>  
  
|<span data-ttu-id="b8b39-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b8b39-113">Attribute</span></span>|<span data-ttu-id="b8b39-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b8b39-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8b39-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="b8b39-115">filterTable</span></span>|<span data-ttu-id="b8b39-116">Ciąg określający nazwę tabeli routingu, który zawiera filtry, które mogło zostać ocenione przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="b8b39-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="b8b39-117">Ta wartość musi odpowiadać `name` atrybutu [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="b8b39-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="b8b39-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="b8b39-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="b8b39-119">Wartość logiczna określająca, czy filtr zbada zarówno treści komunikatu i nagłówka lub tylko nagłówek.</span><span class="sxs-lookup"><span data-stu-id="b8b39-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="b8b39-120">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="b8b39-120">The default is `true`.</span></span>|  
|<span data-ttu-id="b8b39-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="b8b39-121">soapProcessingEnabled</span></span>|<span data-ttu-id="b8b39-122">Wartość logiczna określająca, czy powinny być wykonywane przetwarzanie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b8b39-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8b39-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b8b39-123">Child Elements</span></span>  
 <span data-ttu-id="b8b39-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="b8b39-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8b39-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b8b39-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b8b39-126">Element</span><span class="sxs-lookup"><span data-stu-id="b8b39-126">Element</span></span>|<span data-ttu-id="b8b39-127">Opis</span><span class="sxs-lookup"><span data-stu-id="b8b39-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8b39-128">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b8b39-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b8b39-129">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="b8b39-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8b39-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8b39-130">Remarks</span></span>  
 <span data-ttu-id="b8b39-131">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji umożliwia routingu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="b8b39-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="b8b39-132">Możesz określić rzeczywistego tabeli routingu do użycia przez usługę, w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="b8b39-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="b8b39-133">Korzystając z tej sekcji konfiguracji, można zmienić ustawienia routingu na bieżąco po zmianie deseń wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="b8b39-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="b8b39-134">W czasie wykonywania można zarejestrować rozszerzenia routingu z nowymi ustawieniami routingu i usługa routingu rozpocznie się za pomocą informacji zaktualizowanej konfiguracji dla nowych komunikatów i sesje, przy równoczesnym zachowaniu aktywne komunikaty/sesji przy użyciu dowolne reguły były w miejsce, w momencie rozpoczęcia pracy.</span><span class="sxs-lookup"><span data-stu-id="b8b39-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="b8b39-135">Daje możliwość robienia bezpiecznej sesji, odtwarzanie bez ponownej konfiguracji usługi routingu podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b8b39-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
