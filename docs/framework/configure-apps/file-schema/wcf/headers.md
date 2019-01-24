---
title: '&lt;headers&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: f47462ba63b9bd8868420ee9d3a320ba18c83c65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557828"
---
# <a name="ltheadersgt"></a>&lt;headers&gt;
Punkt końcowy może zostać zlikwidowane przez jeden lub więcej nagłówków protokołu SOAP, oprócz jego podstawowego identyfikatora URI. Jeden zestaw scenariuszy, w których jest to przydatne to zestaw scenariuszy pośrednie protokołu SOAP, gdzie punktu końcowego wymaga od klientów zawiera nagłówków protokołu SOAP, przeznaczona dla pośredników tego punktu końcowego. Ten element konfiguracji, może służyć do definiowania takich Nagłówki niestandardowe adresów. Wpisy w kolekcję nagłówków punktu końcowego są zdefiniowane przez użytkownika elementy XML. Każdy element musi być poprawnie sformułowany XML.  
  
 \<system.ServiceModel>  
\<client>  
\<punkt końcowy >  
  
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
|[\<punkt końcowy >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Służy do konfigurowania różnych typów punktów końcowych.|  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalne nagłówki zawierają więcej szczegółowych informacji adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym. Na przykład nagłówków, można wskazać sposób przetwarzania wiadomości przychodzących, gdzie wysłać komunikat odpowiedzi punktu końcowego lub które wystąpienie usługi do przetwarzania wiadomości przychodzących konkretnego użytkownika, jeśli wiele wystąpień są dostępne.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [Punkty końcowe: Adresy, powiązania i kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
