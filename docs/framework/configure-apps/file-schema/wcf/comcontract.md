---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850026"
---
# \<comContract>
Określa kontrakt usługi integracji COM+.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
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
|przedsiębiorc|Ciąg, który zawiera typ kontraktu.|  
|name|Ciąg, który zawiera nazwę kontraktu.|  
|namespace|Ciąg, który zawiera przestrzeń nazw kontraktu.|  
|requiresSession|Wartość logiczna określająca, czy kontrakt może być używany tylko na powiązaniach sesji. Po zainicjowaniu usługi środowisko Integration Runtime zapewnia spójność tego ustawienia z typem powiązania, które ma być używane. Wyjątek jest generowany, jeśli co najmniej jedno powiązanie kontraktu jest w konflikcie. Jeśli ta właściwość ma wartość `false` , a kanał jednokierunkowy jest używany i istnieją wszystkie parametry [out], generowany jest również wyjątek.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|persistableTypes|Wszystkie typy, które są trwałe.|  
|userDefinedTypes|Kolekcja typów zdefiniowanych przez użytkownika (UDT), które mają zostać uwzględnione w kontrakcie usługi.|  
|exposedMethods|Kolekcja metod modelu COM+, które są dostępne, gdy interfejs składnika modelu COM+ jest udostępniany jako usługa sieci Web.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|comContracts|Zawiera kolekcję `comContract` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrakty usługi integracji modelu COM+ są obecnie ograniczone do `http://tempuri.org` przestrzeni nazw, a nazwa kontraktu pochodzi od pomocniczego interfejsu com. Można jednak określić alternatywy przy użyciu `comContracts` sekcji, a także `comContract` elementu w pliku konfiguracji. Można na przykład użyć poniższej konfiguracji, aby określić przestrzeń nazw, nazwę kontraktu i typy zdefiniowane przez użytkownika, a także inne ustawienia dla kontraktu usługi.  
  
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
  
 Po zainicjowaniu usługi określone nazwy obszarów nazw i kontraktów są stosowane do opisów wygenerowanych usług.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [Integrowanie z aplikacjami COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Instrukcje: konfigurowanie ustawień usługi COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
