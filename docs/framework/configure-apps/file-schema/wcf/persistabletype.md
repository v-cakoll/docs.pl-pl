---
title: '&lt;persistableType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3064727eeda30c05f38558f4f0977c71e5abb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="1fda1-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="1fda1-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="1fda1-103">Określa typy możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="1fda1-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="1fda1-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1fda1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1fda1-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="1fda1-105">\<comContracts></span></span>  
<span data-ttu-id="1fda1-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="1fda1-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fda1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fda1-107">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a><span data-ttu-id="1fda1-108">Typ</span><span class="sxs-lookup"><span data-stu-id="1fda1-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fda1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1fda1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1fda1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1fda1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fda1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1fda1-111">Attributes</span></span>  
  
|<span data-ttu-id="1fda1-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1fda1-112">Attribute</span></span>|<span data-ttu-id="1fda1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1fda1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1fda1-114">identyfikator</span><span class="sxs-lookup"><span data-stu-id="1fda1-114">id</span></span>|<span data-ttu-id="1fda1-115">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator otoka typu.</span><span class="sxs-lookup"><span data-stu-id="1fda1-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="1fda1-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="1fda1-116">name</span></span>|<span data-ttu-id="1fda1-117">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="1fda1-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fda1-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1fda1-118">Child Elements</span></span>  
 <span data-ttu-id="1fda1-119">Brak</span><span class="sxs-lookup"><span data-stu-id="1fda1-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1fda1-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1fda1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1fda1-121">Element</span><span class="sxs-lookup"><span data-stu-id="1fda1-121">Element</span></span>|<span data-ttu-id="1fda1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1fda1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fda1-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="1fda1-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="1fda1-124">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="1fda1-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fda1-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fda1-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="1fda1-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="1fda1-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="1fda1-127">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="1fda1-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="1fda1-128">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="1fda1-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
