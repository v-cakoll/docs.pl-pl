---
title: <extensions> Sekcja
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268291"
---
# <a name="extensions-section"></a><span data-ttu-id="83fa7-102">\<Rozszerzenia > sekcji</span><span class="sxs-lookup"><span data-stu-id="83fa7-102">\<extensions> section</span></span>
<span data-ttu-id="83fa7-103">Ta sekcja konfiguracji zawiera Kolekcja rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="83fa7-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="83fa7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="83fa7-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83fa7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="83fa7-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83fa7-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="83fa7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="83fa7-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83fa7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83fa7-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="83fa7-108">Attributes</span></span>  
 <span data-ttu-id="83fa7-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="83fa7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="83fa7-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="83fa7-110">Child Elements</span></span>  
  
|<span data-ttu-id="83fa7-111">Element</span><span class="sxs-lookup"><span data-stu-id="83fa7-111">Element</span></span>|<span data-ttu-id="83fa7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="83fa7-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83fa7-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="83fa7-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="83fa7-114">Ta sekcja zawiera elementy podrzędne, które określają zachowanie rozszerzeń, które umożliwiają użytkownikowi dostosowywanie zachowania usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="83fa7-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="83fa7-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="83fa7-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="83fa7-116">Ta sekcja umożliwia zastosowanie elementu niestandardowego powiązania z maszyny lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83fa7-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="83fa7-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="83fa7-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="83fa7-118">Ta sekcja zawiera elementy podrzędne, określających rozszerzeń powiązania, które umożliwiają użytkownikowi dostosowywanie powiązania.</span><span class="sxs-lookup"><span data-stu-id="83fa7-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="83fa7-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="83fa7-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="83fa7-120">Ta sekcja zawiera elementy podrzędne, które rejestruje standardowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="83fa7-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83fa7-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="83fa7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="83fa7-122">Element</span><span class="sxs-lookup"><span data-stu-id="83fa7-122">Element</span></span>|<span data-ttu-id="83fa7-123">Opis</span><span class="sxs-lookup"><span data-stu-id="83fa7-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83fa7-124">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="83fa7-124">system.ServiceModel</span></span>|<span data-ttu-id="83fa7-125">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="83fa7-125">The root element of all WCF configuration elements.</span></span>|
