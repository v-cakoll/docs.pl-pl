---
title: '&lt;Filtr&gt; elementu &lt;dodać&gt; dla &lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3bbba1c805c6b300f7cf7b3d9112cde9df7607a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745058"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a>&lt;Filtr&gt; elementu &lt;dodać&gt; dla &lt;sharedListeners&gt;
Dodaje filtr do odbiornika w `sharedListeners` kolekcji.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<sharedListeners > — Element  
\<add>  
\<Filtr >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Typ**|Atrybut wymagany.<br /><br /> Określa typ filtru. Można użyć tylko pełną nazwę typu (w formacie <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości), lub w pełni kwalifikowana nazwa typu w tym informacje o zestawie można użyć (w formacie <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> właściwości). Aby uzyskać informacje na temat tworzenia w pełni kwalifikowana nazwa typu, zobacz [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData —**|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
|`sharedListeners`|Kolekcja obiektów nasłuchujących może odwoływać się wszystkie źródła lub element śledzenia.|  
|`add`|Dodaje odbiornika do **sharedListeners** kolekcji.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli odbiornik jest zdefiniowany w `<add>` elementu `<sharedListeners>` element powinien być zdefiniowany filtr dla tego odbiornika w `<filter>` element, który jest elementem podrzędnym `<add>` elementu.  
  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `<filter>` element, aby dodać filtr do obiektu nasłuchującego śledzenia `console` w `sharedListeners` kolekcji.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.TraceFilter>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceSource>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
