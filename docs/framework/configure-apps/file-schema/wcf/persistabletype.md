---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 3ea99d360ceb1e3fe6e97cbf9c8827dd7c853f63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256527"
---
# <a name="persistabletype"></a><span data-ttu-id="045a6-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="045a6-101">\<persistableType></span></span>
<span data-ttu-id="045a6-102">Określa typy stałe.</span><span class="sxs-lookup"><span data-stu-id="045a6-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="045a6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="045a6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="045a6-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="045a6-104">\<comContracts></span></span>  
<span data-ttu-id="045a6-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="045a6-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045a6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="045a6-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="045a6-107">Typ</span><span class="sxs-lookup"><span data-stu-id="045a6-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="045a6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="045a6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="045a6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="045a6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="045a6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="045a6-110">Attributes</span></span>  
  
|<span data-ttu-id="045a6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="045a6-111">Attribute</span></span>|<span data-ttu-id="045a6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="045a6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="045a6-113">identyfikator</span><span class="sxs-lookup"><span data-stu-id="045a6-113">id</span></span>|<span data-ttu-id="045a6-114">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator typu stałe.</span><span class="sxs-lookup"><span data-stu-id="045a6-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="045a6-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="045a6-115">name</span></span>|<span data-ttu-id="045a6-116">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu stałe.</span><span class="sxs-lookup"><span data-stu-id="045a6-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="045a6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="045a6-117">Child Elements</span></span>  
 <span data-ttu-id="045a6-118">Brak</span><span class="sxs-lookup"><span data-stu-id="045a6-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="045a6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="045a6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="045a6-120">Element</span><span class="sxs-lookup"><span data-stu-id="045a6-120">Element</span></span>|<span data-ttu-id="045a6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="045a6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="045a6-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="045a6-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="045a6-123">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="045a6-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="045a6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="045a6-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="045a6-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="045a6-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="045a6-126">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="045a6-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="045a6-127">Instrukcje: Konfigurowanie ustawień usługi COM +</span><span class="sxs-lookup"><span data-stu-id="045a6-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
