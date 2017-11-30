---
title: "&lt;extensions&gt; — sekcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a564b85609ca289f382789844d4e78252bb66482
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="e44ca-102">&lt;extensions&gt; — sekcja</span><span class="sxs-lookup"><span data-stu-id="e44ca-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="e44ca-103">Ta sekcja konfiguracji zawiera Kolekcja rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="e44ca-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="e44ca-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e44ca-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44ca-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e44ca-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e44ca-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e44ca-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e44ca-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e44ca-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e44ca-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e44ca-108">Attributes</span></span>  
 <span data-ttu-id="e44ca-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="e44ca-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e44ca-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e44ca-110">Child Elements</span></span>  
  
|<span data-ttu-id="e44ca-111">Element</span><span class="sxs-lookup"><span data-stu-id="e44ca-111">Element</span></span>|<span data-ttu-id="e44ca-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e44ca-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e44ca-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="e44ca-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="e44ca-114">Ta sekcja zawiera elementy podrzędne, które określają zachowanie rozszerzeń, które umożliwiają użytkownikowi dostosowywanie zachowania usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e44ca-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="e44ca-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="e44ca-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="e44ca-116">Ta sekcja umożliwia zastosowanie elementu niestandardowego powiązania z maszyny lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e44ca-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="e44ca-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="e44ca-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="e44ca-118">Ta sekcja zawiera elementy podrzędne, które Określ rozszerzenia powiązania, które umożliwiają użytkownikowi dostosowywanie powiązania.</span><span class="sxs-lookup"><span data-stu-id="e44ca-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="e44ca-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="e44ca-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="e44ca-120">Ta sekcja zawiera elementy podrzędne, które rejestruje standardowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="e44ca-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e44ca-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e44ca-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e44ca-122">Element</span><span class="sxs-lookup"><span data-stu-id="e44ca-122">Element</span></span>|<span data-ttu-id="e44ca-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e44ca-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e44ca-124">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e44ca-124">system.ServiceModel</span></span>|<span data-ttu-id="e44ca-125">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e44ca-125">The root element of all WCF configuration elements.</span></span>|
