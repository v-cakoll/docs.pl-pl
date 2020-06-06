---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855309"
---
# \<exposedMethod>
Reprezentuje metodę COM+, która jest uwidaczniana, gdy interfejs składnika modelu COM+ jest udostępniany jako usługa sieci Web.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|name|Ciąg, który zawiera metodę COM+, która jest uwidaczniana, gdy interfejs składnika modelu COM+ jest ujawniony jako usługa sieci Web.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|Kolekcja [\<exposedMethod>](exposedmethod.md) elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Narzędzie konfiguracji integracji modelu COM+ (ComSvcConfig. exe) może służyć do dodawania określonych metod z interfejsu COM, które mają być wyświetlane w wygenerowanym kontrakcie usługi.  
  
 Na przykład można użyć poniższego polecenia, aby dodać trzy nazwane metody z `IFinances` interfejsu com na `ItemOrders` . Składnik finansowy do wygenerowanego kontraktu usługi.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Po uruchomieniu również programu ComSvcConfig. exe program generuje następujący kontrakt usługi z listą wymienionych wcześniej metod jako [\<exposedMethod>](exposedmethod.md) elementy.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 W czasie inicjalizacji usługi środowisko uruchomieniowe próbuje wygenerować kontrakt usługi przez odzwierciedlenie i dodanie tylko metod uwzględnionych na liście [\<exposedMethod>](exposedmethod.md) elementów. Ślad jest generowany dla każdej metody interfejsu, która nie jest uwzględniona w kontrakcie usługi.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [Integrowanie z aplikacjami COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Instrukcje: konfigurowanie ustawień usługi COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
