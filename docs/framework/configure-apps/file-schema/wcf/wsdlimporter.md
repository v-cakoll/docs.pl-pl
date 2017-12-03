---
title: '&lt;Element wsdlImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f4fe6c82d0a6f53dfa05a82622e0412280212cc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltwsdlimportergt"></a>&lt;Element wsdlImporter&gt;
Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.  
  
\<System. ServiceModel >  
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
 WSDL importer umożliwia importowanie metadanych, jak również przekonwertować tych informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym. Selektywnie importowaniem informacji kontraktu i punktu końcowego i właściwości, które ujawnia błędy importu i zaakceptuj typu informacje istotne dla procesu importowania i konwersji. Obsługuje ona również importowania informacji o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumentów WSDL, rozszerzenia WSDL i dokumentach schematów XML.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [Konfiguracja klienta programu WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienci](../../../../../docs/framework/wcf/feature-details/clients.md)
