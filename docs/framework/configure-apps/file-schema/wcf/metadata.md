---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855226"
---
# <a name="metadata"></a><span data-ttu-id="4e777-101">\<> metadanych</span><span class="sxs-lookup"><span data-stu-id="4e777-101">\<metadata></span></span>
<span data-ttu-id="4e777-102">Określa sposób przetwarzania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="4e777-102">Specifies how service metadata can be processed.</span></span>  
  
<span data-ttu-id="4e777-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e777-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4e777-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4e777-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4e777-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="4e777-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="4e777-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> metadanych**</span><span class="sxs-lookup"><span data-stu-id="4e777-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e777-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e777-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e777-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e777-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4e777-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e777-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e777-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e777-110">Attributes</span></span>  
 <span data-ttu-id="4e777-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="4e777-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e777-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e777-112">Child Elements</span></span>  
  
|<span data-ttu-id="4e777-113">Element</span><span class="sxs-lookup"><span data-stu-id="4e777-113">Element</span></span>|<span data-ttu-id="4e777-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4e777-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e777-115">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="4e777-115">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="4e777-116">Określa wszystkich importerów zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="4e777-116">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="4e777-117">Importer zasad jest używany do wyszukiwania potwierdzeń niestandardowych zasad dotyczących funkcji powiązania, a także do dołączania niestandardowego elementu powiązania, który implementuje funkcje wymagane przez potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="4e777-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="4e777-118">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="4e777-118">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="4e777-119">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="4e777-119">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="4e777-120">Importer WSDL jest używany do importowania metadanych, a także konwertowania tych informacji na różne klasy, które reprezentują informacje o kontrakcie i punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="4e777-120">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="4e777-121">Umożliwia selektywne importowanie informacji o kontraktach i punktach końcowych oraz właściwości, które uwidaczniają błędy importu i akceptują informacje o typie odpowiednie dla procesu importu i konwersji.</span><span class="sxs-lookup"><span data-stu-id="4e777-121">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="4e777-122">Obsługuje ona również importowanie informacji o powiązaniach i właściwości, które zapewniają dostęp do dowolnych dokumentów zasad, dokumentów WSDL, rozszerzeń WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="4e777-122">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4e777-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e777-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4e777-124">Element</span><span class="sxs-lookup"><span data-stu-id="4e777-124">Element</span></span>|<span data-ttu-id="4e777-125">Opis</span><span class="sxs-lookup"><span data-stu-id="4e777-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e777-126">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="4e777-126">\<client></span></span>](client.md)|<span data-ttu-id="4e777-127">Sekcja klienta definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="4e777-127">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e777-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e777-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="4e777-129">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="4e777-129">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="4e777-130">Klienci</span><span class="sxs-lookup"><span data-stu-id="4e777-130">Clients</span></span>](../../../wcf/feature-details/clients.md)
