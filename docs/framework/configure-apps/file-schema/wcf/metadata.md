---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855226"
---
# \<metadata>
<span data-ttu-id="716df-101">Określa sposób przetwarzania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="716df-101">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="716df-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="716df-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="716df-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="716df-103">Attributes and Elements</span></span>  
 <span data-ttu-id="716df-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="716df-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="716df-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="716df-105">Attributes</span></span>  
 <span data-ttu-id="716df-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="716df-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="716df-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="716df-107">Child Elements</span></span>  
  
|<span data-ttu-id="716df-108">Element</span><span class="sxs-lookup"><span data-stu-id="716df-108">Element</span></span>|<span data-ttu-id="716df-109">Opis</span><span class="sxs-lookup"><span data-stu-id="716df-109">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="716df-110">Określa wszystkich importerów zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="716df-110">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="716df-111">Importer zasad jest używany do wyszukiwania potwierdzeń niestandardowych zasad dotyczących funkcji powiązania, a także do dołączania niestandardowego elementu powiązania, który implementuje funkcje wymagane przez potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="716df-111">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="716df-112">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="716df-112">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="716df-113">Importer WSDL jest używany do importowania metadanych, a także konwertowania tych informacji na różne klasy, które reprezentują informacje o kontrakcie i punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="716df-113">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="716df-114">Umożliwia selektywne importowanie informacji o kontraktach i punktach końcowych oraz właściwości, które uwidaczniają błędy importu i akceptują informacje o typie odpowiednie dla procesu importu i konwersji.</span><span class="sxs-lookup"><span data-stu-id="716df-114">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="716df-115">Obsługuje ona również importowanie informacji o powiązaniach i właściwości, które zapewniają dostęp do dowolnych dokumentów zasad, dokumentów WSDL, rozszerzeń WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="716df-115">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="716df-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="716df-116">Parent Elements</span></span>  
  
|<span data-ttu-id="716df-117">Element</span><span class="sxs-lookup"><span data-stu-id="716df-117">Element</span></span>|<span data-ttu-id="716df-118">Opis</span><span class="sxs-lookup"><span data-stu-id="716df-118">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="716df-119">Sekcja klienta definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="716df-119">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="716df-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="716df-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="716df-121">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="716df-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="716df-122">Klienci</span><span class="sxs-lookup"><span data-stu-id="716df-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
