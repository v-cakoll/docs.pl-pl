---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 92c59b3804e22c62340acccc1e12e594203c8e8b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145422"
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="37982-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="37982-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="37982-103">Określa typy stałe.</span><span class="sxs-lookup"><span data-stu-id="37982-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="37982-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="37982-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="37982-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="37982-105">\<comContracts></span></span>  
<span data-ttu-id="37982-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="37982-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37982-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="37982-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="37982-108">Typ</span><span class="sxs-lookup"><span data-stu-id="37982-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37982-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37982-109">Attributes and Elements</span></span>  
 <span data-ttu-id="37982-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37982-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37982-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37982-111">Attributes</span></span>  
  
|<span data-ttu-id="37982-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37982-112">Attribute</span></span>|<span data-ttu-id="37982-113">Opis</span><span class="sxs-lookup"><span data-stu-id="37982-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37982-114">identyfikator</span><span class="sxs-lookup"><span data-stu-id="37982-114">id</span></span>|<span data-ttu-id="37982-115">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator typu stałe.</span><span class="sxs-lookup"><span data-stu-id="37982-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="37982-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="37982-116">name</span></span>|<span data-ttu-id="37982-117">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu stałe.</span><span class="sxs-lookup"><span data-stu-id="37982-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37982-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37982-118">Child Elements</span></span>  
 <span data-ttu-id="37982-119">Brak</span><span class="sxs-lookup"><span data-stu-id="37982-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37982-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37982-120">Parent Elements</span></span>  
  
|<span data-ttu-id="37982-121">Element</span><span class="sxs-lookup"><span data-stu-id="37982-121">Element</span></span>|<span data-ttu-id="37982-122">Opis</span><span class="sxs-lookup"><span data-stu-id="37982-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37982-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="37982-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="37982-124">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="37982-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37982-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37982-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="37982-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="37982-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="37982-127">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="37982-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="37982-128">Instrukcje: Konfigurowanie ustawień usługi COM +</span><span class="sxs-lookup"><span data-stu-id="37982-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
