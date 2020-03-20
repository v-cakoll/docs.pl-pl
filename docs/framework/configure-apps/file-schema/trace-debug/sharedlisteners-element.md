---
title: <sharedListeners>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153324"
---
# <a name="sharedlisteners-element"></a>\<SharedListeners> Element
Zawiera detektory, do których może odwoływać się dowolne źródło lub element śledzenia.  Te odbiorniki nie otrzymują żadnych śladów domyślnie i nie jest możliwe do pobrania tych odbiorników w czasie wykonywania. Detektory zidentyfikowane jako detektory udostępnione można dodać do źródeł lub śladów według nazwy.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodaj>](add-element-for-listeners-for-trace.md)|Dodaje odbiornik do `sharedListeners` kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`Configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa element główny sekcji konfiguracji ASP.NET.|  
  
## <a name="remarks"></a>Uwagi  
 Dodanie odbiornika do kolekcji odbiorników udostępnionych nie czyni go aktywnym odbiornikiem. Nadal musi być dodawany do źródła śledzenia lub `Listeners` śledzenia, dodając go do kolekcji dla tego elementu śledzenia. Klasy detektora w .NET Framework pochodzą <xref:System.Diagnostics.TraceListener> z klasy.  
  
 Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `<sharedListeners>` pokazano, jak użyć `console` elementu, aby dodać odbiornik do `Listeners` kolekcji dla <xref:System.Diagnostics.TraceSource> i <xref:System.Diagnostics.Trace> klas. Detektor śledzenia konsoli zapisuje informacje śledzenia do konsoli <xref:System.Diagnostics.TraceSource> za <xref:System.Diagnostics.Trace>pośrednictwem wywołań do jednego lub .  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
- [Obiekty nasłuchujące śledzenia](../../../debug-trace-profile/trace-listeners.md)
