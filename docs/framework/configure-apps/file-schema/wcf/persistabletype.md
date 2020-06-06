---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855071"
---
# \<persistableType>
<span data-ttu-id="e9caf-101">Określa wszystkie typy, które są trwałe.</span><span class="sxs-lookup"><span data-stu-id="e9caf-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="e9caf-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9caf-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="e9caf-103">Typ</span><span class="sxs-lookup"><span data-stu-id="e9caf-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9caf-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e9caf-104">Attributes and Elements</span></span>  
 <span data-ttu-id="e9caf-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e9caf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9caf-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e9caf-106">Attributes</span></span>  
  
|<span data-ttu-id="e9caf-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e9caf-107">Attribute</span></span>|<span data-ttu-id="e9caf-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e9caf-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9caf-109">identyfikator</span><span class="sxs-lookup"><span data-stu-id="e9caf-109">id</span></span>|<span data-ttu-id="e9caf-110">Wymagany atrybut, który zawiera ciąg, który określa unikatowy identyfikator dla typu trwałego.</span><span class="sxs-lookup"><span data-stu-id="e9caf-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="e9caf-111">name</span><span class="sxs-lookup"><span data-stu-id="e9caf-111">name</span></span>|<span data-ttu-id="e9caf-112">Opcjonalny atrybut, który zawiera ciąg określający nazwę typu, który jest trwały.</span><span class="sxs-lookup"><span data-stu-id="e9caf-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9caf-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e9caf-113">Child Elements</span></span>  
 <span data-ttu-id="e9caf-114">Brak</span><span class="sxs-lookup"><span data-stu-id="e9caf-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9caf-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e9caf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e9caf-116">Element</span><span class="sxs-lookup"><span data-stu-id="e9caf-116">Element</span></span>|<span data-ttu-id="e9caf-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e9caf-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="e9caf-118">Kolekcja `persistableType` elementów.</span><span class="sxs-lookup"><span data-stu-id="e9caf-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9caf-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9caf-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="e9caf-120">Integrowanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="e9caf-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="e9caf-121">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="e9caf-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
