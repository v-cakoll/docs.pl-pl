---
title: <listeners>, element dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153376"
---
# <a name="listeners-element-for-trace"></a>\<słuchaczy> Element do \<śledzenia>
Określa odbiornik, który zbiera, przechowuje i kieruje wiadomości. Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<słuchacze>**

## <a name="syntax"></a>Składnia  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodaj>](add-element-for-listeners-for-trace.md)|Dodaje odbiornik do `Listeners` kolekcji.|  
|[\<wyraźne>](clear-element-for-listeners-for-trace.md)|Czyści `Listeners` kolekcję do śledzenia.|  
|[\<usuń>](remove-element-for-listeners-for-trace.md)|Usuwa odbiornik z kolekcji. `Listeners`|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa element główny sekcji konfiguracji ASP.NET.|  
|`trace`|Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 I <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> klasy współużytkuje tę samą kolekcję **odbiorników.** Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, druga klasa używa tego samego odbiornika. Klasy odbiornika dostarczane z .NET Framework pochodzą <xref:System.Diagnostics.TraceListener> z klasy.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak używać ** \<detektorów**>`MyListener` `MyEventListener` element, aby dodać odbiorników i **odbiorników** kolekcji. `MyListener`tworzy plik `MyListener.log` wywoływany i zapisuje dane wyjściowe do pliku. `MyEventListener`tworzy wpis w dzienniku zdarzeń.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
