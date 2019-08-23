---
title: <assert>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 5ba781598542d271f41476b1a1e9d61faeb6ff74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927183"
---
# <a name="assert-element"></a>\<Element Assert >
Określa, czy podczas wywoływania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody ma być wyświetlane okno komunikatu, a także określa nazwę pliku, w którym mają zostać zapisane komunikaty.  
  
 \<> konfiguracji  
\<system.diagnostics>  
\<> potwierdzenia  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`assertuienabled`|Atrybut opcjonalny.<br /><br /> Określa, czy ma być wyświetlane okno komunikatu, gdy metoda **Debug. Assert** zwraca **wartość false**.|  
|`logfilename`|Atrybut opcjonalny.<br /><br /> Określa nazwę pliku, do którego ma zostać zapisany komunikat, jeśli **Debug. Assert** zwraca **wartość false**.|  
  
## <a name="assertuienabled-attribute"></a>AssertUiEnabled — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Wyświetla okno komunikatu. Domyślnie włączone.|  
|`false`|Nie wyświetla okna komunikatu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Oba atrybuty w  **\<elemencie Assert >** są opcjonalne. Można wyłączyć okna komunikatów bez określania pliku, w którym mają zostać zapisane komunikaty, lub można określić plik, do którego mają być zapisane komunikaty, pozostawiając pola komunikatów włączone.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć wyświetlanie okien komunikatów po wywołaniu **debugowania. Assert** i Zapisz wiadomości w `c:\log.txt`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Debug>
- [Schemat ustawień śledzenia i debugowania](index.md)
