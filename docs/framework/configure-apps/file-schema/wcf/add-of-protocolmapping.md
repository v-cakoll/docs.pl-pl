---
title: <add> dla <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 6197d01665d49a7c97ac9e44251abf15faf80a8f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850381"
---
# <a name="add-of-protocolmapping"></a>\<add> dla \<protocolMapping>
Reprezentuje domyślne mapowanie protokołu między schematem protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązaniem Windows Communication Foundation (WCF). Podczas tworzenia domyślnych punktów końcowych w środowisku uruchomieniowym środowisko WCF przegląda skonfigurowane mapowania i decyduje o tym, które powiązanie ma być używane dla określonego adresu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
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
|powiązanie|Ciąg określający typ powiązania, które ma być używane dla punktu końcowego podczas domyślnego tworzenia punktu końcowego.|  
|bindingConfiguration|Ciąg określający nazwę sekcji konfiguracji powiązania, do której ma zostać utworzone odwołanie.|  
|schemat|Schemat protokołu transportowego, który ma być używany dla domyślnego punktu końcowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|Reprezentuje sekcję konfiguracji definiującą domyślne mapowania protokołów między schematami protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązaniami Windows Communication Foundation (WCF).|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguracji przedstawia domyślne mapowanie protokołu w pliku Machine. config. To mapowanie domyślne można zastąpić na poziomie komputera, modyfikując plik Machine. config. Lub jeśli chcesz, aby przesłonić ją tylko w ramach zakresu aplikacji, możesz zastąpić tę sekcję w pliku konfiguracji aplikacji i zmienić mapowanie poszczególnych schematów protokołu.  
  
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
