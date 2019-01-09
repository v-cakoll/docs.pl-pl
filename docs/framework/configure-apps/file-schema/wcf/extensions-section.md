---
title: '&lt;extensions&gt; — sekcja'
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 92dd3c528290344d9537c51fccf7c13c74c1984a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145318"
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="4c512-102">&lt;extensions&gt; — sekcja</span><span class="sxs-lookup"><span data-stu-id="4c512-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="4c512-103">Ta sekcja konfiguracji zawiera Kolekcja rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="4c512-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="4c512-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4c512-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c512-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c512-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c512-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4c512-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4c512-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4c512-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c512-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4c512-108">Attributes</span></span>  
 <span data-ttu-id="4c512-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="4c512-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4c512-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4c512-110">Child Elements</span></span>  
  
|<span data-ttu-id="4c512-111">Element</span><span class="sxs-lookup"><span data-stu-id="4c512-111">Element</span></span>|<span data-ttu-id="4c512-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4c512-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c512-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="4c512-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="4c512-114">Ta sekcja zawiera elementy podrzędne, które określają zachowanie rozszerzeń, które umożliwiają użytkownikowi dostosowywanie zachowania usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4c512-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="4c512-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="4c512-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="4c512-116">Ta sekcja umożliwia zastosowanie elementu niestandardowego powiązania z maszyny lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4c512-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="4c512-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="4c512-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="4c512-118">Ta sekcja zawiera elementy podrzędne, określających rozszerzeń powiązania, które umożliwiają użytkownikowi dostosowywanie powiązania.</span><span class="sxs-lookup"><span data-stu-id="4c512-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="4c512-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="4c512-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="4c512-120">Ta sekcja zawiera elementy podrzędne, które rejestruje standardowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4c512-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c512-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4c512-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4c512-122">Element</span><span class="sxs-lookup"><span data-stu-id="4c512-122">Element</span></span>|<span data-ttu-id="4c512-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4c512-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c512-124">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4c512-124">system.ServiceModel</span></span>|<span data-ttu-id="4c512-125">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="4c512-125">The root element of all WCF configuration elements.</span></span>|
