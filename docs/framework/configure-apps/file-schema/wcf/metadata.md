---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 4555dc9c2e0b783de2fb57e47c9aada0d69462e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931304"
---
# <a name="metadata"></a><span data-ttu-id="9e407-101">\<> metadanych</span><span class="sxs-lookup"><span data-stu-id="9e407-101">\<metadata></span></span>
<span data-ttu-id="9e407-102">Określa sposób przetwarzania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="9e407-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="9e407-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9e407-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9e407-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="9e407-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e407-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e407-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e407-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9e407-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9e407-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9e407-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e407-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9e407-108">Attributes</span></span>  
 <span data-ttu-id="9e407-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="9e407-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9e407-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9e407-110">Child Elements</span></span>  
  
|<span data-ttu-id="9e407-111">Element</span><span class="sxs-lookup"><span data-stu-id="9e407-111">Element</span></span>|<span data-ttu-id="9e407-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9e407-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e407-113">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="9e407-113">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="9e407-114">Określa wszystkich importerów zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="9e407-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="9e407-115">Importer zasad jest używany do wyszukiwania potwierdzeń niestandardowych zasad dotyczących funkcji powiązania, a także do dołączania niestandardowego elementu powiązania, który implementuje funkcje wymagane przez potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="9e407-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="9e407-116">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="9e407-116">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="9e407-117">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="9e407-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="9e407-118">Importer WSDL jest używany do importowania metadanych, a także konwertowania tych informacji na różne klasy, które reprezentują informacje o kontrakcie i punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="9e407-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="9e407-119">Umożliwia selektywne importowanie informacji o kontraktach i punktach końcowych oraz właściwości, które uwidaczniają błędy importu i akceptują informacje o typie odpowiednie dla procesu importu i konwersji.</span><span class="sxs-lookup"><span data-stu-id="9e407-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="9e407-120">Obsługuje ona również importowanie informacji o powiązaniach i właściwości, które zapewniają dostęp do dowolnych dokumentów zasad, dokumentów WSDL, rozszerzeń WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="9e407-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e407-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9e407-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9e407-122">Element</span><span class="sxs-lookup"><span data-stu-id="9e407-122">Element</span></span>|<span data-ttu-id="9e407-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9e407-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e407-124">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="9e407-124">\<client></span></span>](client.md)|<span data-ttu-id="9e407-125">Sekcja klienta definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="9e407-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e407-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e407-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="9e407-127">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="9e407-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="9e407-128">Klienci</span><span class="sxs-lookup"><span data-stu-id="9e407-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
