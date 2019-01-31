---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 63383fbd711f3725748e85fcf12e06b185bf30d1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257615"
---
# <a name="comcontract"></a>\<comContract>
Określa kontrakt usługi integracji COM +.  
  
 \<system.ServiceModel>  
\<comContracts>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|kontrakt|Ciąg, który zawiera typ kontraktu.|  
|nazwa|Ciąg, który zawiera nazwę kontraktu.|  
|— przestrzeń nazw|Ciąg, który zawiera przestrzeń nazw kontraktu.|  
|requiresSession|Wartość logiczna określająca, czy kontrakt mogą być używane tylko na powiązaniach sesyjnych. Podczas inicjowania usługi produktu integration runtime zapewnia to ustawienie jest zgodne z typ powiązania do użycia. Wyjątek jest generowany, jeśli jeden lub więcej powiązań dla kontraktu usługi są w konflikcie. Jeśli ta właściwość jest `false`i jednokierunkowe kanał jest w użyciu i istnieją [parametry out], wyjątek zostanie również wygenerowany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|persistableTypes|Wszystkie typy stałe.|  
|userDefinedTypes|Kolekcja z użytkownika zdefiniowanych typów (UDT), które ma być zawarty w kontrakcie usługi.|  
|exposedMethods|Kolekcja metod modelu COM +, które są dostępne, gdy interfejs składnika COM + jest widoczny jako usługi sieci Web.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|comContracts|Zawiera kolekcję `comContract` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrakty usług integracji modelu COM + są obecnie ograniczone do `http://tempuri.org` przestrzeni nazw i Nazwa kontraktu jest tworzony na podstawie obsługi interfejsu COM. Można jednak określić alternatywne przy użyciu `comContracts` sekcji, jak również `comContract` elementu w pliku konfiguracji. Na przykład można użyć następującej konfiguracji do określania przestrzeni nazw, Nazwa kontraktu i typów zdefiniowanych przez użytkownika do uwzględnienia, a także inne ustawienia dla kontraktu usługi.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 Podczas inicjowania usługi określonych przestrzeni nazw i nazwy kontraktów są stosowane do opisów wygenerowanego usługi.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [Współdziałanie z aplikacjami COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Instrukcje: Konfigurowanie ustawień usługi COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
