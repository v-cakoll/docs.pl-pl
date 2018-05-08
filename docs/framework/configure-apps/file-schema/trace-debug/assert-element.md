---
title: '&lt;Assert&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ab1644d23e4d6d78b62e701902e5ec39e134b38b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltassertgt-element"></a>&lt;Assert&gt; — Element
Określa, czy wyświetlać okno komunikatu po wywołaniu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody; określa także nazwę pliku do zapisania komunikatów.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<Assert >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`assertuienabled`|Atrybut opcjonalny.<br /><br /> Określa, czy do wyświetlenia komunikatu dialogowe **Debug.Assert** daje w wyniku metody **false**.|  
|`logfilename`|Atrybut opcjonalny.<br /><br /> Określa nazwę pliku do zapisu, jeśli komunikat **Debug.Assert** daje w wyniku **false**.|  
  
## <a name="assertuienabled-attribute"></a>assertuienabled atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Wyświetla okno komunikatu. Domyślnie włączone.|  
|`false`|Nie są wyświetlane w oknie komunikatu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Oba atrybuty w  **\<assert >** elementu są opcjonalne. Pola komunikatów można wyłączyć bez określania pliku do zapisywania wiadomości, lub w przypadku określenia pliku do zapisu komunikaty podczas opuszczania komunikatu zaznaczone pola.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób Wyłącz wyświetlanie pola komunikatu podczas wywoływania **Debug.Assert** i zapisu wiadomości `c:\log.txt`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Debug>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
