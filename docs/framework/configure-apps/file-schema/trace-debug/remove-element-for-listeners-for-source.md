---
title: <remove> Element <listeners> dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4809c471deb51e0560b438b5a2c8849daad34ca0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120136"
---
# <a name="remove-element-for-listeners-for-source"></a>\<Usuń >, Element dla \<odbiorników > dla \<źródła >
Usuwa odbiornik z `Listeners` kolekcję dla źródła śledzenia.  
  
 \<Konfiguracja >  
\<system.diagnostics>  
\<źródła >  
\<source>  
\<listeners>  
\<remove>  
  
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
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.|  
|`source`|Określa źródło śledzenia, który inicjuje komunikatów śledzenia.|  
|`listeners`|Określa obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.|  
  
## <a name="remarks"></a>Uwagi  
 `<remove>` Elementu usuwa określony odbiornik z `Listeners` kolekcję dla źródła śledzenia.  
  
 Możesz usunąć element z `Listeners` kolekcję dla źródła śledzenia, programowo przez wywołanie metody <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metody <xref:System.Diagnostics.TraceSource.Listeners%2A> właściwość <xref:System.Diagnostics.TraceSource> wystąpienia.  
  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<remove>` element przed użyciem `<add>` elementu do dodania odbiornika `console` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)
- [Obiekty nasłuchujące śledzenia](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
