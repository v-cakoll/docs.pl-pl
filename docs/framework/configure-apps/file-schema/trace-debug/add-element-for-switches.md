---
title: "&lt;Dodaj&gt; elementu &lt;przełączników&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de1acb37f3236598e9d8a74a188033d18b65ac8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a>&lt;Dodaj&gt; elementu &lt;przełączników&gt;
Określa poziom, gdy jest ustawiona przełącznik śledzenia.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<przełączniki >  
\<Dodaj >  
  
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
|**Nazwa**|Atrybut wymagany.<br /><br /> Określa nazwę tego przełącznika. Wartość tego atrybutu odpowiada *displayName* parametr przekazany do konstruktora przełącznika.|  
|**wartość**|Atrybut wymagany.<br /><br /> Określa poziom przełącznika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`switches`|Zawiera przełączniki śledzenia i poziom, gdzie są ustawione przełączniki śledzenia.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Aby zmienić poziom przełącznika śledzenia, należy umieścić go w pliku konfiguracji. Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, możesz ją włączyć lub wyłączyć. Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>można przypisać różne poziomy, aby określić typy śledzenia i debugowania komunikatów dane wyjściowe aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie  **\<Dodaj >** element, aby ustawić `General` przełącznika śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu, a następnie Włącz `Data` przełącznika logiczna śledzenia.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [Schemat ustawień debugowania i śledzenia](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
