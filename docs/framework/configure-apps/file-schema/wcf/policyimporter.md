---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855062"
---
# \<policyImporter>
<span data-ttu-id="0f360-101">Określa importera zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="0f360-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="0f360-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f360-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f360-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0f360-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0f360-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0f360-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f360-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0f360-105">Attributes</span></span>  
  
|<span data-ttu-id="0f360-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0f360-106">Attribute</span></span>|<span data-ttu-id="0f360-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0f360-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0f360-108">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="0f360-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f360-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0f360-109">Child Elements</span></span>  
 <span data-ttu-id="0f360-110">Brak</span><span class="sxs-lookup"><span data-stu-id="0f360-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f360-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0f360-111">Parent Elements</span></span>  
  
|<span data-ttu-id="0f360-112">Element</span><span class="sxs-lookup"><span data-stu-id="0f360-112">Element</span></span>|<span data-ttu-id="0f360-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0f360-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="0f360-114">Określa wszystkich importerów zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="0f360-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f360-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f360-115">Remarks</span></span>  
 <span data-ttu-id="0f360-116">Importer zasad jest używany do wyszukiwania potwierdzeń niestandardowych zasad dotyczących funkcji powiązania, a także do dołączania niestandardowego elementu powiązania, który implementuje funkcje wymagane przez potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="0f360-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f360-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f360-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="0f360-118">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="0f360-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="0f360-119">Klienci</span><span class="sxs-lookup"><span data-stu-id="0f360-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
