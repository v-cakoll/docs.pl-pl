---
title: '&lt;routing&gt; w &lt;serviceBehavior&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15e46f8d9550d4361ef92c1fa4860f17a2dfd088
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a>&lt;routing&gt; w &lt;serviceBehavior&gt;
Udostępnia środowiska wykonawczego usługa routingu umożliwia dynamiczne modyfikacji konfigurację routingu.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
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
  
