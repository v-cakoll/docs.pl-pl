---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855071"
---
# <a name="persistabletype"></a><span data-ttu-id="7f1b3-101">\<persistableType ></span><span class="sxs-lookup"><span data-stu-id="7f1b3-101">\<persistableType></span></span>
<span data-ttu-id="7f1b3-102">Określa wszystkie typy, które są trwałe.</span><span class="sxs-lookup"><span data-stu-id="7f1b3-102">Specifies all the persistable types.</span></span>  
  
<span data-ttu-id="7f1b3-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f1b3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7f1b3-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7f1b3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7f1b3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="7f1b3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="7f1b3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="7f1b3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="7f1b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<persistableTypes >** ](persistabletypes.md)</span><span class="sxs-lookup"><span data-stu-id="7f1b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)</span></span>\
<span data-ttu-id="7f1b3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistableType >**</span><span class="sxs-lookup"><span data-stu-id="7f1b3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1b3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f1b3-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="7f1b3-110">Typ</span><span class="sxs-lookup"><span data-stu-id="7f1b3-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f1b3-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f1b3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7f1b3-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f1b3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f1b3-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f1b3-113">Attributes</span></span>  
  
|<span data-ttu-id="7f1b3-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7f1b3-114">Attribute</span></span>|<span data-ttu-id="7f1b3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7f1b3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f1b3-116">identyfikator</span><span class="sxs-lookup"><span data-stu-id="7f1b3-116">id</span></span>|<span data-ttu-id="7f1b3-117">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator dla typu trwałego.</span><span class="sxs-lookup"><span data-stu-id="7f1b3-117">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="7f1b3-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="7f1b3-118">name</span></span>|<span data-ttu-id="7f1b3-119">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu, który jest trwały.</span><span class="sxs-lookup"><span data-stu-id="7f1b3-119">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f1b3-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f1b3-120">Child Elements</span></span>  
 <span data-ttu-id="7f1b3-121">Brak</span><span class="sxs-lookup"><span data-stu-id="7f1b3-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f1b3-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f1b3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7f1b3-123">Element</span><span class="sxs-lookup"><span data-stu-id="7f1b3-123">Element</span></span>|<span data-ttu-id="7f1b3-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7f1b3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f1b3-125">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="7f1b3-125">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="7f1b3-126">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="7f1b3-126">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f1b3-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f1b3-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="7f1b3-128">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="7f1b3-128">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="7f1b3-129">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="7f1b3-129">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="7f1b3-130">Instrukcje: Konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="7f1b3-130">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
