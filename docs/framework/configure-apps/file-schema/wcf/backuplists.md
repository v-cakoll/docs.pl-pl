---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: b65cc4d04b5304e93b70509c9db3bc2248accb7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926435"
---
# <a name="backuplists"></a>\<backupLists >
Reprezentuje sekcję konfiguracji definiującą zestaw usług kopii zapasowych używanych w obsłudze błędów. Każdy element podrzędny to lista kopii zapasowych, która wylicza zestaw punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty. Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu automatycznie przejdzie w tryb failover do kolejnej listy.  Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności uczenia się aplikacji klienckiej, jak obsługiwać złożone wzorce lub wszystkie usługi są wdrażane.  
  
 \<system.serviceModel>  
\<> routingu  
\<backupLists >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](filter.md)|Zawiera listę punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty. .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> routingu](routing.md)|Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe Wysyłaj komunikaty do, gdy filtr jest zgodny.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
