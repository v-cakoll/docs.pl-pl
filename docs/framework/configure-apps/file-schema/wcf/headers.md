---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 660497012dd057e4ecf95524833e2573fe03a8b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224563"
---
# <a name="headers"></a>\<headers>
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
- [Punkty końcowe: adresy, wiązania i kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
