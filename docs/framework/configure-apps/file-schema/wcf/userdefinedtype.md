---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854833"
---
# <a name="userdefinedtype"></a>\<userDefinedType >
Reprezentuje typ zdefiniowany przez użytkownika (UDT), który ma zostać uwzględniony w kontrakcie usługi.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<userDefinedTypes >** ](userdefinedtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userDefinedType >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Opcjonalny atrybut, który zawiera ciąg, który zawiera nazwę typu, który można odczytać. Nie jest on używany przez środowisko uruchomieniowe, ale pomaga czytelnikowi odróżnić typy.|  
|`TypeDefID`|Ciąg identyfikatora GUID, który identyfikuje określony typ UDT w zarejestrowanej bibliotece typów.|  
|`TypeLibID`|Ciąg identyfikatora GUID, który identyfikuje zarejestrowanej biblioteki typów, która definiuje typ.|  
|`TypeLibVersion`|Ciąg, który identyfikuje wersję biblioteki typów, która definiuje typ.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`userDefinedTypes`|Kolekcja `userDefinedType` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko Integration Runtime środowiska COM+ tworzy usługi, sprawdzając bibliotekę typów. Gdy składnik COM+ zawiera metody, które przechodzą wariant, system nie może ustalić rzeczywistych typów do przekazania przed środowiskiem uruchomieniowym. W związku z tym podczas próby przekazania typu zdefiniowanego przez użytkownika (UDT) w ramach WARIANTu nie powiedzie się, ponieważ nie jest to znany typ serializacji.  
  
 Aby obejść ten problem, można dodać UDTs do pliku konfiguracji, aby można je było uwzględnić jako znane typy w odpowiednim kontrakcie usługi. Aby to zrobić, należy jednoznacznie zidentyfikować UDT i kontrakty, czyli oryginalne interfejsy COM, które z niego korzystają.  
  
 Poniższy przykład ilustruje dodanie dwóch konkretnych UDTs do sekcji > <`userDefinedTypes`w pliku konfiguracji.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <userDefinedTypes>
      <userDefinedType name="CustomerType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">
      </userDefinedType>
      <userDefinedType name="AddressType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">
      </userDefinedType>
    </userDefinedTypes>
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 Po zainicjowaniu usługi środowisko Integration Runtime wyszukuje określone typy i dodaje je do kolekcji znanych typów dla określonych kontraktów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [Współdziałanie z aplikacjami COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Instrukcje: Konfigurowanie ustawień usługi COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
