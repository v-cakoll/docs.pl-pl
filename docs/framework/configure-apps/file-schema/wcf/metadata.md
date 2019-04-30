---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: c0c9848d073c799e1f97dd79b375848dfab71e99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763909"
---
# <a name="metadata"></a><span data-ttu-id="4b2e0-101">\<metadata></span><span class="sxs-lookup"><span data-stu-id="4b2e0-101">\<metadata></span></span>
<span data-ttu-id="4b2e0-102">Określa, jak metadane usługi mogą być przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="4b2e0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4b2e0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b2e0-104">\<client></span><span class="sxs-lookup"><span data-stu-id="4b2e0-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b2e0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b2e0-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b2e0-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4b2e0-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4b2e0-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b2e0-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b2e0-108">Attributes</span></span>  
 <span data-ttu-id="4b2e0-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4b2e0-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4b2e0-110">Child Elements</span></span>  
  
|<span data-ttu-id="4b2e0-111">Element</span><span class="sxs-lookup"><span data-stu-id="4b2e0-111">Element</span></span>|<span data-ttu-id="4b2e0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4b2e0-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b2e0-113">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="4b2e0-113">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="4b2e0-114">Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="4b2e0-115">Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązań funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, których wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="4b2e0-116">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="4b2e0-116">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="4b2e0-117">Określa importerów WSDL, które importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="4b2e0-118">WSDL importer umożliwia importowanie metadanych, a także przekształcać dane tej informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="4b2e0-119">Selektywnie można było zaimportować informacje o kontraktu i punktu końcowego i właściwości, które ujawnić błędy importowania i zaakceptuj dotyczą proces importowania i konwersji informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="4b2e0-120">Obsługuje ona również importowania informacje o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumenty WSDL, rozszerzenia WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b2e0-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4b2e0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4b2e0-122">Element</span><span class="sxs-lookup"><span data-stu-id="4b2e0-122">Element</span></span>|<span data-ttu-id="4b2e0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4b2e0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b2e0-124">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="4b2e0-124">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="4b2e0-125">W sekcji klienta definiuje listę punktów końcowych, które klient może połączyć się z.</span><span class="sxs-lookup"><span data-stu-id="4b2e0-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b2e0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b2e0-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="4b2e0-127">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="4b2e0-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="4b2e0-128">Klienci</span><span class="sxs-lookup"><span data-stu-id="4b2e0-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
