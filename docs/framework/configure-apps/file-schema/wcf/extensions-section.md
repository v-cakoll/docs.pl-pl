---
title: <extensions>Paragraf
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855353"
---
# <a name="extensions-section"></a><span data-ttu-id="8ff9c-102">\<sekcja > rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="8ff9c-102">\<extensions> section</span></span>
<span data-ttu-id="8ff9c-103">Ta sekcja konfiguracji zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika, zachowań i innych aspektów rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="8ff9c-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="8ff9c-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8ff9c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8ff9c-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8ff9c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8ff9c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> rozszerzeń**</span><span class="sxs-lookup"><span data-stu-id="8ff9c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff9c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ff9c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ff9c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8ff9c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8ff9c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8ff9c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ff9c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8ff9c-110">Attributes</span></span>  
 <span data-ttu-id="8ff9c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="8ff9c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ff9c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8ff9c-112">Child Elements</span></span>  
  
|<span data-ttu-id="8ff9c-113">Element</span><span class="sxs-lookup"><span data-stu-id="8ff9c-113">Element</span></span>|<span data-ttu-id="8ff9c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8ff9c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ff9c-115">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="8ff9c-115">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="8ff9c-116">Ta sekcja zawiera elementy podrzędne, które określają rozszerzenia zachowań, które umożliwiają użytkownikowi dostosowanie zachowań usługi lub punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8ff9c-116">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="8ff9c-117">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="8ff9c-117">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="8ff9c-118">Ta sekcja umożliwia korzystanie z niestandardowego elementu powiązania z pliku konfiguracji komputera lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ff9c-118">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="8ff9c-119">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="8ff9c-119">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="8ff9c-120">Ta sekcja zawiera elementy podrzędne, które określają rozszerzenia powiązań, które umożliwiają użytkownikowi dostosowanie powiązań.</span><span class="sxs-lookup"><span data-stu-id="8ff9c-120">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="8ff9c-121">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="8ff9c-121">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="8ff9c-122">Ta sekcja zawiera elementy podrzędne, które rejestrują standardowe punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="8ff9c-122">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ff9c-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8ff9c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8ff9c-124">Element</span><span class="sxs-lookup"><span data-stu-id="8ff9c-124">Element</span></span>|<span data-ttu-id="8ff9c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8ff9c-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ff9c-126">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8ff9c-126">system.ServiceModel</span></span>|<span data-ttu-id="8ff9c-127">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="8ff9c-127">The root element of all WCF configuration elements.</span></span>|
