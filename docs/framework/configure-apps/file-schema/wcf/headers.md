---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855171"
---
# \<headers>
Punkt końcowy może być rozkierowany przy użyciu co najmniej jednego nagłówka SOAP oprócz podstawowego identyfikatora URI. Jednym z zestawów scenariuszy, w których jest to przydatne, jest zestaw scenariuszy pośrednich protokołu SOAP, w których punkt końcowy wymaga od klientów tego punktu końcowego dołączenia nagłówków protokołu SOAP przeznaczonych dla pośredników. Ten element konfiguracji może służyć do definiowania takich niestandardowych nagłówków adresów. Wpisy w kolekcji nagłówka punktu końcowego są elementami XML zdefiniowanymi przez użytkownika. Każdy element musi być poprawnie sformułowanym plikiem XML.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Zdefiniowane przez użytkownika elementy XML.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|Konfiguruje różne typy punktów końcowych.|  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalne nagłówki zawierają bardziej szczegółowe informacje dotyczące adresowania, które identyfikują lub współpracują z punktem końcowym. Na przykład nagłówki mogą wskazywać, jak przetwarzać komunikat przychodzący, gdzie punkt końcowy powinien wysłać komunikat odpowiedzi lub którego wystąpienia usługi należy użyć do przetworzenia komunikatu przychodzącego od określonego użytkownika, gdy jest dostępnych wiele wystąpień.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [Punkty końcowe: Adresy, powiązania i kontrakty](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
