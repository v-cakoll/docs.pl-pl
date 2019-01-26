---
title: '&lt;Dodaj&gt; elementu &lt;przełączników&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 3b15cd7759eb36f95b93f2885151e2f6075d92d9
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083343"
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a>&lt;Dodaj&gt; elementu &lt;przełączników&gt;
Określa poziom, którego ustawiono przełącznikiem śledzenia.  
  
 \<Konfiguracja >  
\<system.diagnostics>  
\<przełączniki >  
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
|**Nazwa**|Atrybut wymagany.<br /><br /> Określa nazwę przełącznika. Wartość tego atrybutu odnosi się do *displayName* parametr, który jest przekazywany do konstruktora przełącznika.|  
|**value**|Atrybut wymagany.<br /><br /> Określa poziom przełącznika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`switches`|Zawiera przełączniki śledzenia i poziomu, gdzie są ustawione przełączniki śledzenia.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Aby zmienić poziom o przełącznikiem śledzenia, należy umieścić go w pliku konfiguracji. Jeśli przełącznik <xref:System.Diagnostics.BooleanSwitch>, możesz je włączyć lub wyłączyć. Jeśli przełącznik <xref:System.Diagnostics.TraceSwitch>można przypisać różne poziomy, aby określić typy śledzenia i debugowania komunikaty wyjściowe aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać  **\<Dodaj >** element, aby ustawić `General` przełącznikiem śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu i włączyć `Data` przełącznikiem logiczna śledzenia.  
  
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
- [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
