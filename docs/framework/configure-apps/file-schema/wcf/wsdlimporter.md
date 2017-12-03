---
title: '&lt;Element wsdlImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f4fe6c82d0a6f53dfa05a82622e0412280212cc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="27261-102">&lt;Element wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="27261-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="27261-103">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="27261-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="27261-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="27261-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="27261-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="27261-105">\<client></span></span>  
<span data-ttu-id="27261-106">\<metadane ></span><span class="sxs-lookup"><span data-stu-id="27261-106">\<metadata></span></span>  
<span data-ttu-id="27261-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="27261-107">\<wsdlImporters></span></span>  
<span data-ttu-id="27261-108">\<Element wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="27261-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27261-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="27261-109">Syntax</span></span>  
  
```xml  
<metadata>  
  <wsdlImporters>  
    <wsdlImporter type="string" />  
  </wsdlImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27261-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="27261-110">Attributes and Elements</span></span>  
 <span data-ttu-id="27261-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="27261-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27261-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="27261-112">Attributes</span></span>  
  
|<span data-ttu-id="27261-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="27261-113">Attribute</span></span>|<span data-ttu-id="27261-114">Opis</span><span class="sxs-lookup"><span data-stu-id="27261-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="27261-115">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="27261-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27261-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="27261-116">Child Elements</span></span>  
 <span data-ttu-id="27261-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="27261-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27261-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="27261-118">Parent Elements</span></span>  
  
|<span data-ttu-id="27261-119">Element</span><span class="sxs-lookup"><span data-stu-id="27261-119">Element</span></span>|<span data-ttu-id="27261-120">Opis</span><span class="sxs-lookup"><span data-stu-id="27261-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27261-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="27261-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="27261-122">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="27261-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27261-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27261-123">Remarks</span></span>  
 <span data-ttu-id="27261-124">WSDL importer umożliwia importowanie metadanych, jak również przekonwertować tych informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="27261-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="27261-125">Selektywnie importowaniem informacji kontraktu i punktu końcowego i właściwości, które ujawnia błędy importu i zaakceptuj typu informacje istotne dla procesu importowania i konwersji.</span><span class="sxs-lookup"><span data-stu-id="27261-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="27261-126">Obsługuje ona również importowania informacji o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumentów WSDL, rozszerzenia WSDL i dokumentach schematów XML.</span><span class="sxs-lookup"><span data-stu-id="27261-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27261-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27261-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="27261-128">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="27261-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="27261-129">Klienci</span><span class="sxs-lookup"><span data-stu-id="27261-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
