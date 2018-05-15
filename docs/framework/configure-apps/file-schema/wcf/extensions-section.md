---
title: '&lt;extensions&gt; — sekcja'
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 09cabfc6c03602c3b6de343a29b5b25755f2cf0f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="3f7d6-102">&lt;extensions&gt; — sekcja</span><span class="sxs-lookup"><span data-stu-id="3f7d6-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="3f7d6-103">Ta sekcja konfiguracji zawiera Kolekcja rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="3f7d6-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="3f7d6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3f7d6-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7d6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f7d6-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <extensions>  
    <bindingExtensions>  
    </bindingExtensions>  
    <behaviorExtensions>  
    </behaviorExtensions>  
    <bindingElementExtensions>  
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f7d6-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3f7d6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3f7d6-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f7d6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f7d6-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f7d6-108">Attributes</span></span>  
 <span data-ttu-id="3f7d6-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="3f7d6-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f7d6-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3f7d6-110">Child Elements</span></span>  
  
|<span data-ttu-id="3f7d6-111">Element</span><span class="sxs-lookup"><span data-stu-id="3f7d6-111">Element</span></span>|<span data-ttu-id="3f7d6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3f7d6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f7d6-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="3f7d6-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="3f7d6-114">Ta sekcja zawiera elementy podrzędne, które określają zachowanie rozszerzeń, które umożliwiają użytkownikowi dostosowywanie zachowania usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3f7d6-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="3f7d6-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="3f7d6-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="3f7d6-116">Ta sekcja umożliwia zastosowanie elementu niestandardowego powiązania z maszyny lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f7d6-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="3f7d6-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="3f7d6-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="3f7d6-118">Ta sekcja zawiera elementy podrzędne, które Określ rozszerzenia powiązania, które umożliwiają użytkownikowi dostosowywanie powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f7d6-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="3f7d6-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="3f7d6-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="3f7d6-120">Ta sekcja zawiera elementy podrzędne, które rejestruje standardowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="3f7d6-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f7d6-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3f7d6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3f7d6-122">Element</span><span class="sxs-lookup"><span data-stu-id="3f7d6-122">Element</span></span>|<span data-ttu-id="3f7d6-123">Opis</span><span class="sxs-lookup"><span data-stu-id="3f7d6-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f7d6-124">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3f7d6-124">system.ServiceModel</span></span>|<span data-ttu-id="3f7d6-125">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3f7d6-125">The root element of all WCF configuration elements.</span></span>|
