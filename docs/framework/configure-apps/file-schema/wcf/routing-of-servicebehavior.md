---
title: '&lt;routing&gt; w &lt;serviceBehavior&gt;'
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 5fb7febe365f73acf09ba74b07215fe9cc659efb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750755"
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a>&lt;routing&gt; w &lt;serviceBehavior&gt;
Udostępnia środowiska wykonawczego usługa routingu umożliwia dynamiczne modyfikacji konfigurację routingu.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<Routing >  
  
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
|filterTable|Ciąg określający nazwę tabeli routingu, która zawiera filtry, które ma zostać obliczone przez usługę routingu. Ta wartość musi być zgodna `name` atrybutu [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) sekcji.|  
|routeOnHeaderOnly|Wartość logiczna określająca, czy filtr zbada zarówno treści wiadomości i nagłówek lub tylko nagłówek. Wartość domyślna to `true`.|  
|soapProcessingEnabled|Wartość logiczna określająca, czy powinien wystąpić przetwarzania protokołu SOAP.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji umożliwia routingu dla usługi. Można określić rzeczywistego tabeli routingu do użycia przez usługę w tym elemencie.  
  
 Za pomocą tej sekcji konfiguracyjnej, można zmienić ustawienia routingu na bieżąco po zmianie deseniu wdrożenia. W czasie wykonywania można zarejestrować rozszerzenia routingu przy użyciu nowych ustawień routingu i usługi routingu rozpocznie się za pomocą zaktualizowanej konfiguracji informacji dla nowych wiadomości i sesji, pozostawiając locie wiadomości/sesji przy użyciu niezależnie od zasady zostały w miejsce, gdy zostały rozpoczęte.  Daje możliwość są bezpieczne dla sesji, bez odtworzenia ponownej konfiguracji usługi routingu podczas wykonywania.  
  
