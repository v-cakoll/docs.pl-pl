---
title: <add> dla <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 85d09c920de2ca1ab4971551ff98ea58c4492f44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109268"
---
# <a name="add-of-protocolmapping"></a>\<Dodaj > z \<protocolMapping >
Reprezentuje domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) a powiązaniem Windows Communication Foundation (WCF). Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, WCF analizuje skonfigurowanego mapowania i decyduje o tym, na które powiązania do użycia dla określonego na podstawie adresu.  
  
 \<system.serviceModel>  
\<protocolMapping >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Ciąg określający typ powiązania stosowanego dla punktu końcowego podczas domyślnego tworzenia punktu końcowego.|  
|bindingConfiguration|Ciąg określający nazwę sekcji konfiguracji powiązania można odwoływać się.|  
|schemat|Schematem protokołu transportu, która ma być używany dla domyślnego punktu końcowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Reprezentuje sekcję konfiguracji do definiowania domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązania Windows Communication Foundation (WCF).|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config. Możesz przesłonić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config. Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracyjnym aplikacji i zmienić mapowanie schematów pojedynczy protokół.  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
