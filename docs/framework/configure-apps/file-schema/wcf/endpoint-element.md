---
title: <endpoint>, element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855378"
---
# <a name="endpoint-element"></a>\<Element > punktu końcowego
Określa powiązanie, kontrakt i właściwości adresu dla punktu końcowego usługi, który jest używany do udostępniania usług.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usług**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usługi**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> punktu końcowego**  
  
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
|adres|Ciąg zawierający adres punktu końcowego. Adres może być określony jako adres bezwzględny lub względny. Jeśli zostanie podany adres względny, host powinien podać adres podstawowy odpowiedni dla schematu transportu używanego w powiązaniu. Jeśli adres nie jest skonfigurowany, zakłada się, że adres podstawowy jest adresem dla tego punktu końcowego.<br /><br /> Wartość domyślna to pusty ciąg.|  
|behaviorConfiguration|Ciąg zawierający nazwę zachowania do użycia w punkcie końcowym.|  
|powiązanie|Wymagany atrybut ciągu, który określa typ powiązania do użycia. Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną. Typ jest typem zarejestrowanym według nazwy sekcji, a nie nazwą typu powiązania.|  
|bindingConfiguration|Ciąg określający nazwę powiązania powiązania do użycia podczas tworzenia wystąpienia punktu końcowego. Nazwa powiązania musi znajdować się w zakresie w punkcie, w którym jest zdefiniowany punkt końcowy. Wartość domyślna to pusty ciąg.<br /><br /> Ten atrybut jest używany w połączeniu z `binding` programem w celu odwoływania się do określonej konfiguracji powiązań w pliku konfiguracji. Ustaw ten atrybut, jeśli próbujesz użyć niestandardowego powiązania. W przeciwnym razie może zostać zgłoszony wyjątek.|  
|powiązaniename|Ciąg określający unikalną kwalifikowaną nazwę powiązania w celu eksportu definicji za pomocą WSDL. Wartość domyślna to pusty ciąg.|  
|bindingNamespace|Ciąg określający kwalifikowaną nazwę przestrzeni nazw powiązania w celu eksportu definicji za pomocą WSDL. Wartość domyślna to pusty ciąg.|  
|Przedsiębiorc|Ciąg wskazujący, który kontrakt jest ujawniany przez ten punkt końcowy. Zestaw musi implementować typ kontraktu. Jeśli implementacja usługi implementuje pojedynczy typ kontraktu, ta właściwość może zostać pominięta. Wartość domyślna to pusty ciąg.|  
|endpointConfiguration|Ciąg określający nazwę standardowego punktu końcowego, który jest ustawiany przez `kind` atrybut, który odwołuje się do dodatkowych informacji konfiguracyjnych tego standardowego punktu końcowego. Ta sama nazwa musi być zdefiniowana w `<standardEndpoints>` sekcji.|  
|isSystemEndpoint|Wartość logiczna określająca, czy punkt końcowy jest punktem końcowym infrastruktury.|  
|Natur|Ciąg określający typ stosowanego standardowego punktu końcowego. Typ musi być zarejestrowany w `<extensions>` sekcji lub pliku Machine. config. Jeśli nic nie zostanie określone, tworzony jest wspólny punkt końcowy usługi.|  
|listenUriMode|Określa sposób, w jaki transport `ListenUri` traktuje podany na potrzeby nasłuchiwania usługi. Prawidłowe wartości to<br /><br /> -Jawne<br />-Unikatowy<br /><br /> Wartość domyślna to explicit.|  
|listenUri|Ciąg określający identyfikator URI, z którego nasłuchuje punkt końcowy usługi. Wartość domyślna to pusty ciąg.|  
|nazwa|Atrybut opcjonalny. Ciąg określający nazwę punktu końcowego usługi. Wartość domyślna to połączenie nazwy powiązania i nazwy opisu kontraktu. Usługi mogą mieć wiele punktów końcowych, więc `name` atrybut punktu końcowego różni się od nazwy usługi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nagłówki >](headers.md)|Kolekcja nagłówków adresów.|  
|[\<> tożsamości](identity.md)|Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> usługi](service.md)|Sekcja konfiguracji, która definiuje listę punktów końcowych, z którymi klient może się połączyć.|  
  
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
- [Punktów końcowych Adresy, powiązania i kontrakty](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
