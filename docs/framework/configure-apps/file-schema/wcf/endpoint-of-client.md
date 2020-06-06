---
title: <endpoint> dla <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855319"
---
# <a name="endpoint-of-client"></a>\<endpoint> dla \<client>
Określa właściwości kontraktu, powiązania i adresu punktu końcowego kanału, który jest używany przez klientów do łączenia się z punktami końcowymi usługi na serwerze.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
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
|adres|Wymagany atrybut ciągu.<br /><br /> Określa adres punktu końcowego. Wartość domyślna to pusty ciąg. Adres musi być bezwzględnym identyfikatorem URI.|  
|behaviorConfiguration|Ciąg zawierający nazwę zachowania zachowania do użycia w celu utworzenia wystąpienia punktu końcowego. Nazwa zachowania musi znajdować się w zakresie, w którym jest zdefiniowana usługa. Wartość domyślna to pusty ciąg.|  
|powiązanie|Wymagany atrybut ciągu.<br /><br /> Ciąg określający typ powiązania do użycia. Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną. Typ jest zarejestrowany przez nazwę sekcji, a nie nazwę typu powiązania.|  
|bindingConfiguration|Opcjonalny. Ciąg zawierający nazwę konfiguracji powiązania, która ma być używana podczas tworzenia wystąpienia punktu końcowego. Konfiguracja powiązania musi znajdować się w zakresie w punkcie, w którym jest zdefiniowany punkt końcowy. Wartość domyślna to pusty ciąg.<br /><br /> Ten atrybut jest używany w połączeniu z programem w `binding` celu odwoływania się do określonej konfiguracji powiązań w pliku konfiguracji. Ustaw ten atrybut, jeśli próbujesz użyć niestandardowego powiązania. W przeciwnym razie może zostać zgłoszony wyjątek.|  
|przedsiębiorc|Wymagany atrybut ciągu.<br /><br /> Ciąg wskazujący, który kontrakt jest ujawniany przez ten punkt końcowy. Zestaw musi implementować typ kontraktu.|  
|endpointConfiguration|Ciąg określający nazwę standardowego punktu końcowego, który jest ustawiany przez `kind` atrybut, który odwołuje się do dodatkowych informacji konfiguracyjnych tego standardowego punktu końcowego. Ta sama nazwa musi być zdefiniowana w `<standardEndpoints>` sekcji.|  
|Natur|Ciąg określający typ stosowanego standardowego punktu końcowego. Typ musi być zarejestrowany w `<extensions>` sekcji lub pliku Machine. config. Jeśli nic nie jest określone, tworzony jest wspólny punkt końcowy kanału.|  
|name|Opcjonalny atrybut ciągu. Ten atrybut jednoznacznie identyfikuje punkt końcowy dla danego kontraktu. Można zdefiniować wielu klientów dla danego typu kontraktu. Każda definicja musi być zróżnicowana przy użyciu unikatowej nazwy konfiguracji. Jeśli ten atrybut zostanie pominięty, odpowiadający mu punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem kontraktu. Wartość domyślna to pusty ciąg.<br /><br /> `name`Atrybut powiązania służy do eksportowania definicji za pomocą języka WSDL.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Kolekcja nagłówków adresów.|  
|[\<identity>](identity.md)|Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<client>](client.md)|Sekcja konfiguracji, która definiuje listę punktów końcowych, z którymi klient może się połączyć.|  
  
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
- [Konfiguracja klienta programu WCF](../../../wcf/feature-details/client-configuration.md)
- [Klienci](../../../wcf/feature-details/clients.md)
