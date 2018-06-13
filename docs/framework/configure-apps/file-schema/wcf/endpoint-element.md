---
title: '&lt;endpoint&gt;, element'
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: ef436acca40eaac135a54042b62abd76ec55febf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749507"
---
# <a name="ltendpointgt-element"></a>&lt;endpoint&gt;, element
Określa powiązanie, kontrakt i właściwości adresu punktu końcowego usługi, który jest używany do udostępnienia usług.  
  
 \<system.ServiceModel>  
\<usługi >  
\<punkt końcowy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|adres|Ciąg zawierający adres punktu końcowego. Adres można określić jako adres bezwzględny lub względny. Jeśli zostanie podany adres względny, hosta powinien zapewniać odpowiednie dla schemat transportu używane powiązanie adres podstawowy. Jeśli nie skonfigurowano adres podstawowy adres zakłada się, że adres dla tego punktu końcowego.<br /><br /> Wartość domyślna to ciąg pusty.|  
|behaviorConfiguration|Ciąg zawierający nazwę zachowania do użycia w punkcie końcowym.|  
|powiązanie|Wymagany atrybut ciągu określający typ powiązania do użycia. Typ musi mieć sekcję konfiguracji zarejestrowanych, aby można było odwoływać się. Typ jest zarejestrowaną nazwę sekcji, a nie nazwa typu powiązania.|  
|bindingConfiguration|Ciąg określający nazwę powiązania w celu użycia podczas tworzenia wystąpienia klasy punktu końcowego. Nazwa powiązania musi być w zakresie w punkcie, który zdefiniowano punktu końcowego. Wartość domyślna to ciąg pusty.<br /><br /> Ten atrybut jest używany w połączeniu z `binding` do odwołania konfigurację powiązania określonych w pliku konfiguracji. Ustaw ten atrybut, jeśli chcesz użyć niestandardowego powiązania. W przeciwnym razie może być wyjątek.|  
|bindingName|Ciąg określający unikalną kwalifikowaną nazwę powiązania w celu eksportu definicji za pośrednictwem WSDL. Wartość domyślna to ciąg pusty.|  
|bindingNamespace|Ciąg określający kwalifikowaną nazwę przestrzeni nazw powiązania dla definicji eksportowania za pośrednictwem WSDL. Wartość domyślna to ciąg pusty.|  
|kontrakt|Ciąg znaków wskazujący, który kontrakt jest ujawniany ten punkt końcowy. Zestaw musi implementować typ kontraktu. Jeśli implementacji usługi implementuje typu jeden kontrakt, tej właściwości można pominąć. Wartość domyślna to ciąg pusty.|  
|endpointConfiguration|Ciąg określający nazwę standardowego punktu końcowego, który jest uporządkowany według `kind` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego standardowego punktu końcowego. Taką samą nazwę, muszą być zdefiniowane w `<standardEndpoints>` sekcji.|  
|isSystemEndpoint|Wartość logiczna określająca, czy punkt końcowy jest punktem końcowym infrastruktury.|  
|rodzaj|Ciąg określający typ stosowanego standardowego punktu końcowego. Typ musi być zarejestrowana w `<extensions>` sekcji lub w pliku machine.config. Jeśli nie określono żadnej wartości, jest tworzona wspólnego punktu końcowego usługi.|  
|listenUriMode|Określa, jak warstwa transportu traktuje `ListenUri` dostarczony dla usługi do nasłuchiwania. Prawidłowe wartości to<br /><br /> -Jawne<br />— Unikatowe<br /><br /> Wartość domyślna to Explicit.|  
|Identyfikator ListenUri|Ciąg określający URI, na którym nasłuchuje usługa punktu końcowego. Wartość domyślna to ciąg pusty.|  
|nazwa|Atrybut opcjonalny. Ciąg określający nazwę punktu końcowego usługi. Wartość domyślna to łączenia nazwę i opis nazwy kontraktu. Usługi mogą mieć wiele punktów końcowych, więc punktu końcowego `name` atrybut różni się od nazwy usługi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nagłówki >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Kolekcja nagłówków adresu.|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Tożsamości, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Sekcja konfiguracyjna, który definiuje listę punktów końcowych, które klient może połączyć się.|  
  
## <a name="example"></a>Przykład  
 Jest to przykład konfiguracji punktu końcowego usługi.  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [Punkty końcowe: adresy, powiązania i kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Instrukcje: tworzenie punktu końcowego usługi w konfiguracji](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
