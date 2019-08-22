---
title: <disableCachingBindingFailures>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba74907e2f6fc2ca14e12a24113fa7654c9b967e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663799"
---
# <a name="disablecachingbindingfailures-element"></a>\<disableCachingBindingFailures, element >
Określa, czy należy wyłączyć buforowanie niepowodzeń powiązań, które wystąpiły, ponieważ nie można odnaleźć zestawu przez sondowanie.  
  
 \<> elementu konfiguracji  
\<Element > środowiska uruchomieniowego  
\<disableCachingBindingFailures >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|dostępny|Atrybut wymagany.<br /><br /> Określa, czy należy wyłączyć buforowanie niepowodzeń powiązań, które wystąpiły, ponieważ nie można odnaleźć zestawu przez sondowanie.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Nie należy wyłączać buforowania niepowodzeń powiązań, ponieważ zestaw nie został odnaleziony przez sondowanie. Jest to domyślne zachowanie dotyczące powiązań rozpoczynające się od .NET Framework w wersji 2,0.|  
|1|Wyłącz buforowanie niepowodzeń powiązań, ponieważ zestaw nie został odnaleziony przez sondowanie. To ustawienie przywraca zachowanie powiązania .NET Framework w wersji 1,1.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od .NET Framework w wersji 2,0, domyślnym zachowaniem ładowania zestawów jest buforowanie wszystkich błędów powiązań i ładowania. Oznacza to, że jeśli próba załadowania zestawu nie powiedzie się, kolejne żądania załadowania tego samego zestawu kończą się niepowodzeniem, bez próby zlokalizowania zestawu. Ten element wyłącza zachowanie domyślne dla niepowodzeń powiązań, które występują, ponieważ nie można odnaleźć zestawu w ścieżce sondowania. Te błędy są <xref:System.IO.FileNotFoundException>wyrzucane.  
  
 Ten element nie ma wpływ na pewne błędy powiązań i ładowania i są zawsze buforowane. Te błędy występują, ponieważ zestaw został znaleziony, ale nie można go załadować. Zgłaszają <xref:System.IO.FileLoadException>lub. <xref:System.BadImageFormatException> Poniższa lista zawiera kilka przykładów takich niepowodzeń.  
  
- Jeśli próba załadowania pliku nie jest prawidłowym zestawem, kolejne próby załadowania zestawu zakończą się niepowodzeniem, nawet jeśli zły plik zostanie zastąpiony właściwym zestawem.  
  
- W przypadku próby załadowania zestawu, który jest zablokowany przez system plików, kolejne próby załadowania zestawu zakończą się niepowodzeniem nawet po wydaniu zestawu przez system plików.  
  
- Jeśli co najmniej jedna wersja zestawu, który próbujesz załadować, znajduje się w ścieżce sondowania, ale określona wersja, której żądasz, nie należy do nich, kolejne próby załadowania tej wersji będą kończyć się niepowodzeniem, nawet jeśli poprawna wersja zostanie przeniesiona do ścieżki sondowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć buforowanie niepowodzeń powiązań zestawów, które występują, ponieważ nie znaleziono zestawu przez sondowanie.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../deployment/how-the-runtime-locates-assemblies.md)
