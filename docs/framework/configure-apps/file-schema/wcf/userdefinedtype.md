---
title: '&lt;userDefinedType&gt;'
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: ffa9480312c278097ae110c686fb507209c117e1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755282"
---
# <a name="ltuserdefinedtypegt"></a>&lt;userDefinedType&gt;
Reprezentuje użytkownika zdefiniowany typ (UDT), które ma być zawarty w kontrakcie usługi.  
  
 \<system.ServiceModel>  
\<comContracts>  
\<comContract >  
\<userDefinedTypes >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
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
|`name`|Opcjonalny atrybut, który zawiera ciąg, który zawiera czytelną nazwę typu. To nie jest używany przez środowisko uruchomieniowe, ale pomaga czytnik do rozróżniania typów.|  
|`TypeDefID`|Ciąg GUID identyfikujący określonego typu UDT w ramach z zarejestrowaną biblioteką typów.|  
|`TypeLibID`|Ciąg GUID identyfikujący zarejestrowaną bibliotekę typu, który definiuje typ.|  
|`TypeLibVersion`|Ciąg, który identyfikuje wersję biblioteki typu, który definiuje typ.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`userDefinedTypes`|Kolekcja `userDefinedType` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Środowiska uruchomieniowego integracji COM + tworzy usług, sprawdzając, czy biblioteki typów. Gdy składnik modelu COM + zawiera metody, które przekazują wariant, system nie może określić rzeczywiste typy do przekazania przed środowiska wykonawczego. W związku z tym przy próbie przekazania użytkownika zdefiniowany typ (UDT) w ramach WARIANTU go nie działa, ponieważ nie jest znanym typem do serializacji.  
  
 Aby obejść ten problem, można dodać typów do pliku konfiguracji, tak aby mogły być uwzględniana jako znane typy kontraktu odpowiednią usługę. Aby to zrobić, należy jednoznacznie zidentyfikować UDT i kontraktem (kontraktami), oznacza to, oryginalny interfejsy modelu COM, który korzysta z niego.  
  
 W poniższym przykładzie pokazano, dodawanie dwóch określonych typów do <`userDefinedTypes`> pliku konfiguracji, w tym celu.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
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
  
 Podczas inicjowania usługi integracji środowiska uruchomieniowego odwołuje się do określonych typów i dodaje je do kolekcji znanych typów dla określonego umów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Współdziałanie z aplikacjami COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Instrukcje: konfigurowanie ustawień usługi COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
