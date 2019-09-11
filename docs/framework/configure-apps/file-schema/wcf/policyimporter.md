---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855062"
---
# <a name="policyimporter"></a><span data-ttu-id="747e1-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="747e1-101">\<policyImporter></span></span>
<span data-ttu-id="747e1-102">Określa importera zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="747e1-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
<span data-ttu-id="747e1-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="747e1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="747e1-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="747e1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="747e1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="747e1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="747e1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> metadanych**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="747e1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="747e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<policyImporters >** ](policyimporters.md)</span><span class="sxs-lookup"><span data-stu-id="747e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)</span></span>  
<span data-ttu-id="747e1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<policyImporter >**</span><span class="sxs-lookup"><span data-stu-id="747e1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="747e1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="747e1-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="747e1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="747e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="747e1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="747e1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="747e1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="747e1-112">Attributes</span></span>  
  
|<span data-ttu-id="747e1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="747e1-113">Attribute</span></span>|<span data-ttu-id="747e1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="747e1-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="747e1-115">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="747e1-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="747e1-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="747e1-116">Child Elements</span></span>  
 <span data-ttu-id="747e1-117">Brak</span><span class="sxs-lookup"><span data-stu-id="747e1-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="747e1-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="747e1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="747e1-119">Element</span><span class="sxs-lookup"><span data-stu-id="747e1-119">Element</span></span>|<span data-ttu-id="747e1-120">Opis</span><span class="sxs-lookup"><span data-stu-id="747e1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="747e1-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="747e1-121">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="747e1-122">Określa wszystkich importerów zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="747e1-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="747e1-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="747e1-123">Remarks</span></span>  
 <span data-ttu-id="747e1-124">Importer zasad jest używany do wyszukiwania potwierdzeń niestandardowych zasad dotyczących funkcji powiązania, a także do dołączania niestandardowego elementu powiązania, który implementuje funkcje wymagane przez potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="747e1-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="747e1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="747e1-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="747e1-126">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="747e1-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="747e1-127">Klienci</span><span class="sxs-lookup"><span data-stu-id="747e1-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
