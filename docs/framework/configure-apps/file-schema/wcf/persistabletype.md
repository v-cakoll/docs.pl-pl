---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 939a29e90ee21e94ccb78842d6f7224e9a6288d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083741"
---
# <a name="persistabletype"></a><span data-ttu-id="4d33b-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="4d33b-101">\<persistableType></span></span>
<span data-ttu-id="4d33b-102">Określa typy stałe.</span><span class="sxs-lookup"><span data-stu-id="4d33b-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="4d33b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4d33b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4d33b-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="4d33b-104">\<comContracts></span></span>  
<span data-ttu-id="4d33b-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="4d33b-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d33b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d33b-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="4d33b-107">Typ</span><span class="sxs-lookup"><span data-stu-id="4d33b-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d33b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d33b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4d33b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d33b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d33b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d33b-110">Attributes</span></span>  
  
|<span data-ttu-id="4d33b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4d33b-111">Attribute</span></span>|<span data-ttu-id="4d33b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4d33b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d33b-113">identyfikator</span><span class="sxs-lookup"><span data-stu-id="4d33b-113">id</span></span>|<span data-ttu-id="4d33b-114">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator typu stałe.</span><span class="sxs-lookup"><span data-stu-id="4d33b-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="4d33b-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="4d33b-115">name</span></span>|<span data-ttu-id="4d33b-116">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu stałe.</span><span class="sxs-lookup"><span data-stu-id="4d33b-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d33b-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d33b-117">Child Elements</span></span>  
 <span data-ttu-id="4d33b-118">Brak</span><span class="sxs-lookup"><span data-stu-id="4d33b-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d33b-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d33b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4d33b-120">Element</span><span class="sxs-lookup"><span data-stu-id="4d33b-120">Element</span></span>|<span data-ttu-id="4d33b-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4d33b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d33b-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="4d33b-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="4d33b-123">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="4d33b-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d33b-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d33b-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="4d33b-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="4d33b-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="4d33b-126">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="4d33b-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="4d33b-127">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="4d33b-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
