---
title: '&lt;loadFromRemoteSources&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acd66cdff9f2c68e7d665b1fd236b18eeb9b4bac
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadFromRemoteSources&gt; — Element
Określa, czy zestawy ze źródła zdalnego należy przyznać pełne zaufanie.  
  
> [!NOTE]
>  Jeśli były kierowane do tego tematu, z powodu komunikat o błędzie na liście błędów projektu programu Visual Studio lub błąd kompilacji, zobacz [porady: Użyj zestawu z sieci Web w programie Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
 \<Konfiguracja >  
\<runtime>  
\<loadFromRemoteSources >  
  
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
|`false`|Nie przyznać pełne zaufanie do aplikacji z zdalnych źródeł. Domyślnie włączone.|  
|`true`|Przyznać pełne zaufanie do aplikacji z zdalnych źródeł.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 .NET Framework w wersji 3.5 i wcześniejszymi wersjami Jeśli załadować zestawu z lokalizacji zdalnej, zestaw może działać częściowo zaufany za pomocą zestaw uprawnień, która była uzależniona od strefy, w której została załadowana. Na przykład jeśli zestaw jest ładowany z witryny internetowej, jego został załadowany w strefie Internet i przyznane zestaw uprawnień internetowych. Innymi słowy wykonane w piaskownicy Internet. Jeśli zostanie podjęta próba uruchomienia tego zestawu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszych wersjach, jest zgłaszany wyjątek; musi być jawnie tworzenia piaskownicy dla zestawu (zobacz [porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), lub uruchomić go w trybie pełnego zaufania.  
  
 `<loadFromRemoteSources>` Element umożliwia określenie, czy zestawy, które powinny zostać uruchomione częściowo zaufany w starszych wersjach programu .NET Framework są uruchamiane w pełni zaufane w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych wersjach. Domyślnie zdalne zestawy nie są uruchamiane w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych. Do uruchamiania zdalnego zestawu, należy uruchomić go jako w pełni zaufany lub Utwórz piaskownicy <xref:System.AppDomain> do uruchamiania go.  
  
> [!NOTE]
>  W [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], zestawy w udziałach sieci lokalnej są domyślnie uruchamiane przy pełnym zaufaniu; nie należy włączyć `<loadFromRemoteSources>` elementu.  
  
> [!NOTE]
>  Jeśli aplikacja został skopiowany z sieci web, jego oflagowane przez system Windows jako aplikacji sieci web, nawet wtedy, gdy znajduje się on na komputerze lokalnym. Określenie, że można zmienić, zmieniając właściwości pliku lub skorzystać z `<loadFromRemoteSources>` element, aby udzielić zestawu pełne zaufanie. Alternatywnie, można użyć <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metody można załadować zestawu lokalnego, który system operacyjny został oznaczony jako załadowanych z sieci web.  
  
 `enabled` Atrybutu dla tego elementu jest efektywne tylko wtedy, gdy zabezpieczenia dostępu kodu (CAS) jest wyłączona. Domyślnie urzędów certyfikacji zasad jest wyłączone w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych wersjach. Jeśli ustawisz `enabled` do `true`, zdalne aplikacje są udzielane pełne zaufanie.  
  
 Jeśli `<loadFromRemoteSources>` `enabled` nie jest ustawiony na `true`, jest zwracany wyjątek w następujących warunkach:  
  
-   Zachowanie sandboxing bieżącej domeny różni się od jego zachowanie w [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]. Wymaga to zasad CAS, które mają zostać wyłączone, a bieżąca domena nie powinien być w trybie piaskownicy.  
  
-   Trwa ładowanie zestawu nie pochodzi z `MyComputer` strefy.  
  
> [!NOTE]
>  Mogą wystąpić <xref:System.IO.FileLoadException> w aplikacji Windows Virtual PC podczas próby załadowania pliku z połączonego folderów na komputerze hostingu. Ten błąd może również wystąpić, gdy próbuje załadować plik z folderu połączone za pośrednictwem [usług pulpitu zdalnego](http://go.microsoft.com/fwlink/?LinkId=182775) (usług terminalowych). Aby zapobiec wyjątek, ustaw `enabled` do `true`.  
  
 Ustawienie `<loadFromRemoteSources>` elementu `true` uniemożliwia tego wyjątku z został zgłoszony. Umożliwia określenie, że użytkownik nie używają środowisko uruchomieniowe języka wspólnego do piaskownicy załadowanych zestawów zabezpieczeń i mogą być dozwolone do wykonania jako pełne zaufanie.  
  
> [!IMPORTANT]
>  Zestaw nie należy uruchamiać w trybie pełnego zaufania, nie należy ustawiać ten element konfiguracji. Zamiast tego utwórz piaskownicy <xref:System.AppDomain> w którym można załadować zestawu.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element jest zwykle używana w pliku konfiguracji aplikacji, ale mogą być używane w inne pliki konfiguracji, w zależności od kontekstu. Aby uzyskać więcej informacji, zobacz artykuł [więcej niejawne korzysta z zasad CAS: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) w blogu .NET zabezpieczeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można przyznać pełne zaufanie do aplikacji z zdalnych źródeł.  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Więcej niejawne używa zasad CAS: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [Porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
