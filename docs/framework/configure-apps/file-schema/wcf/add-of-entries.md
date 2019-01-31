---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 7267b8719987ecd25bcca78a7897a0d4172a42ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264573"
---
# <a name="add-of-entries"></a>\<Dodaj > z \<wpisów >
Reprezentuje pozycji routingu, który jest mapowany punkt końcowy klienta, który został uprzednio zdefiniowany filtr. Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.  
  
 \<system.serviceModel>  
\<Routing >  
\<filterTables>  
\<filterTable>  
\<entries>  
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
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|backupList|Ciąg, który określa odwołanie do tworzenia kopii zapasowej listy punktów końcowych.|  
|endpoint|Ciąg określający odniesienie do klienta punkt końcowy, który będą wysyłane wiadomości, które są zgodne z filtrem określonym przez `filterName` atrybutu.|  
|filterName|Ciąg, który określa odwołanie do elementu filtru.|  
|priority|Liczba całkowita, która określa priorytet tego wpisu.<br /><br /> Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, używając najniższy priorytet 0. Wszystkie wpisy dla określonego priorytetu są obliczane jednocześnie, jeśli brak zgodności można odnaleźć wpisu dla Bieżący priorytet zostaną ocenione na następny poziom priorytetu.<br /><br /> Ta wartość jest opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Sekcja konfiguracji, który zawiera pozycje mapowania routingu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
