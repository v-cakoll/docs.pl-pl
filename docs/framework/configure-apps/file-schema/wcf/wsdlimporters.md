---
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: da9ab00c86e7f2657bfc28724d328ccbbc6957b1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69915165"
---
# \<wsdlImporters>
<span data-ttu-id="31073-101">Ten element konfiguracji określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 przy użyciu załączników WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="31073-101">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="31073-102">Każdy element podrzędny to <`wsdlImporter`>, który określa sposób importowania metadanych, oraz konwertowania tych informacji na różne klasy, które reprezentują informacje o kontrakcie i punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="31073-102">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="31073-103">Umożliwia selektywne importowanie informacji o kontraktach i punktach końcowych oraz właściwości, które uwidaczniają błędy importu i akceptują informacje o typie odpowiednie dla procesu importu i konwersji.</span><span class="sxs-lookup"><span data-stu-id="31073-103">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="31073-104">Obsługuje ona również importowanie informacji o powiązaniach i właściwości, które zapewniają dostęp do dowolnych dokumentów zasad, dokumentów WSDL, rozszerzeń WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="31073-104">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31073-105">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31073-105">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="31073-106">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="31073-106">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="31073-107">Klienci</span><span class="sxs-lookup"><span data-stu-id="31073-107">Clients</span></span>](../../../wcf/feature-details/clients.md)
