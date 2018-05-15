---
title: '&lt;routing&gt; w &lt;serviceBehavior&gt;'
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 5fb7febe365f73acf09ba74b07215fe9cc659efb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a><span data-ttu-id="39bd4-102">&lt;routing&gt; w &lt;serviceBehavior&gt;</span><span class="sxs-lookup"><span data-stu-id="39bd4-102">&lt;routing&gt; of &lt;serviceBehavior&gt;</span></span>
<span data-ttu-id="39bd4-103">Udostępnia środowiska wykonawczego usługa routingu umożliwia dynamiczne modyfikacji konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="39bd4-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="39bd4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39bd4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39bd4-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="39bd4-105">\<behaviors></span></span>  
<span data-ttu-id="39bd4-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="39bd4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="39bd4-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="39bd4-107">\<behavior></span></span>  
<span data-ttu-id="39bd4-108">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="39bd4-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39bd4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="39bd4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39bd4-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39bd4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39bd4-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39bd4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39bd4-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39bd4-112">Attributes</span></span>  
  
|<span data-ttu-id="39bd4-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39bd4-113">Attribute</span></span>|<span data-ttu-id="39bd4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="39bd4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39bd4-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="39bd4-115">filterTable</span></span>|<span data-ttu-id="39bd4-116">Ciąg określający nazwę tabeli routingu, która zawiera filtry, które ma zostać obliczone przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="39bd4-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="39bd4-117">Ta wartość musi być zgodna `name` atrybutu [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="39bd4-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="39bd4-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="39bd4-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="39bd4-119">Wartość logiczna określająca, czy filtr zbada zarówno treści wiadomości i nagłówek lub tylko nagłówek.</span><span class="sxs-lookup"><span data-stu-id="39bd4-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="39bd4-120">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="39bd4-120">The default is `true`.</span></span>|  
|<span data-ttu-id="39bd4-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="39bd4-121">soapProcessingEnabled</span></span>|<span data-ttu-id="39bd4-122">Wartość logiczna określająca, czy powinien wystąpić przetwarzania protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="39bd4-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39bd4-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39bd4-123">Child Elements</span></span>  
 <span data-ttu-id="39bd4-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="39bd4-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39bd4-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39bd4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="39bd4-126">Element</span><span class="sxs-lookup"><span data-stu-id="39bd4-126">Element</span></span>|<span data-ttu-id="39bd4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="39bd4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39bd4-128">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="39bd4-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="39bd4-129">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="39bd4-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39bd4-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39bd4-130">Remarks</span></span>  
 <span data-ttu-id="39bd4-131">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji umożliwia routingu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="39bd4-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="39bd4-132">Można określić rzeczywistego tabeli routingu do użycia przez usługę w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="39bd4-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="39bd4-133">Za pomocą tej sekcji konfiguracyjnej, można zmienić ustawienia routingu na bieżąco po zmianie deseniu wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="39bd4-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="39bd4-134">W czasie wykonywania można zarejestrować rozszerzenia routingu przy użyciu nowych ustawień routingu i usługi routingu rozpocznie się za pomocą zaktualizowanej konfiguracji informacji dla nowych wiadomości i sesji, pozostawiając locie wiadomości/sesji przy użyciu niezależnie od zasady zostały w miejsce, gdy zostały rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="39bd4-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="39bd4-135">Daje możliwość są bezpieczne dla sesji, bez odtworzenia ponownej konfiguracji usługi routingu podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="39bd4-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
  
