---
title: <endpoint> — element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 94b6cc6225171d90164e6d6880e1095513f16ece
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354738"
---
# <a name="endpoint-element"></a>\<punkt końcowy > element
Określa powiązanie, kontrakt i właściwości adresu punktu końcowego usługi, który jest używany do udostępnienia usług.  
  
 \<system.ServiceModel>  
\<service>  
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
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|adres|Ciąg, który zawiera adres punktu końcowego. Adres można określić jako bezwzględny lub względny adres. Jeśli nie podano adresu względnego, host powinien zapewniać odpowiedni dla używany w wiązaniu schemat transportu adres podstawowy. Jeśli adres nie jest skonfigurowany, adres bazowy zakłada się, że adres dla tego punktu końcowego.<br /><br /> Wartość domyślna to ciąg pusty.|  
|behaviorConfiguration|Ciąg zawierający nazwę zachowania użytego w punkcie końcowym.|  
|powiązanie|Wymagany atrybut ciągu określający typ powiązania do użycia. Typ musi mieć sekcję zarejestrowanych konfiguracji, aby odwoływać się. Typ jest zarejestrowaną nazwę sekcji, a nie nazwa typu powiązania.|  
|bindingConfiguration|Ciąg określający nazwę powiązania w celu użycia podczas tworzenia wystąpienia punktu końcowego. Nazwa powiązania musi być w zakresie w punkcie, który jest zdefiniowany punkt końcowy. Wartość domyślna to ciąg pusty.<br /><br /> Ten atrybut jest używany w połączeniu z `binding` można odwoływać się do konfiguracji powiązania określone w pliku konfiguracji. Ustaw ten atrybut, jeśli chcesz użyć niestandardowego powiązania. W przeciwnym razie może być wyjątek.|  
|bindingName|Ciąg określający unikalną kwalifikowaną nazwę powiązania w celu eksportu definicji za pośrednictwem WSDL. Wartość domyślna to ciąg pusty.|  
|bindingNamespace|Ciąg określający kwalifikowaną nazwę przestrzeni nazw powiązania dla definicji eksportowania za pośrednictwem WSDL. Wartość domyślna to ciąg pusty.|  
|kontrakt|Ciąg wskazujący, który kontrakt tego punktu końcowego jest uwidaczniany. Zestaw musi implementować typ kontraktu. Jeśli implementacji usługi implementuje typ kontraktu pojedynczego, tej właściwości można pominąć. Wartość domyślna to ciąg pusty.|  
|endpointConfiguration|Ciąg określający nazwę standardowego punktu końcowego, który jest uporządkowany według `kind` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego standardowego punktu końcowego. Taką samą nazwę muszą być zdefiniowane w `<standardEndpoints>` sekcji.|  
|isSystemEndpoint|Wartość logiczna określająca, czy punkt końcowy jest punktem końcowym infrastruktury.|  
|rodzaj|Ciąg określający typ stosowanego standardowego punktu końcowego. Typ musi być zarejestrowana w `<extensions>` sekcji lub w pliku machine.config. Jeśli nic nie zostanie określony, zostanie utworzony wspólnego punktu końcowego usługi.|  
|listenUriMode|Określa, jak warstwa transportu traktuje `ListenUri` określone usługi do nasłuchiwania. Prawidłowe wartości to:<br /><br /> -Jawne<br />— Unikatowe<br /><br /> Wartość domyślna to jawne.|  
|listenUri|Ciąg określający URI, na którym nasłuchuje punktu końcowego usługi. Wartość domyślna to ciąg pusty.|  
|nazwa|Atrybut opcjonalny. Ciąg określający nazwę punktu końcowego usługi. Wartość domyślna to łączenie nazwę i opis nazwy kontraktu. Usługi mogą mieć wiele punktów końcowych, więc punktu końcowego `name` atrybut różni się od nazwy usługi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Kolekcję nagłówków adresowych.|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Sekcja konfiguracji, który definiuje listę punktów końcowych, które klient może połączyć się z.|  
  
## <a name="example"></a>Przykład  
 Jest to przykład konfiguracji punktu końcowego usługi.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [Punkty końcowe: Adresy, powiązania i kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
