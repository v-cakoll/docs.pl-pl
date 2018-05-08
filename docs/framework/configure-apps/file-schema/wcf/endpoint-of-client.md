---
title: '&lt;endpoint&gt; w &lt;client&gt;'
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f9a69483ab058823fd419edc84868e801b91d2c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltendpointgt-of-ltclientgt"></a>&lt;endpoint&gt; w &lt;client&gt;
Określa kontrakt, powiązanie i właściwości adresu punktu końcowego kanału, który jest używany przez klientów nawiązywania połączenia z usługą punktów końcowych na serwerze.  
  
 \<system.ServiceModel>  
\<Klient >  
\<punkt końcowy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"   endpointConfiguration="String"   kind="String"  
   name="String"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|adres|Atrybut wymaganych parametrów.<br /><br /> Określa adres punktu końcowego. Wartość domyślna to ciąg pusty. Adres musi być bezwzględnym identyfikatorem URI.|  
|behaviorConfiguration|Ciąg zawierający nazwę zachowania zachowania, które ma być używany do utworzenia wystąpienia punktu końcowego. Nazwa zachowania musi być w zakresie w punkcie, który usługa została zdefiniowana. Wartość domyślna to ciąg pusty.|  
|powiązanie|Atrybut wymaganych parametrów.<br /><br /> Ciąg określający typ powiązania do użycia. Typ musi mieć sekcję konfiguracji zarejestrowanych, aby można było odwoływać się. Ten typ jest zarejestrowany przez nazwę sekcji zamiast nazwą typu powiązania.|  
|bindingConfiguration|Opcjonalna. Ciąg zawierający nazwę konfiguracji powiązania ma być używany podczas tworzenia wystąpienia klasy punktu końcowego. Konfiguracja powiązania musi należeć do zakresu na punktu, w którym zdefiniowano punktu końcowego. Wartość domyślna to ciąg pusty.<br /><br /> Ten atrybut jest używany w połączeniu z `binding` do odwołania konfigurację powiązania określonych w pliku konfiguracji. Ustaw ten atrybut, jeśli chcesz użyć niestandardowego powiązania. W przeciwnym razie może być wyjątek.|  
|kontrakt|Atrybut wymaganych parametrów.<br /><br /> Ciąg znaków wskazujący, który kontrakt jest ujawniany ten punkt końcowy. Zestaw musi implementować typ kontraktu.|  
|endpointConfiguration|Ciąg określający nazwę standardowego punktu końcowego, który jest uporządkowany według `kind` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego standardowego punktu końcowego. Taką samą nazwę, muszą być zdefiniowane w `<standardEndpoints>` sekcji.|  
|rodzaj|Ciąg określający typ stosowanego standardowego punktu końcowego. Typ musi być zarejestrowana w `<extensions>` sekcji lub w pliku machine.config. Jeśli nie określono żadnej wartości, jest tworzona wspólnego punktu końcowego kanału.|  
|nazwa|Opcjonalny atrybut ciągu. Ten atrybut jest unikatowym identyfikatorem dla danego kontraktu punktu końcowego. Można określić wielu klientów dla danego typu kontraktu. Każda definicja należy zróżnicować przez unikatową nazwę. W przypadku pominięcia tego atrybutu odpowiedniego punkt końcowy jest używany jako domyślny punkt końcowy skojarzone z określonym typem kontraktu. Wartość domyślna to ciąg pusty.<br /><br /> `name` Atrybut powiązania jest używany w celu eksportu definicji za pośrednictwem WSDL.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nagłówki >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Kolekcja nagłówków adresu.|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Tożsamości, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Klient >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Sekcja konfiguracyjna, który definiuje listę punktów końcowych, które klient może połączyć się.|  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>  
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 [Konfiguracja klienta programu WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienci](../../../../../docs/framework/wcf/feature-details/clients.md)
