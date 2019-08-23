---
title: <remove>Element dla <listeners> elementu<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920474"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<Usuń element > dla \<odbiorników \<> śledzenia >
Usuwa odbiornik z kolekcji **odbiorników** .  
  
 \<> konfiguracji  
\<system.diagnostics>  
\<> śledzenia  
\<> odbiorników  
\<remove>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**name**|Atrybut wymagany.<br /><br /> Nazwa odbiornika, który ma zostać usunięty z kolekcji **odbiorników** .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`listeners`|Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty. Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|`trace`|Konfiguruje usługę śledzenia ASP.NET.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>Usunięcie <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>z kolekcji powoduje zmianę zachowania metod,, i<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> . `Listeners` Wywołanie metody `Fail` <xref:System.Diagnostics.DefaultTraceListener> lub zwykle powoduje wyświetlenie okna komunikatu, ale okno komunikatu nie jest wyświetlane, jeśli nie znajduje się w `Listeners` kolekcji. `Assert`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak usunąć domyślny odbiornik śledzenia z kolekcji detektorów śledzenia .  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
