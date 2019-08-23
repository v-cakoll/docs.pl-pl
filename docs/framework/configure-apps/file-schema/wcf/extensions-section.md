---
title: <extensions>Paragraf
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 4c8b5fe6eef1863ee3f02cb761a3aac61406e446
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918969"
---
# <a name="extensions-section"></a><span data-ttu-id="c90cd-102">\<sekcja > rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="c90cd-102">\<extensions> section</span></span>
<span data-ttu-id="c90cd-103">Ta sekcja konfiguracji zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika, zachowań i innych aspektów rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="c90cd-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="c90cd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c90cd-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c90cd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c90cd-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c90cd-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c90cd-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c90cd-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c90cd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c90cd-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c90cd-108">Attributes</span></span>  
 <span data-ttu-id="c90cd-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="c90cd-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c90cd-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c90cd-110">Child Elements</span></span>  
  
|<span data-ttu-id="c90cd-111">Element</span><span class="sxs-lookup"><span data-stu-id="c90cd-111">Element</span></span>|<span data-ttu-id="c90cd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c90cd-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c90cd-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="c90cd-113">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="c90cd-114">Ta sekcja zawiera elementy podrzędne, które określają rozszerzenia zachowań, które umożliwiają użytkownikowi dostosowanie zachowań usługi lub punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c90cd-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="c90cd-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="c90cd-115">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="c90cd-116">Ta sekcja umożliwia korzystanie z niestandardowego elementu powiązania z pliku konfiguracji komputera lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c90cd-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="c90cd-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="c90cd-117">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="c90cd-118">Ta sekcja zawiera elementy podrzędne, które określają rozszerzenia powiązań, które umożliwiają użytkownikowi dostosowanie powiązań.</span><span class="sxs-lookup"><span data-stu-id="c90cd-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="c90cd-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="c90cd-119">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="c90cd-120">Ta sekcja zawiera elementy podrzędne, które rejestrują standardowe punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="c90cd-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c90cd-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c90cd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c90cd-122">Element</span><span class="sxs-lookup"><span data-stu-id="c90cd-122">Element</span></span>|<span data-ttu-id="c90cd-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c90cd-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c90cd-124">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c90cd-124">system.ServiceModel</span></span>|<span data-ttu-id="c90cd-125">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="c90cd-125">The root element of all WCF configuration elements.</span></span>|
