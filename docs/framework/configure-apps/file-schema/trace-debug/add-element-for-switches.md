---
title: <add>, element dla <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 8fcd5cbe63a323a7509f5ff8c615364295c244d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920544"
---
# <a name="add-element-for-switches"></a>\<Dodaj element > dla \<przełączników >
Określa poziom, w którym jest ustawiony przełącznik śledzenia.  
  
 \<> konfiguracji  
\<system.diagnostics>  
\<Przełączniki >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**name**|Atrybut wymagany.<br /><br /> Określa nazwę przełącznika. Wartość tego atrybutu odpowiada parametrowi *DisplayName* , który jest przesyłany do konstruktora przełącznika.|  
|**value**|Atrybut wymagany.<br /><br /> Określa poziom przełącznika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`switches`|Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracji. Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, możesz go włączyć i wyłączyć. Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>, można przypisać do niego różne poziomy, aby określić typy komunikatów śledzenia lub debugowania, które są wyprowadzane przez aplikację.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak <xref:System.Diagnostics.TraceLevel> używać `Data` `General`  **\<elementu > Dodaj** , aby ustawić przełącznik śledzenia na poziomie i włączyć przełącznik logiczny śledzenia.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [Schemat ustawień śledzenia i debugowania](index.md)
