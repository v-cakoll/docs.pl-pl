---
title: <filter>Element dla <add> elementu<sharedListeners>
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
ms.openlocfilehash: 571a3add232f3e4f9747040dc104b85e8cc3085e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920511"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<Filtr > elementu do \<dodania > dla \<sharedListeners >
Dodaje filtr do odbiornika w `sharedListeners` kolekcji.  
  
 \<> konfiguracji  
\<system.diagnostics>  
\<sharedListeners, element >  
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
|**type**|Atrybut wymagany.<br /><br /> Określa typ filtru. Można użyć tylko pełnej nazwy typu (w formacie <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości) lub użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie (w formacie <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> właściwości). Aby uzyskać informacje na temat tworzenia w pełni kwalifikowanej nazwy typu, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Atrybut opcjonalny.<br /><br /> Ciąg przesłany do konstruktora dla określonej klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|`sharedListeners`|Kolekcja detektorów, które mogą odwoływać się do każdego elementu źródłowego lub śledzenia.|  
|`add`|Dodaje odbiornik do kolekcji **sharedListeners** .|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli odbiornik jest zdefiniowany `<add>` w elemencie `<sharedListeners>` elementu, filtr dla tego odbiornika `<filter>` powinien być zdefiniowany w elemencie, który jest elementem podrzędnym `<add>` elementu.  
  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, `<filter>` jak za pomocą elementu dodać filtr do odbiornika `console` śledzenia w `sharedListeners` kolekcji.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [Schemat ustawień śledzenia i debugowania](index.md)
