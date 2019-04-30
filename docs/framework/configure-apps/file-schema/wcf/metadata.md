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
# <a name="metadata"></a>\<metadata>
Określa, jak metadane usługi mogą być przetwarzane.  
  
 \<system.ServiceModel>  
\<client>  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<policyImporters>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań. Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązań funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, których wymaga potwierdzenia.|  
|[\<wsdlImporters>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Określa importerów WSDL, które importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy. WSDL importer umożliwia importowanie metadanych, a także przekształcać dane tej informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym. Selektywnie można było zaimportować informacje o kontraktu i punktu końcowego i właściwości, które ujawnić błędy importowania i zaakceptuj dotyczą proces importowania i konwersji informacji o typie. Obsługuje ona również importowania informacje o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumenty WSDL, rozszerzenia WSDL i dokumentów schematu XML.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Klient >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|W sekcji klienta definiuje listę punktów końcowych, które klient może połączyć się z.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Konfiguracja klienta programu WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Klienci](../../../../../docs/framework/wcf/feature-details/clients.md)
