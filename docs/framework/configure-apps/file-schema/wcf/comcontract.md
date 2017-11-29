---
title: '&lt;comContract&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b22c8d0b72d4dfc63eb5fa9afa073f993f75418e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcomcontractgt"></a>&lt;comContract&gt;
Określa kontrakt usługi integracji COM +.  
  
 \<System. ServiceModel >  
\<comContracts >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
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
|— przestrzeń nazw|Ciąg zawierający przestrzeń nazw kontraktu.|  
|Element requiresSession|Wartość logiczna określająca, czy kontrakt można używać tylko na powiązaniach sesyjnych. Podczas inicjowania usługi środowiska uruchomieniowego integracji zapewnia, że to ustawienie jest zgodne z typ powiązania do użycia. Wyjątek jest generowany, jeśli jeden lub więcej powiązania dla kontraktu będących w konflikcie. Jeśli ta właściwość jest `false`, jednokierunkowe kanał jest w użyciu i istnieją parametry [out], wyjątek zostanie również wygenerowany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|persistableTypes|Wszystkie typy możliwy do utrwalenia.|  
|userDefinedTypes|Kolekcja z użytkownika zdefiniowanych typów (UDT), które ma być zawarty w kontrakcie usługi.|  
|exposedMethods|Kolekcja metod modelu COM +, które są dostępne, gdy interfejs składnika COM + jest udostępniany jako usługa sieci Web.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|comContracts|Zawiera kolekcję `comContract` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrakty usług integracji COM + są obecnie ograniczone do przestrzeni nazw "http://tempuri.org", a Nazwa kontraktu pochodzi od obsługi interfejsu COM. Można jednak określić alternatywne przy użyciu `comContracts` sekcji, jak również `comContract` w pliku konfiguracji. Na przykład można użyć następującej konfiguracji do określania przestrzeni nazw, Nazwa kontraktu i typy zdefiniowane przez użytkownika do uwzględnienia, a także innych ustawień dla kontraktu usługi.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Współdziałanie z aplikacjami COM +](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Porady: Konfigurowanie ustawień usług COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
