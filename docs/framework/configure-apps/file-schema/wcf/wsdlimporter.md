---
title: '&lt;Element wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 43c1a50c740cd9c75ee641e4ac4d0fa8ea3ca36b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144993"
---
# <a name="ltwsdlimportergt"></a>&lt;Element wsdlImporter&gt;
Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.  
  
\<system.ServiceModel>  
\<Klient >  
\<metadane >  
\<wsdlImporters >  
\<Element wsdlImporter >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`type`|Typ tego elementu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<wsdlImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.|  
  
## <a name="remarks"></a>Uwagi  
 WSDL importer umożliwia importowanie metadanych, a także przekształcać dane tej informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym. Selektywnie można było zaimportować informacje o kontraktu i punktu końcowego i właściwości, które ujawnić błędy importowania i zaakceptuj dotyczą proces importowania i konwersji informacji o typie. Obsługuje ona również importowania informacje o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumenty WSDL, rozszerzenia WSDL i dokumentów schematu XML.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [Konfiguracja klienta programu WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienci](../../../../../docs/framework/wcf/feature-details/clients.md)
