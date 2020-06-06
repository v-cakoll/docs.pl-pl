---
title: <extensions>Paragraf
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855353"
---
# <a name="extensions-section"></a><span data-ttu-id="c27db-102">\<extensions>Paragraf</span><span class="sxs-lookup"><span data-stu-id="c27db-102">\<extensions> section</span></span>
<span data-ttu-id="c27db-103">Ta sekcja konfiguracji zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika, zachowań i innych aspektów rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="c27db-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="c27db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c27db-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c27db-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c27db-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c27db-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c27db-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c27db-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c27db-107">Attributes</span></span>  
 <span data-ttu-id="c27db-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="c27db-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c27db-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c27db-109">Child Elements</span></span>  
  
|<span data-ttu-id="c27db-110">Element</span><span class="sxs-lookup"><span data-stu-id="c27db-110">Element</span></span>|<span data-ttu-id="c27db-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c27db-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="c27db-112">Ta sekcja zawiera elementy podrzędne, które określają rozszerzenia zachowań, które umożliwiają użytkownikowi dostosowanie zachowań usługi lub punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c27db-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="c27db-113">Ta sekcja umożliwia korzystanie z niestandardowego elementu powiązania z pliku konfiguracji komputera lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c27db-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="c27db-114">Ta sekcja zawiera elementy podrzędne, które określają rozszerzenia powiązań, które umożliwiają użytkownikowi dostosowanie powiązań.</span><span class="sxs-lookup"><span data-stu-id="c27db-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="c27db-115">Ta sekcja zawiera elementy podrzędne, które rejestrują standardowe punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="c27db-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c27db-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c27db-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c27db-117">Element</span><span class="sxs-lookup"><span data-stu-id="c27db-117">Element</span></span>|<span data-ttu-id="c27db-118">Opis</span><span class="sxs-lookup"><span data-stu-id="c27db-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c27db-119">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c27db-119">system.ServiceModel</span></span>|<span data-ttu-id="c27db-120">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="c27db-120">The root element of all WCF configuration elements.</span></span>|
