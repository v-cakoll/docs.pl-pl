---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: b9d61a736a2f8650c543433931d57e156d115018
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706855"
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="71a83-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="71a83-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="71a83-103">Określa typy stałe.</span><span class="sxs-lookup"><span data-stu-id="71a83-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="71a83-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="71a83-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="71a83-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="71a83-105">\<comContracts></span></span>  
<span data-ttu-id="71a83-106">\<comContract></span><span class="sxs-lookup"><span data-stu-id="71a83-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71a83-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="71a83-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="71a83-108">Typ</span><span class="sxs-lookup"><span data-stu-id="71a83-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71a83-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="71a83-109">Attributes and Elements</span></span>  
 <span data-ttu-id="71a83-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="71a83-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71a83-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="71a83-111">Attributes</span></span>  
  
|<span data-ttu-id="71a83-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="71a83-112">Attribute</span></span>|<span data-ttu-id="71a83-113">Opis</span><span class="sxs-lookup"><span data-stu-id="71a83-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71a83-114">identyfikator</span><span class="sxs-lookup"><span data-stu-id="71a83-114">id</span></span>|<span data-ttu-id="71a83-115">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator typu stałe.</span><span class="sxs-lookup"><span data-stu-id="71a83-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="71a83-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="71a83-116">name</span></span>|<span data-ttu-id="71a83-117">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu stałe.</span><span class="sxs-lookup"><span data-stu-id="71a83-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71a83-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="71a83-118">Child Elements</span></span>  
 <span data-ttu-id="71a83-119">Brak</span><span class="sxs-lookup"><span data-stu-id="71a83-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71a83-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="71a83-120">Parent Elements</span></span>  
  
|<span data-ttu-id="71a83-121">Element</span><span class="sxs-lookup"><span data-stu-id="71a83-121">Element</span></span>|<span data-ttu-id="71a83-122">Opis</span><span class="sxs-lookup"><span data-stu-id="71a83-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71a83-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="71a83-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="71a83-124">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="71a83-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71a83-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71a83-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="71a83-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="71a83-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="71a83-127">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="71a83-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="71a83-128">Instrukcje: Konfigurowanie ustawień usługi COM +</span><span class="sxs-lookup"><span data-stu-id="71a83-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
