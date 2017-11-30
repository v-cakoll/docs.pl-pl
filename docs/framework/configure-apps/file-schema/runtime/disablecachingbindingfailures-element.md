---
title: "&lt;disablecachingbindingfailures —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25d504afd7945718f08dd5f2bf92d7ea33037a11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a>&lt;disablecachingbindingfailures —&gt; — Element
Określa, czy wyłączyć buforowanie powiązanie błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie.  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<disablecachingbindingfailures — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|włączone|Atrybut wymagany.<br /><br /> Określa, czy wyłączyć buforowanie powiązanie błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Nie wyłączaj buforowanie powiązania błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie. Jest to domyślne zachowanie wiązania w programie .NET Framework w wersji 2.0.|  
|1|Wyłącz buforowanie powiązania błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie. To ustawienie umożliwia przywrócenie zachowania wiązania programu .NET Framework w wersji 1.1.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnym zachowaniem podczas ładowania zestawów w programie .NET Framework w wersji 2.0, jest w pamięci podręcznej wszystkie błędy ładowania i powiązania. Oznacza to jeśli próba załadowania zestawu nie powiedzie się, kolejnych żądań wysyłanych do załadowania tego samego zestawu nie bezpośrednio, bez próba zlokalizować zestawu. Ten element wyłącza to zachowanie domyślne dla powiązania błędów występujących, ponieważ nie można odnaleźć zestawu w ścieżce sondowania. Te błędy throw <xref:System.IO.FileNotFoundException>.  
  
 Niektóre powiązania błędy ładowania tego elementu nie podlegają i zawsze są buforowane. Te wystąpienia, ponieważ zestaw został znaleziony, ale nie można załadować. Generują one <xref:System.BadImageFormatException> lub <xref:System.IO.FileLoadException>. Poniższa lista zawiera kilka przykładów tych błędów.  
  
-   Jeśli próba załadowania pliku nie jest prawidłowym zestawem, kolejne próby ładowania zestawu zakończy się niepowodzeniem, nawet jeśli nieprawidłowego pliku jest zastępowany poprawny zestaw.  
  
-   Próba załadowania zestawu, który jest zablokowany przez system plików, kolejne próby ładowania zestawu zakończy się niepowodzeniem nawet po wydaniu zestaw przez system plików.  
  
-   Jeśli wersji co najmniej jednego zestawu, który próbujesz załadować znajduje się w ścieżce sondowania, ale żądanej wersji nie jest między nimi, kolejnych prób załadować tej wersji zakończy się niepowodzeniem, nawet jeśli poprawna wersja jest przenoszony do ścieżki próbkowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączenie buforowania zestawu powiązania błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Jak lokalizuje zestawów przez środowisko uruchomieniowe](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
