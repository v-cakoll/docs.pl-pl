---
title: <disableCachingBindingFailures> Element
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
ms.openlocfilehash: 23633cb282b8e59b4df4bcc2cd38717d805a207e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117495"
---
# <a name="disablecachingbindingfailures-element"></a>\<element > disableCachingBindingFailures
Określa, czy należy wyłączyć buforowanie niepowodzeń powiązań, które wystąpiły, ponieważ nie można odnaleźć zestawu przez sondowanie.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCachingBindingFailures >**  
  
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
 Począwszy od .NET Framework w wersji 2,0, domyślnym zachowaniem ładowania zestawów jest buforowanie wszystkich błędów powiązań i ładowania. Oznacza to, że jeśli próba załadowania zestawu nie powiedzie się, kolejne żądania załadowania tego samego zestawu kończą się niepowodzeniem, bez próby zlokalizowania zestawu. Ten element wyłącza zachowanie domyślne dla niepowodzeń powiązań, które występują, ponieważ nie można odnaleźć zestawu w ścieżce sondowania. Te błędy generują <xref:System.IO.FileNotFoundException>.  
  
 Ten element nie ma wpływ na pewne błędy powiązań i ładowania i są zawsze buforowane. Te błędy występują, ponieważ zestaw został znaleziony, ale nie można go załadować. Generują <xref:System.BadImageFormatException> lub <xref:System.IO.FileLoadException>. Poniższa lista zawiera kilka przykładów takich niepowodzeń.  
  
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
