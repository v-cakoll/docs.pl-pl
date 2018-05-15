---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 23724957398ed1ade2c81a3932e9773d7cf4c642
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="2be1a-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="2be1a-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="2be1a-103">Określa typy możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="2be1a-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="2be1a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2be1a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2be1a-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="2be1a-105">\<comContracts></span></span>  
<span data-ttu-id="2be1a-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="2be1a-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be1a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2be1a-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="2be1a-108">Typ</span><span class="sxs-lookup"><span data-stu-id="2be1a-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2be1a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2be1a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2be1a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2be1a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2be1a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2be1a-111">Attributes</span></span>  
  
|<span data-ttu-id="2be1a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2be1a-112">Attribute</span></span>|<span data-ttu-id="2be1a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2be1a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2be1a-114">identyfikator</span><span class="sxs-lookup"><span data-stu-id="2be1a-114">id</span></span>|<span data-ttu-id="2be1a-115">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator otoka typu.</span><span class="sxs-lookup"><span data-stu-id="2be1a-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="2be1a-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="2be1a-116">name</span></span>|<span data-ttu-id="2be1a-117">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="2be1a-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2be1a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2be1a-118">Child Elements</span></span>  
 <span data-ttu-id="2be1a-119">Brak</span><span class="sxs-lookup"><span data-stu-id="2be1a-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2be1a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2be1a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2be1a-121">Element</span><span class="sxs-lookup"><span data-stu-id="2be1a-121">Element</span></span>|<span data-ttu-id="2be1a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2be1a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2be1a-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="2be1a-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="2be1a-124">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="2be1a-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2be1a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2be1a-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="2be1a-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="2be1a-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="2be1a-127">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="2be1a-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="2be1a-128">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="2be1a-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
