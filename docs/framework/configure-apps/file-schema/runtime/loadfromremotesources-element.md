---
title: '&lt;loadfromremotesources —&gt; — Element'
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a8858059159edddb4456561719c572fb9268be7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484070"
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadfromremotesources —&gt; — element
Określa, czy zestawy, ładowane z zdalnych źródeł może być przyznany pełnego zaufania w programie .NET Framework 4 i nowszych.
  
> [!NOTE]
>  Jeśli były kierowane do tego tematu, ze względu na komunikat o błędzie na liście błędów projektu programu Visual Studio lub błąd kompilacji, zobacz [porady: Użyj zestawu z sieci Web w programie Visual Studio](https://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
 \<Konfiguracja >  
\<runtime>  
\<loadfromremotesources — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy zestaw, który jest ładowany ze źródła zdalnego należy przyznać pełne zaufanie.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie przyznawaj pełnego zaufania do aplikacji ze zdalnego źródła. Domyślnie włączone.|  
|`true`|Przyznać pełne zaufanie do aplikacji ze zdalnego źródła.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi

W .NET Framework 3.5 i wcześniejszymi wersjami Jeśli zestaw jest ładowany z lokalizacji zdalnej, kod w zestawie jest uruchamiany w częściowej relacji zaufania z zestaw uprawnień, który zależy od strefy, z której jest ładowany. Na przykład jeśli zestaw jest ładowany z witryny sieci Web, go jest ładowany do strefy Internet i przyznane Internet zestaw uprawnień. Innymi słowy wykonuje w piaskownicy Internet.

Począwszy od programu .NET Framework 4, zasady zabezpieczenia dostępu kodu jest wyłączona, a zestawy są ładowane w trybie pełnego zaufania. Zazwyczaj, to czy przyznać pełne zaufanie do zestawy, ładowane z <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodę, która wcześniej była piaskownicy. Aby temu zapobiec, możliwość uruchamiania kodu w zestawy, ładowane ze źródła zdalnego jest domyślnie wyłączona. Domyślnie, jeśli użytkownik podejmie próbę załadowania zestawu zdalnego <xref:System.IO.FileLoadException> z komunikatem o wyjątku, jak jest generowany, następujące czynności:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

Aby załadować zestaw i wykonywanie kodu, należy:

- Jawnie utworzyć piaskownicy dla zestawu (zobacz [porady: uruchamianie częściowo zaufanego kodu w piaskownicy](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).

- Uruchom kod zestawu w trybie pełnego zaufania. Możesz to zrobić, konfigurując `<loadFromRemoteSources>` elementu. Dzięki temu można określić, że zestawy, które działają w częściowej relacji zaufania we wcześniejszych wersjach programu .NET Framework jest teraz uruchomione w trybie pełnego zaufania w .NET Framework 4 i nowszych wersjach.

> [!IMPORTANT]
> Jeśli zestaw nie jest uruchamiany w trybie pełnego zaufania, ten element konfiguracji nie jest ustawiony. Zamiast tego utworzyć piaskownicy <xref:System.AppDomain> w którym można załadować zestawu.

`enabled` Atrybutu dla `<loadFromRemoteSources>` element jest efektywne tylko wtedy, gdy zabezpieczenia dostępu kodu (CAS) jest wyłączony. Domyślnie urzędy certyfikacji zasad jest wyłączona w .NET Framework 4 i nowszych wersjach. Jeśli ustawisz `enabled` do `true`, zdalne zespoły są udzielane pełne zaufanie.

Jeśli `enabled` nie jest ustawiony na `true`, <xref:System.IO.FileLoadException> jest zgłaszany w ramach jednej z następujących warunków:

- Zachowanie piaskownicy bieżącej domeny różni się od jego zachowanie w programie .NET Framework 3.5. Wymaga to urzędów certyfikacji zasad jest wyłączona, a bieżąca domena nie należy go w trybie piaskownicy.

- Nie jest ładowany zestaw `MyComputer` strefy.

Ustawienie `<loadFromRemoteSources>` elementu `true` zapobiega ten wyjątek z zgłaszane. Pozwala określić, że nie polegasz na środowisko uruchomieniowe języka wspólnego do izolowanego załadowanych zestawów dla zabezpieczeń i mogą być dozwolone do wykonania w pełne zaufanie.

## <a name="notes"></a>Uwagi

- W .NET Framework 4.5 i nowsze wersje zestawy w udziałach sieci lokalnej są uruchamiane w trybie pełnego zaufania domyślnie; nie trzeba włączyć `<loadFromRemoteSources>` elementu.

- Jeśli wniosek został skopiowany z sieci web, jego zostanie oflagowana przez Windows jako aplikacji sieci web, nawet wtedy, gdy znajduje się na komputerze lokalnym. Oznaczenie tego można zmienić, zmieniając jego właściwości pliku, lub możesz użyć `<loadFromRemoteSources>` elementu, aby przyznać zestawu pełne zaufanie. Alternatywnie, można użyć <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metodę, aby załadować zestaw lokalnego, który system operacyjny został oznaczony jako załadowaniu z sieci web.

- Możesz otrzymać <xref:System.IO.FileLoadException> w aplikacji, która działa w aplikacji Windows Virtual PC. Może to nastąpić podczas próby załadowania pliku z połączonych folderów na komputerze hostingu. Może również wystąpić podczas próby załadowania pliku z folderem połączone za pośrednictwem [usług pulpitu zdalnego](https://go.microsoft.com/fwlink/?LinkId=182775) (usług terminalowych). Aby zapobiec wyjątek, ustaw `enabled` do `true`.

## <a name="configuration-file"></a>Plik konfiguracji

Ten element jest zwykle używana w pliku konfiguracyjnym aplikacji, ale mogą być używane w inne pliki konfiguracji, w zależności od kontekstu. Aby uzyskać więcej informacji, zobacz artykuł [więcej niejawne korzysta z urzędów certyfikacji zasad: loadfromremotesources —](https://go.microsoft.com/fwlink/p/?LinkId=266839) w blogu dotyczącym zabezpieczeń .NET.  

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak udzielić pełnym zaufaniu zestawy, ładowane z zdalnych źródeł.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Zobacz także

[Więcej niejawne zastosowania zasady CAS: loadfromremotesources —](https://go.microsoft.com/fwlink/p/?LinkId=266839)  
[Porady: uruchamianie częściowo zaufanego kodu w piaskownicy](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
[Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
[Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
