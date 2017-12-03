---
title: '&lt;add&gt; w &lt;entries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b01ad9e608fca669c28124cf5a68781d86058308
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;add&gt; w &lt;entries&gt;
Reprezentuje pozycji routingu mapowanego klienta punktu końcowego, który został uprzednio zdefiniowany filtr. Komunikatów spełniające warunki tego filtru będą wysyłane do tego miejsca docelowego.  
  
 \<system.serviceModel >  
\<Routing >  
\<routingTables >  
\<Tabela >  
\<wpisy >  
\<Dodaj >  
  
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
