---
title: '&lt;Usuń&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cc6772e7a9b98f09df21fd1acf24f578b66ae51e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754278"
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Usuń&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;
Usuwa odbiornik z `Listeners` kolekcji źródła śledzenia.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<źródeł >  
\<źródło >  
\<obiekty nasłuchujące >  
\<Usuń >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Atrybut wymagany.<br /><br /> Nazwa odbiornika do usunięcia z `Listeners` kolekcji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.|  
|`source`|Określa źródło śledzenia, który inicjuje śledzenia wiadomości.|  
|`listeners`|Określa nasłuchujących zbierania, przechowywania i kierowania wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 `<remove>` Element usuwa określony odbiornik z `Listeners` kolekcji źródła śledzenia.  
  
 Można usunąć elementu z `Listeners` kolekcji źródła śledzenia programowo przez wywołanie metody <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metoda <xref:System.Diagnostics.TraceSource.Listeners%2A> właściwość <xref:System.Diagnostics.TraceSource> wystąpienia.  
  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `<remove>` element, aby można było używać `<add>` elementu do dodania odbiornika `console` do `Listeners` kolekcji źródła śledzenia `TraceSourceApp`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [Obiekty nasłuchujące śledzenie](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
