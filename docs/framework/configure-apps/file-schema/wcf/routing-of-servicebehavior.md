---
title: <routing> dla <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397731"
---
# <a name="routing-of-servicebehavior"></a>\<routing> dla \<serviceBehavior>
Zapewnia dostęp do usługi routingu w czasie wykonywania w celu umożliwienia dynamicznej modyfikacji konfiguracji routingu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|filterTable|Ciąg określający nazwę tabeli routingu zawierającej filtry, które mają być oceniane przez usługę routingu. Ta wartość musi być zgodna z `name` atrybutem [\<filterTable>](filtertable.md) elementu w [\<filterTables>](filtertables.md) sekcji.|  
|routeOnHeaderOnly|Wartość logiczna określająca, czy filtr będzie przebadał zarówno treść komunikatu, jak i nagłówek, czy tylko nagłówek. Wartość domyślna to `true`.|  
|soapProcessingEnabled|Wartość logiczna określająca, czy należy wykonać przetwarzanie protokołu SOAP.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji włącza Routing dla usługi. Możesz określić rzeczywistą tabelę routingu, która ma być używana przez usługę w tym elemencie.  
  
 Za pomocą tej sekcji konfiguracji można zmienić ustawienia routingu na bieżąco po zmianie wzorca wdrożenia. W czasie wykonywania można zarejestrować własne rozszerzenie routingu z nowymi ustawieniami routingu, a usługa routingu rozpocznie korzystanie z zaktualizowanych informacji o konfiguracji dla nowych komunikatów i sesji, pozostawiając jednocześnie komunikaty/sesje w locie przy użyciu dowolnych reguł podczas ich uruchamiania.  Umożliwia to bezpieczne dla sesji ponowne odtwarzanie usługi routingu podczas środowiska uruchomieniowego.  
