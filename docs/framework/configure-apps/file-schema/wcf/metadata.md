---
title: '&lt;metadata&gt;'
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 7e314ae56ed7a1b532bb8946fbb28802e72d3e20
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747856"
---
# <a name="ltmetadatagt"></a><span data-ttu-id="9eca9-102">&lt;metadata&gt;</span><span class="sxs-lookup"><span data-stu-id="9eca9-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="9eca9-103">Określa, jak metadanych usługi mogą być przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="9eca9-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="9eca9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9eca9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9eca9-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="9eca9-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eca9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9eca9-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
                 <wsdlImporters>  
                      <wsdlImporter type="string" />  
                 </wsdlImporters>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eca9-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9eca9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9eca9-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9eca9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eca9-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9eca9-109">Attributes</span></span>  
 <span data-ttu-id="9eca9-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="9eca9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9eca9-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9eca9-111">Child Elements</span></span>  
  
|<span data-ttu-id="9eca9-112">Element</span><span class="sxs-lookup"><span data-stu-id="9eca9-112">Element</span></span>|<span data-ttu-id="9eca9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9eca9-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9eca9-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="9eca9-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="9eca9-115">Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="9eca9-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="9eca9-116">Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązanie funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, które wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="9eca9-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="9eca9-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="9eca9-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="9eca9-118">Określa wszystkich importerów WSDL, które importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="9eca9-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="9eca9-119">WSDL importer umożliwia importowanie metadanych, jak również przekonwertować tych informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="9eca9-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="9eca9-120">Selektywnie importowaniem informacji kontraktu i punktu końcowego i właściwości, które ujawnia błędy importu i zaakceptuj typu informacje istotne dla procesu importowania i konwersji.</span><span class="sxs-lookup"><span data-stu-id="9eca9-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="9eca9-121">Obsługuje ona również importowania informacji o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumentów WSDL, rozszerzenia WSDL i dokumentach schematów XML.</span><span class="sxs-lookup"><span data-stu-id="9eca9-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9eca9-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9eca9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9eca9-123">Element</span><span class="sxs-lookup"><span data-stu-id="9eca9-123">Element</span></span>|<span data-ttu-id="9eca9-124">Opis</span><span class="sxs-lookup"><span data-stu-id="9eca9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9eca9-125">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="9eca9-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="9eca9-126">W sekcji klienta definiuje listę punktów końcowych, które klient może połączyć się.</span><span class="sxs-lookup"><span data-stu-id="9eca9-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9eca9-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9eca9-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="9eca9-128">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="9eca9-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="9eca9-129">Klienci</span><span class="sxs-lookup"><span data-stu-id="9eca9-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
