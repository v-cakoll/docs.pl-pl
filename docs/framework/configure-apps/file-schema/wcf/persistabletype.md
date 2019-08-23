---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: fcfd338e289b5151688724f0e84b6878707d32be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933834"
---
# <a name="persistabletype"></a><span data-ttu-id="7f261-101">\<persistableType ></span><span class="sxs-lookup"><span data-stu-id="7f261-101">\<persistableType></span></span>
<span data-ttu-id="7f261-102">Określa wszystkie typy, które są trwałe.</span><span class="sxs-lookup"><span data-stu-id="7f261-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="7f261-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7f261-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f261-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="7f261-104">\<comContracts></span></span>  
<span data-ttu-id="7f261-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="7f261-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f261-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f261-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="7f261-107">Typ</span><span class="sxs-lookup"><span data-stu-id="7f261-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f261-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f261-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7f261-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f261-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f261-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f261-110">Attributes</span></span>  
  
|<span data-ttu-id="7f261-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7f261-111">Attribute</span></span>|<span data-ttu-id="7f261-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7f261-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f261-113">identyfikator</span><span class="sxs-lookup"><span data-stu-id="7f261-113">id</span></span>|<span data-ttu-id="7f261-114">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator dla typu trwałego.</span><span class="sxs-lookup"><span data-stu-id="7f261-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="7f261-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="7f261-115">name</span></span>|<span data-ttu-id="7f261-116">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu, który jest trwały.</span><span class="sxs-lookup"><span data-stu-id="7f261-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f261-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f261-117">Child Elements</span></span>  
 <span data-ttu-id="7f261-118">Brak</span><span class="sxs-lookup"><span data-stu-id="7f261-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f261-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f261-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7f261-120">Element</span><span class="sxs-lookup"><span data-stu-id="7f261-120">Element</span></span>|<span data-ttu-id="7f261-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7f261-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f261-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="7f261-122">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="7f261-123">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="7f261-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f261-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f261-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="7f261-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="7f261-125">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="7f261-126">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="7f261-126">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="7f261-127">Instrukcje: Konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="7f261-127">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
