---
title: <endpoint> dla <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 3af41ad5b5681b08aac44d984372ab5ac66caf5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673228"
---
# <a name="endpoint-of-client"></a>\<punkt końcowy > z \<klienta >
Określa kontrakt, powiązanie i właściwości adresu punktu końcowego kanału, który jest używany przez klientów do łączenia się z punktami końcowymi usługi na serwerze.  
  
 \<system.ServiceModel>  
\<client>  
\<punkt końcowy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|adres|Atrybut wymagany ciąg.<br /><br /> Określa adres punktu końcowego. Wartość domyślna to ciąg pusty. Adres musi być bezwzględnym identyfikatorem URI.|  
|behaviorConfiguration|Ciąg zawierający nazwę zachowania użytego do utworzenia wystąpienia punktu końcowego. Nazwa zachowania musi być w zakresie w punkcie, który jest zdefiniowany przez usługę. Wartość domyślna to ciąg pusty.|  
|powiązanie|Atrybut wymagany ciąg.<br /><br /> Ciąg, który określa typ powiązania do użycia. Typ musi mieć sekcję zarejestrowanych konfiguracji, aby odwoływać się. Ten typ jest zarejestrowany przy użyciu nazwy sekcji, a nie przez nazwę typu powiązania.|  
|bindingConfiguration|Opcjonalna. Ciąg zawierający nazwę konfiguracji powiązania, który ma być używany, gdy punkt końcowy zostanie uruchomiony. Konfiguracja powiązania musi być w zakresie w punkcie, który jest zdefiniowany punkt końcowy. Wartość domyślna to ciąg pusty.<br /><br /> Ten atrybut jest używany w połączeniu z `binding` można odwoływać się do konfiguracji powiązania określone w pliku konfiguracji. Ustaw ten atrybut, jeśli chcesz użyć niestandardowego powiązania. W przeciwnym razie może być wyjątek.|  
|kontrakt|Atrybut wymagany ciąg.<br /><br /> Ciąg wskazujący, który kontrakt tego punktu końcowego jest uwidaczniany. Zestaw musi implementować typ kontraktu.|  
|endpointConfiguration|Ciąg określający nazwę standardowego punktu końcowego, który jest uporządkowany według `kind` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego standardowego punktu końcowego. Taką samą nazwę muszą być zdefiniowane w `<standardEndpoints>` sekcji.|  
|rodzaj|Ciąg określający typ stosowanego standardowego punktu końcowego. Typ musi być zarejestrowana w `<extensions>` sekcji lub w pliku machine.config. Jeśli nic nie zostanie określony, zostanie utworzony wspólnego punktu końcowego kanału.|  
|nazwa|Atrybut opcjonalny ciąg. Ten atrybut jest jednoznacznie identyfikuje punkt końcowy dla danego kontraktu. Można zdefiniować wielu klientach na potrzeby danego typu kontraktu. Każda definicja musi być rozróżniane przez unikatową nazwę. Jeśli ten atrybut zostanie pominięty, odpowiedni punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem umowy. Wartość domyślna to ciąg pusty.<br /><br /> `name` Atrybut powiązania jest używany w celu eksportu definicji za pośrednictwem WSDL.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Kolekcję nagłówków adresowych.|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Klient >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Sekcja konfiguracji, który definiuje listę punktów końcowych, które klient może połączyć się z.|  
  
## <a name="example"></a>Przykład  
 Jest to przykład konfiguracji punktu końcowego kanału.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [Konfiguracja klienta programu WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Klienci](../../../../../docs/framework/wcf/feature-details/clients.md)
