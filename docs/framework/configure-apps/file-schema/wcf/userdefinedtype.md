---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 46beb88cedf051ed1683161b6ed9b37273ed01f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182143"
---
# <a name="userdefinedtype"></a>\<userDefinedType>
Reprezentuje użytkownika zdefiniowany typ (UDT), które ma być zawarty w kontrakcie usługi.  
  
 \<system.ServiceModel>  
\<comContracts>  
\<comContract>  
\<userDefinedTypes>  
  
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
|`name`|Opcjonalny atrybut, który zawiera ciąg dostarczający czytelną nazwę typu. To nie jest używany przez środowisko uruchomieniowe, ale pomaga czytnik do rozróżniania typów.|  
|`TypeDefID`|Ciąg identyfikatora GUID, który identyfikuje określonego typu UDT w ramach z zarejestrowaną biblioteką typów.|  
|`TypeLibID`|Ciąg GUID identyfikujący zarejestrowaną bibliotekę typu, który definiuje typ.|  
|`TypeLibVersion`|Ciąg, który identyfikuje typ wersji biblioteki, który definiuje typ.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`userDefinedTypes`|Kolekcja `userDefinedType` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe integracji modelu COM + tworzy usług, sprawdzając biblioteki typów. Gdy składnik COM + zawiera metody, zaliczonych wariant, system nie może określić rzeczywiste typy, które mają być przekazane przed środowiska uruchomieniowego. W związku z tym spróbujesz przekazać użytkownika zdefiniowany typ (UDT) w ramach WARIANTU, go nie powiedzie się, ponieważ nie jest znany typ do serializacji.  
  
 Aby obejść ten problem, można dodać typów zdefiniowanych przez użytkownika do pliku konfiguracji, tak aby mogły być dołączony jako znanych typów w kontrakcie odpowiednią usługę. Aby to zrobić, należy jednoznacznie zidentyfikować UDT i kontraktami, oznacza to, oryginalnym interfejsy COM, w celu zastosowania.  
  
 W poniższym przykładzie pokazano, dodanie dwóch określonych typów do <`userDefinedTypes`> sekcji w pliku konfiguracji, w tym celu.  
  
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
  
 Podczas inicjowania usługi integration runtime odwołuje się do określonych typów i dodaje je do kolekcji znanych typów dla określonej umowy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [Współdziałanie z aplikacjami COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Instrukcje: konfigurowanie ustawień usługi COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
