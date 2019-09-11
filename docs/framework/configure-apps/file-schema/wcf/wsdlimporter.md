---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854756"
---
# <a name="wsdlimporter"></a><span data-ttu-id="0d748-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="0d748-101">\<wsdlImporter></span></span>
<span data-ttu-id="0d748-102">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 przy użyciu załączników WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="0d748-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="0d748-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d748-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d748-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0d748-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0d748-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="0d748-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="0d748-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> metadanych**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="0d748-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="0d748-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsdlImporters >** ](wsdlimporters.md)</span><span class="sxs-lookup"><span data-stu-id="0d748-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)</span></span>  
<span data-ttu-id="0d748-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Element WsdlImporter >**</span><span class="sxs-lookup"><span data-stu-id="0d748-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d748-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d748-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d748-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0d748-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0d748-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0d748-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d748-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0d748-112">Attributes</span></span>  
  
|<span data-ttu-id="0d748-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0d748-113">Attribute</span></span>|<span data-ttu-id="0d748-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0d748-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0d748-115">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="0d748-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d748-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0d748-116">Child Elements</span></span>  
 <span data-ttu-id="0d748-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="0d748-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d748-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0d748-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0d748-119">Element</span><span class="sxs-lookup"><span data-stu-id="0d748-119">Element</span></span>|<span data-ttu-id="0d748-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0d748-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d748-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="0d748-121">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="0d748-122">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 przy użyciu załączników WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="0d748-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d748-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d748-123">Remarks</span></span>  
 <span data-ttu-id="0d748-124">Importer WSDL jest używany do importowania metadanych, a także konwertowania tych informacji na różne klasy, które reprezentują informacje o kontrakcie i punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="0d748-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="0d748-125">Umożliwia selektywne importowanie informacji o kontraktach i punktach końcowych oraz właściwości, które uwidaczniają błędy importu i akceptują informacje o typie odpowiednie dla procesu importu i konwersji.</span><span class="sxs-lookup"><span data-stu-id="0d748-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="0d748-126">Obsługuje ona również importowanie informacji o powiązaniach i właściwości, które zapewniają dostęp do dowolnych dokumentów zasad, dokumentów WSDL, rozszerzeń WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="0d748-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d748-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d748-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="0d748-128">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="0d748-128">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="0d748-129">Klienci</span><span class="sxs-lookup"><span data-stu-id="0d748-129">Clients</span></span>](../../../wcf/feature-details/clients.md)
