---
title: '&lt;add&gt; w &lt;entries&gt;'
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: a6960c16c84c13d905f0993ee3cfc1cf67df07fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744983"
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;add&gt; w &lt;entries&gt;
Reprezentuje pozycji routingu mapowanego klienta punktu końcowego, który został uprzednio zdefiniowany filtr. Komunikatów spełniające warunki tego filtru będą wysyłane do tego miejsca docelowego.  
  
 \<system.serviceModel>  
\<Routing >  
\<routingTables >  
\<Tabela >  
\<wpisy >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|backupList|Ciąg, który określa odwołania do tworzenia kopii zapasowej listy punktów końcowych.|  
|endpoint|Ciąg określający odwołanie do punktu końcowego klienta, które będą otrzymywać wiadomości, zgodne z filtrem określonym przez `filterName` atrybutu.|  
|filterName|Ciąg określający odwołanie do elementu filtru.|  
|priorytet|Liczba całkowita określająca priorytet tego wpisu.<br /><br /> Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, używając 0 oznacza najniższy priorytet. Wszystkie wpisy dla priorytetu są oceniane jednocześnie, jeśli brak zgodności można odnaleźć wpisu dla Bieżący priorytet ocenia się na następny poziom priorytetu.<br /><br /> Ta wartość jest opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Routing >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Sekcja konfiguracyjna, zawierającą pozycje mapowania routingu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
