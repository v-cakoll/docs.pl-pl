---
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: 75f88219ab73d321b3e04c140bbfe964aed0b83a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225511"
---
# <a name="wsdlimporters"></a><span data-ttu-id="b8d12-101">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="b8d12-101">\<wsdlImporters></span></span>
<span data-ttu-id="b8d12-102">Ten element konfiguracji określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="b8d12-102">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="b8d12-103">Każdy element podrzędny jest <`wsdlImporter`>, który określa sposób, aby zaimportować metadane, jak również konwertować te informacje w różnych zajęciach, które reprezentują kontraktu i punktu końcowego informacji.</span><span class="sxs-lookup"><span data-stu-id="b8d12-103">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="b8d12-104">Selektywnie można było zaimportować informacje o kontraktu i punktu końcowego i właściwości, które ujawnić błędy importowania i zaakceptuj dotyczą proces importowania i konwersji informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="b8d12-104">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="b8d12-105">Obsługuje ona również importowania informacje o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumenty WSDL, rozszerzenia WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="b8d12-105">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d12-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8d12-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="b8d12-107">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="b8d12-107">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="b8d12-108">Klienci</span><span class="sxs-lookup"><span data-stu-id="b8d12-108">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
