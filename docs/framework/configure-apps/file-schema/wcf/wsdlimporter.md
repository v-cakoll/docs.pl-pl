---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 13c9400874f1e02fac3ce0c3010153ad7806288c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915186"
---
# <a name="wsdlimporter"></a>\<wsdlImporter>
Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 przy użyciu załączników WS-Policy.  
  
\<system.ServiceModel>  
\<> klienta  
\<> metadanych  
\<wsdlImporters>  
\<wsdlImporter>  
  
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
|[\<wsdlImporters >](wsdlimporters.md)|Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 przy użyciu załączników WS-Policy.|  
  
## <a name="remarks"></a>Uwagi  
 Importer WSDL jest używany do importowania metadanych, a także konwertowania tych informacji na różne klasy, które reprezentują informacje o kontrakcie i punkcie końcowym. Umożliwia selektywne importowanie informacji o kontraktach i punktach końcowych oraz właściwości, które uwidaczniają błędy importu i akceptują informacje o typie odpowiednie dla procesu importu i konwersji. Obsługuje ona również importowanie informacji o powiązaniach i właściwości, które zapewniają dostęp do dowolnych dokumentów zasad, dokumentów WSDL, rozszerzeń WSDL i dokumentów schematu XML.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Konfiguracja klienta programu WCF](../../../wcf/feature-details/client-configuration.md)
- [Klienci](../../../wcf/feature-details/clients.md)
