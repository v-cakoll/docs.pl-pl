---
title: '&lt;Nagłówki&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747154"
---
# <a name="ltheadersgt"></a>&lt;Nagłówki&gt;
Punkt końcowy może zostać zlikwidowane przez co najmniej jeden nagłówek SOAP oprócz jego podstawowego identyfikatora URI. Jeden zestaw scenariuszy, w których jest to przydatne to zestaw SOAP scenariuszy pośredniczącego w przypadku gdy punkt końcowy wymaga klientom tego punktu końcowego obejmują celem pośredników nagłówki SOAP. Ten element konfiguracji może służyć do definiowania takie nagłówki niestandardowy adres. Wpisy w kolekcji nagłówka punktu końcowego są zdefiniowane przez użytkownika elementy XML. Każdy element ma być poprawnie sformułowanym XML.  
  
 \<system.ServiceModel>  
\<Klient >  
\<punkt końcowy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Region||  
|Element członkowski||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<punkt końcowy >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Umożliwia skonfigurowanie różnych typów punktów końcowych.|  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalne nagłówki zawierają bardziej szczegółowe informacje adresowania do identyfikacji użytkownika lub interakcji z punktem końcowym. Na przykład nagłówków można wskazać sposobu przetwarzania wiadomości przychodzących, gdzie wysłać komunikat odpowiedzi punktu końcowego lub które wystąpienie usługi do przetwarzania komunikat przychodzący z konkretnego użytkownika, jeśli dostępnych jest wiele wystąpień.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [Punkty końcowe: adresy, powiązania i kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
