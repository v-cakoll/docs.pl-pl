---
title: <add> dla <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 3052a7570d1d93836603454817be921b37d26060
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658836"
---
# <a name="add-of-entries"></a>\<Dodaj > \<wpisów >
Reprezentuje wpis routingu, który mapuje filtr do punktu końcowego klienta, który został wcześniej zdefiniowany. Komunikaty pasujące do tego filtru zostaną wysłane do tego miejsca docelowego.  
  
 \<system.serviceModel>  
\<> routingu  
\<filterTables >  
\<filterTable>  
\<> wpisów  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|backupList|Ciąg określający odwołanie do listy kopii zapasowych punktów końcowych.|  
|endpoint|Ciąg określający odwołanie do punktu końcowego klienta, który będzie odbierać komunikaty zgodne z filtrem określonym przez `filterName` atrybut.|  
|filterName|Ciąg określający odwołanie do elementu filtru.|  
|priority|Liczba całkowita, która określa priorytet tego wpisu.<br /><br /> Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, a wartość 0 to najniższy priorytet. Wszystkie wpisy o określonym priorytecie są oceniane jednocześnie, jeśli nie zostanie znaleziony pasujący wpis dla bieżącego priorytetu, zostanie obliczony następny poziom priorytetu.<br /><br /> Ta wartość jest opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> routingu](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Sekcja konfiguracji, która zawiera wpisy mapowania routingu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
