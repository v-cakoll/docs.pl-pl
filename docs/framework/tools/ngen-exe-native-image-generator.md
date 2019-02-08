---
title: Ngen.exe (Generator obrazu natywnego)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d6550282f9a64912ec3306a3b898845e894d165
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827217"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (Generator obrazu natywnego)
Generator obrazów natywnych (Ngen.exe) jest narzędziem, które poprawia wydajność zarządzanych aplikacji. Program Ngen.exe tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy specyficzny dla procesora, i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.  
  
 Zmienia się na Ngen.exe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:  
  
-   Program Ngen.exe obecnie kompiluje zestawy w trybie pełnego zaufania, a zasady zabezpieczeń dostępu kodu (CAS) nie są już uwzględniane.  
  
-   Obrazy natywne generowane przez program Ngen.exe nie mogą już być ładowane do aplikacji, które działają w trybie częściowego zaufania.  
  
 Zmiany w programie Ngen.exe wprowadzone w programie .NET Framework w wersji 2.0:  
  
-   Instalacja zestawu powoduje także instalację jego zależności, co upraszcza składnię programu Ngen.exe.  
  
-   Obrazy natywne mogą być współużytkowane w różnych domenach aplikacji.  
  
-   Nowa akcja `update`, ponownie tworzy obrazy, które zostały unieważnione.  
  
-   Akcje mogą być odraczane w celu wykonania przez usługę, która korzysta z czasu bezczynności komputera, aby generować i instalować obrazy.  
  
-   Niektóre przyczyny unieważnienia obrazu zostały wyeliminowane.  
  
 W systemie Windows 8 zobacz [Native Image Task](#native-image-task).  
  
 Aby uzyskać dodatkowe informacje na temat korzystania z Ngen.exe i usługi obrazów natywnych, zobacz [Native Image Service](#native-image-service).  
  
> [!NOTE]
>  Składnia ngen.exe w wersjach 1.0 i 1.1 programu .NET Framework można znaleźć w [Native Image Generator (Ngen.exe) Legacy Syntax](https://msdn.microsoft.com/library/5a69fc7a-103f-4afc-8ab4-606adcb46324).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a>Akcje  
 W poniższej tabeli pokazano składnię każdego `action`. Opisy poszczególnych części `action`, zobacz [argumenty](#ArgumentTable), [poziomy priorytetów](#PriorityTable), [scenariuszy](#ScenarioTable), i [Config](#ConfigTable)tabel. [Opcje](#OptionTable) tabeli opisano `options` i przełączniki pomocy.  
  
|Akcja|Opis|  
|------------|-----------------|  
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|Generuje obrazy natywne dla zestawu i jego zależności, a także instaluje obrazy w pamięci podręcznej obrazów natywnych.<br /><br /> Jeśli `/queue` jest określona, akcja jest kolejkowana dla usługi obrazów natywnych. Domyślnym priorytetem jest 3. Zobacz [poziomy priorytetów](#PriorityTable) tabeli.|  
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Usuwa obrazy natywne zestawu i jego zależności z pamięci podręcznej obrazów natywnych.<br /><br /> Aby odinstalować pojedynczy obraz i jego zależności, należy użyć tych samych argumentów wiersza polecenia, które zostały użyte podczas instalacji obrazu. **Uwaga:**  Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Akcja `uninstall` * nie jest już obsługiwana.|  
|`update` [`/queue`]|Aktualizuje obrazy natywne, które stały się nieprawidłowe.<br /><br /> Jeśli `/queue` jest określony, aktualizacje są kolejkowane dla usługi obrazów natywnych. Aktualizacje są zawsze planowane z priorytetem 3, więc są uruchamiane, gdy komputer znajduje się w stanie bezczynności.|  
|`display` [`assemblyName` &#124; `assemblyPath`]|Wyświetla stan obrazów natywnych dla zestawu i jego zależności.<br /><br /> Jeśli nie zostaną dostarczone argumenty, będą wyświetlane wszystkie dane z pamięci podręcznej obrazów natywnych.|  
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> —lub—<br /><br /> `eqi` [1&#124;2&#124;3]|Wykonuje umieszczone w kolejce zadania kompilacji.<br /><br /> Jeśli określono priorytet, wykonywane są zadania kompilacji z większym lub równym priorytetem. Jeśli nie określono priorytetu, wykonywane są wszystkie skolejkowane zadania kompilacji.|  
|`queue` {`pause` &#124; `continue` &#124; `status`}|Wstrzymuje usługę obrazów natywnych, zezwala wstrzymanej usłudze na kontynuowanie działania lub bada stan usługi.|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a>Argumenty  
  
|Argument|Opis|  
|--------------|-----------------|  
|`assemblyName`|Pełna nazwa wyświetlana zestawu. Na przykład `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Uwaga:**  Można podać częściową nazwę zestawu, taką jak `myAssembly`, aby uzyskać `display` i `uninstall` akcji. <br /><br /> W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.|  
|`assemblyPath`|Jawna ścieżka zestawu. Można określić pełną lub względną ścieżkę.<br /><br /> Jeśli użytkownik określi nazwę pliku bez ścieżki, zestaw musi znajdować się w bieżącym katalogu.<br /><br /> W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a>Poziomy priorytetów  
  
|Priorytet|Opis|  
|--------------|-----------------|  
|`1`|Obrazy natywne są generowane i instalowane natychmiast, bez czekania na okres bezczynności.|  
|`2`|Obrazy natywne są generowane i instalowane bez czekania na okres bezczynności, ale po zakończeniu wszystkich akcji z priorytetem 1 (i ich zależności).|  
|`3`|Obrazy natywne są instalowane, gdy usługa obrazów natywnych wykryje, że komputer jest w stanie bezczynności. Zobacz [usługi obrazów natywnych](#native-image-service).|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a>Scenariusze  
  
|Scenariusz|Opis|  
|--------------|-----------------|  
|`/Debug`|Generuje obrazy natywne, których można używać w debugerze.|  
|`/Profile`|Generuje obrazy natywne, które mogą być używane w profilerze.|  
|`/NoDependencies`|Generuje minimalną liczbę obrazów natywnych wymaganą przez opcje określonego scenariusza.|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a>Konfiguracja  
  
|Konfiguracja|Opis|  
|-------------------|-----------------|  
|`/ExeConfig:``exePath`|Używa konfiguracji określonego zestawu wykonywalnego.<br /><br /> Program Ngen.exe musi podjąć te same decyzje, co moduł ładowania podczas tworzenia powiązania z zależnościami. Gdy współużytkowany składnik jest ładowany w czasie wykonywania, za pomocą <xref:System.Reflection.Assembly.Load%2A> metoda, pliku konfiguracji aplikacji określa zależności, które są ładowane dla współużytkowanego składnika — na przykład wersję zależności, który jest ładowany. `/ExeConfig` Przełącznik zapewnia Ngen.exe wskazówek, na którym zależności będą ładowane w czasie wykonywania.|  
|`/AppBase:``directoryPath`|Podczas lokalizowania zależności należy użyć określonego katalogu jako podstawy aplikacji.|  
  
<a name="OptionTable"></a>   
## <a name="options"></a>Opcje  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/nologo`|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|`/silent`|Pomija wyświetlanie komunikatów o sukcesie.|  
|`/verbose`|Wyświetla szczegółowe informacje na potrzeby debugowania. **Uwaga:**  Ze względu na ograniczenia systemu operacyjnego ta opcja nie wyświetla tak wielu dodatkowych informacji w systemach Windows 98 i Windows Millennium Edition.|  
|`/help`, `/?`|Wyświetla składnię polecenia i opcje dla aktualnego wydania.|  
  
## <a name="remarks"></a>Uwagi  
 Użytkownik musi mieć uprawnienia administracyjne, aby uruchomić program Ngen.exe.  
  
> [!CAUTION]
>  Nie należy uruchamiać programu Ngen.exe dla zestawów, które nie są w pełni zaufane. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]Ngen.exe kompiluje zestawy w trybie pełnego zaufania i zasady zabezpieczenia dostępu kodu nie są już uwzględniane.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obrazy natywne, które są generowane przez program Ngen.exe może nie już być ładowane do aplikacji, które działają w trybie częściowego zaufania. Zamiast tego wywoływany jest kompilator JIT (Just-In-Time).  
  
 Ngen.exe generuje obrazy natywne dla zestawu określonego przez `assemblyname` argument `install` akcji i wszystkich jego zależności. Zależności są ustalane na podstawie odwołań w manifeście zestawu. Jedyny scenariusz, w którym potrzebna jest oddzielna instalacja zależności jest, gdy aplikacja ładuje ją przy użyciu odbicia, na przykład przez wywołanie metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
> [!IMPORTANT]
>  Nie używaj <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody z obrazów natywnych. Obraz załadowany za pomocą tej metody nie może być używany przez inne zestawy w kontekście wykonywania.  
  
 Program Ngen.exe utrzymuje licznik zależności. Na przykład, załóżmy, że `MyAssembly.exe` i `YourAssembly.exe` są zainstalowane w pamięci podręcznej obrazów natywnych i mają odwołania do `OurDependency.dll`. Jeśli `MyAssembly.exe` zostanie odinstalowany, `OurDependency.dll` nie został odinstalowany. Jest on tylko usuwane podczas `YourAssembly.exe` również zostanie odinstalowany.  
  
 Jeśli jest generowany obraz natywny dla zestawu przechowywanego w globalnej pamięci podręcznej zestawów, należy określić jego nazwę wyświetlaną. Zobacz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.  
  
 Obrazy natywne, które generuje program Ngen.exe, mogą być współużytkowane w różnych domenach aplikacji. Oznacza to, że można używać programu Ngen.exe w scenariuszach aplikacji, które wymagają współużytkowania zestawów w różnych domenach aplikacji. Aby określić neutralność domeny:  
  
-   Zastosuj <xref:System.LoaderOptimizationAttribute> atrybutu do aplikacji.  
  
-   Ustaw <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> właściwość podczas tworzenia informacji Instalatora dla nowej domeny aplikacji.  
  
 Zawsze należy używać kodu neutralnego względem domeny podczas ładowania jego zestawu do wielu domen aplikacji. Jeśli obraz natywny zostanie załadowany do niewspółużytkowanej domeny aplikacji po załadowaniu do domeny współużytkowanej, nie będzie można go użyć.  
  
> [!NOTE]
>  Kod neutralny względem domeny nie może zostać zwolniony i wydajność może być nieco niższa, szczególnie w przypadku uzyskiwania dostępu do statycznych elementów członkowskich.  
  
 W tej sekcji uwag:  
  
-   [Generowanie obrazów dla różnych scenariuszy](#Scenarios)  
  
-   [Ustalanie, kiedy używać obrazów natywnych](#WhenToUse)  
  
    -   [Ulepszone wykorzystanie pamięci](#Memory)  
  
    -   [Szybsze uruchamianie aplikacji](#Startup)  
  
    -   [Podsumowanie zagadnień dotyczących użycia](#UsageSummary)  
  
-   [Ważność adresów podstawowych zestawu](#BaseAddresses)  
  
-   [Trwałe powiązania](#HardBinding)  
  
    -   [Określanie wskazówki powiązania dla zależności](#DependencyHint)  
  
    -   [Określanie domyślnej wskazówki powiązania dla zestawu](#AssemblyHint)  
  
-   [Przetwarzanie odroczone](#Deferred)  
  
-   [Obrazy natywne i kompilacja JIT](#JITCompilation)  
  
    -   [Nieprawidłowe obrazy](#InvalidImages)  
  
-   [Rozwiązywanie problemów](#Troubleshooting)  
  
    -   [Assembly Binding Log Viewer](#Fusion)  
  
    -   [Asystent debugowania zarządzanego JITCompilationStart](#MDA)  
  
    -   [Rezygnacja z generowanie obrazu natywnego](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a>Generowanie obrazów dla różnych scenariuszy  
 Po wygenerowaniu obrazu natywnego dla zestawu, środowisko uruchomieniowe automatycznie próbuje zlokalizować i używać tego obrazu macierzystego za każdym razem, których ono działa zestawu. W zależności od scenariuszy użycia można generować wiele obrazów.  
  
 Na przykład, jeśli zestaw zostanie uruchomiony w scenariuszu debugowania lub profilowania, środowisko uruchomieniowe szuka obrazu natywnego, który został wygenerowany za pomocą `/Debug` lub `/Profile` opcje. Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca standardową kompilację JIT. Jedynym sposobem debugowania obrazów natywnych jest utworzenie obrazu natywnego z użyciem `/Debug` opcji.  
  
 `uninstall` Akcji także rozpoznaje scenariusze, można więc odinstalować wszystkie lub tylko wybrane scenariusze.  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a>Ustalanie, kiedy używać obrazów natywnych  
 Obrazy natywne zapewniają poprawę wydajności w dwóch obszarach: ulepszone wykorzystanie pamięci i skrócenie czasu uruchamiania.  
  
> [!NOTE]
>  Wydajność obrazów natywnych zależy od kilku czynników, które utrudniają analizę, takich jak wzorce dostępu kodu i danych, liczba wywołań, jakie miały miejsce między granicami modułów, a także liczba zależności, które zostały już załadowane przez inne aplikacje. Jedynym sposobem ustalenia, czy obrazy natywne przynoszą korzyść aplikacji, są dokładne pomiary wydajności w kluczowych scenariuszach wdrażania.  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a>Ulepszone wykorzystanie pamięci  
 Obrazy natywne mogą znacznie poprawić wykorzystanie pamięci, gdy kod jest współużytkowany w różnych procesach. Obrazy natywne są plikami środowiska Windows PE, więc pojedyncza kopia pliku dll może być współużytkowana przez wiele procesów, natomiast kod natywny wytworzony przez kompilator JIT jest przechowywany w pamięci prywatnej i nie może być współużytkowany.  
  
 Aplikacje uruchamiane w ramach usług terminalowych również mogą korzystać z udostępnionych stron kodowych.  
  
 Ponadto rezygnacja z ładowania kompilatora JIT umożliwia oszczędzenie określonej ilości pamięci dla każdego wystąpienia aplikacji.  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a>Szybsze uruchamianie aplikacji  
 Wstępna kompilacja zestawów przy użyciu programu Ngen.exe może poprawić czas uruchamiania niektórych aplikacji. Ogólnie rzecz biorąc, współużytkowanie zestawów składnika przez aplikacje przynosi zyski, ponieważ po uruchomieniu pierwszej aplikacji składniki współużytkowane są już załadowane dla kolejnych aplikacji. Podczas zimnego uruchamiania nie występują takie zyski z wykorzystania obrazów natywnych, ponieważ każdy zestaw aplikacji musi zostać załadowany z dysku twardego, przez co czas dostępu do dysku twardego przeważa zyski ze współużytkowania.  
  
 Trwałe powiązania mogą wpływać na czas uruchamiania, ponieważ wszystkie obrazy trwale powiązane z głównym zestawem aplikacji muszą zostać załadowane w tym samym czasie.  
  
> [!NOTE]
>  Przed [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], należy umieścić składniki współużytkowane, o silnej nazwie w globalnej pamięci podręcznej, ponieważ moduł ładujący wykonywał dodatkową walidację silnie nazwanych zestawów, które są nie w globalnej pamięci podręcznej zestawów, efektywnie eliminując poprawę w czasie w przypadku uruchamiania uzyskaną dzięki obrazom natywnym. Optymalizacje, które zostały wprowadzone w [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] usunięte dodatkową walidację.  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a>Podsumowanie zagadnień dotyczących użycia  
 Następujące zagadnienia ogólne i dotyczące aplikacji mogą pomóc zadecydować, czy warto używać obrazów natywnych dla swojej aplikacji:  
  
-   Obrazy natywne są ładowane szybciej niż pliki MSIL, ponieważ eliminują potrzebę wykonywania wielu działań podczas uruchamiania, takich jak kompilacja JIT i weryfikacja bezpieczeństwa typów.  
  
-   Obrazy natywne wymagają mniejszego początkowego zestawu roboczego, ponieważ nie ma potrzeby wczytywania kompilatora JIT.  
  
-   Obrazy natywne umożliwiają współużytkowanie kodu przez różne procesy.  
  
-   Obrazy natywne wymagają więcej miejsca na dysku twardym niż zestawy MSIL, a ich generowanie może długo trwać.  
  
-   Obrazy natywne muszą być obsługiwane.  
  
    -   Obrazy muszą być generowane ponownie, gdy oryginalny zestaw lub jedna z jego zależności jest zmieniana.  
  
    -   Pojedynczy zestaw może wymagać wielu obrazów natywnych, aby można było używać go w różnych aplikacjach lub scenariuszach. Na przykład informacje o konfiguracji w dwóch aplikacjach mogą powodować różne decyzje dotyczące powiązań dla tego samego zestawu zależnego.  
  
    -   Obrazy natywne muszą być generowane przez administratora, czyli za pomocą konta systemu Windows z grupy Administratorzy.  
  
 Podczas określania, czy obrazy natywne mogą spowodować poprawę wydajności, oprócz tych ogólnych zagadnień, należy też rozważyć naturę aplikacji.  
  
-   Jeśli aplikacja działa w środowisku, w którym jest używanych wiele współużytkowanych składników, obrazy natywne umożliwią współużytkowanie składników przez wiele procesów.  
  
-   Jeśli aplikacja używa wielu domen aplikacji, obrazy natywne umożliwią współużytkowanie stron kodu w różnych domenach.  
  
    > [!NOTE]
    >  W wersjach 1.0 i 1.1 programu .NET Framework obrazów natywnych nie można współużytkować w różnych domenach aplikacji. Inaczej jest w wersji 2.0 i późniejszych.  
  
-   Jeśli aplikacja będzie uruchamiana na serwerze terminali, obrazy natywne umożliwią współużytkowanie stron kodu.  
  
-   Zazwyczaj korzystne jest kompilowanie do obrazów natywnych dużych aplikacji. Taka kompilacja małych aplikacje zazwyczaj nie przynosi korzyści.  
  
-   W przypadku aplikacji działających przez długi czas kompilacja JIT w czasie wykonywania sprawdza się nieco lepiej niż obrazy natywne. (Trwałe powiązania mogą do pewnego stopnia złagodzić różnicę w wydajności).  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a>Ważność adresów podstawowych zestawu  
 Obrazy natywne są plikami środowiska Windows PE, więc dotyczą ich te same problemy zmiany podstawy, co innych plików wykonywalnych. Spadek wydajności przy relokacji jest jeszcze bardziej widoczny, jeśli są stosowane powiązania trwałe.  
  
 Aby ustawić adres podstawowy dla obrazu natywnego, należy użyć odpowiedniej opcji kompilatora, aby ustawić adres podstawowy dla zestawu. Program Ngen.exe używa tego adresu podstawowego dla obrazu natywnego.  
  
> [!NOTE]
>  Obrazy natywne są większe niż zestawy zarządzane, na podstawie których zostały utworzone. Adresy podstawowe muszą być obliczane tak, aby zezwalały na te większe rozmiary.  
  
 Można użyć narzędzia, takiego jak dumpbin.exe, aby wyświetlić preferowany adres podstawowy obrazu natywnego.  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a>Trwałe powiązania  
 Trwałe powiązania zwiększają przepustowość i zmniejszają rozmiar zestawu roboczego dla obrazów natywnych. Wadą trwałych powiązań jest fakt, że wszystkie obrazy, które są trwale powiązane z zestawem, muszą być ładowane razem z zestawem. Może to znacznie zwiększyć czas uruchamiania dużych aplikacji.  
  
 Trwałe powiązanie jest odpowiednie dla zależności, które są ładowane we wszystkich krytycznych pod względem wydajności scenariuszach aplikacji. Podobnie jak w przypadku każdego aspektu wykorzystania obrazu natywnego, staranne wykonywanie pomiarów wydajności jest jedynym sposobem ustalenia, czy trwałe powiązanie zwiększa wydajność aplikacji.  
  
 <xref:System.Runtime.CompilerServices.DependencyAttribute> i <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> atrybutów umożliwiają dostarczenie wskazówek dotyczących trwałego powiązania do Ngen.exe.  
  
> [!NOTE]
>  Te atrybuty są wskazówkami dla programu Ngen.exe, a nie poleceniami. Użycie ich nie gwarantuje uzyskania trwałego powiązania. Znaczenie tych atrybutów może się zmieniać w przyszłych wersjach.  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a>Określanie wskazówki powiązania dla zależności  
 Zastosuj <xref:System.Runtime.CompilerServices.DependencyAttribute> do zestawu, aby określić prawdopodobieństwo, że określona zależność zostanie załadowana. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> Wskazuje, że trwałe powiązanie jest właściwe, <xref:System.Runtime.CompilerServices.LoadHint.Default> wskazuje, że powinny być używane domyślne dla zależności, i <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> wskazuje, że trwałe powiązanie jest właściwe.  
  
 Poniższy kod pokazuje atrybuty dla zestawu mającego dwie zależności. Pierwsza zależność (Assembly1) jest odpowiednim kandydatem dla trwałego powiązania, ale druga zależność (Assembly2) nie jest.  
  
```vb  
Imports System.Runtime.CompilerServices  
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>  
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>  
```  
  
```csharp  
using System.Runtime.CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]  
```  
  
```cpp  
using namespace System::Runtime::CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];  
```  
  
 Nazwa zestawu nie zawiera rozszerzenia nazwy pliku. Można używać nazw wyświetlanych.  
  
<a name="AssemblyHint"></a>   
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Określanie domyślnej wskazówki powiązania dla zestawu  
 Domyślne wskazówki powiązania potrzebne są tylko zestawom, które będą stosowane natychmiastowo i często przez dowolną aplikację, która jest od nich zależna. Zastosuj <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> z <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> do takich zestawów, aby określić, że trwałe powiązanie powinny być używane.  
  
> [!NOTE]
>  Nie ma powodu do zastosowania <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> do zestawów dll, które nie należą do tej kategorii, ponieważ stosowanie tego atrybutu z dowolną wartością w innych niż <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> ma taki sam skutek jak Niezastosowanie atrybut wcale.  
  
 Firma Microsoft używa <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> do określenia, że trwałe powiązanie jest domyślne dla bardzo niewielkiej liczby zestawów w programie .NET Framework, takich jak mscorlib.dll.  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a>Przetwarzanie odroczone  
 Generowanie obrazów natywnych dla bardzo dużych aplikacji może zająć znaczną ilość czasu. Podobnie zmiany składnika współużytkowanego lub zmiany w ustawieniach komputera mogą wymagać aktualizacji wielu obrazów natywnych. `install` i `update` akcji ma `/queue` opcja, która kolejkuje operację w celu odroczonego wykonania przez usługę obrazów natywnych. Ponadto program Ngen.exe ma `queue` i `executeQueuedItems` akcje, które zapewniają kontrolę nad usługą. Aby uzyskać więcej informacji, zobacz [Native Image Service](#native-image-service).  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a>Obrazy natywne i kompilacja JIT  
 Jeśli program Ngen.exe napotka w zestawie jakiekolwiek metody, których nie może wygenerować, wyklucza je z obrazu natywnego. Gdy środowisko uruchomieniowe wykonuje zestaw, przywraca kompilację JIT dla metod, które nie zostały uwzględnione w obrazie natywnym.  
  
 Ponadto obrazy natywne nie są używane, jeśli zestaw został uaktualniony lub jeśli obraz został unieważniony z jakiegokolwiek powodu.  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a>Nieprawidłowe obrazy  
 Użycie programu Ngen.exe w celu utworzenia obrazu natywnego zestawu powoduje, że dane wyjściowe zależą od opcji wiersza polecenia, które można określić, i niektórych ustawień na komputerze. Są to m.in. następujące ustawienia:  
  
-   Wersja programu .NET Framework.  
  
-   Wersja systemu operacyjnego, jeśli zmiana następuje z systemów operacyjnych z rodziny Windows 9 x na rodzinę Windows NT.  
  
-   Dokładna tożsamość zestawu (ponowna kompilacja zmienia tożsamość).  
  
-   Dokładna tożsamość wszystkich zestawów, do których odwołuje się zestaw (ponowna kompilacja zmienia tożsamość).  
  
-   Czynniki związane z zabezpieczeniami.  
  
 Program Ngen.exe rejestruje te informacje podczas generowania obrazu natywnego. Podczas wykonywania zestawu środowisko uruchomieniowe poszukuje obrazu natywnego wygenerowanego z użyciem opcji i ustawień, które odpowiadają bieżącemu środowisku komputera. Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca kompilację JIT zestawu. Następujące zmiany w ustawieniach komputera i środowiska powodują, że obrazy natywne stają się nieprawidłowe:  
  
-   Wersja programu .NET Framework.  
  
     Jeśli zastosowano aktualizację programu .NET Framework, wszystkie obrazy natywne utworzone przy użyciu programu Ngen.exe stają się nieprawidłowe. Z tego powodu, wykonaj wszystkie aktualizacje programu .NET Framework `Ngen Update` polecenie, aby upewnić się, że wszystkie obrazy natywne są generowane. Program .NET Framework automatycznie tworzy nowe obrazy natywne dla bibliotek programu .NET Framework, które instaluje.  
  
-   Wersja systemu operacyjnego, jeśli zmiana następuje z systemów operacyjnych z rodziny Windows 9 x na rodzinę Windows NT.  
  
     Na przykład jeśli wersja systemu operacyjnego działającego na komputerze zmienia się z Windows 98 Windows XP, wszystkie obrazy natywne przechowywane w pamięci podręcznej obrazów natywnych stają się nieprawidłowe. Jednakże jeśli system operacyjny zmieni się z Windows 2000 Windows XP, obrazy nie są unieważniane.  
  
-   Dokładna tożsamość zestawu.  
  
     Jeśli zestaw zostanie ponownie skompilowany, obraz natywny odpowiadający zestawowi staje się nieprawidłowy.  
  
-   Dokładna tożsamość jakichkolwiek zestawów, do których odwołuje się zestaw.  
  
     Jeżeli zestaw zarządzany zostanie zaktualizowany, wszystkie obrazy natywne zależne bezpośrednio lub pośrednio od tego zestawu stają się nieprawidłowe i muszą zostać wygenerowane ponownie. Obejmuje to zarówno zwykłe odwołania, jak i trwale powiązane zależności. Po każdym zastosowaniu aktualizacji oprogramowania program instalacyjny powinien wykonać `Ngen Update` polecenie, aby zagwarantować ponowne wygenerowanie wszystkich zależnych obrazów natywnych.  
  
-   Czynniki związane z zabezpieczeniami.  
  
     Zmiana zasad zabezpieczeń komputera ograniczająca uprawnienia udzielone uprzednio zestawowi może spowodować, że poprzednio skompilowane obrazy natywne dla tego zestawu staną się nieprawidłowe.  
  
     Aby uzyskać szczegółowe informacje dotyczące sposobu środowiska uruchomieniowego języka wspólnego administruje zabezpieczeniami dostępu kodu i sposobu używania uprawnień, zobacz [zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md).  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Następujące tematy dotyczące rozwiązywania problemów pozwala zobaczyć które obrazy natywne są używane i nie można używać przez aplikację, aby określić, kiedy kompilator JIT zaczyna kompilować metody i pokazuje, jak zrezygnować z tworzenia obrazu natywnego określony metody.  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a>podgląd dziennika powiązań zestawów  
 Aby upewnić się, że obrazy natywne są używane przez aplikację, możesz użyć [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md). Wybierz **obrazy natywne** w **kategorie dziennika** pola w oknie Podgląd dziennika powiązań. Program Fuslogvw.exe dostarcza informacje o tym, dlaczego obraz natywny został odrzucony.  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>Asystent debugowania zarządzanego JITCompilationStart  
 Możesz użyć [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) zarządzanego Asystenta debugowania (MDA), aby określić, kiedy kompilator JIT zaczyna kompilować funkcję.  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a>Rezygnacja z generowanie obrazu natywnego  
 W niektórych przypadkach program NGen.exe mogą mieć trudności generowania, który obraz natywny dla określonej metody lub możesz lepiej, że metoda być skompilowana w trybie JIT zamiast następnie kompilowane do obrazów natywnych. W takim przypadku można użyć `System.Runtime.BypassNGenAttribute` atrybutu, aby uniemożliwić NGen.exe generuje obraz natywny dla konkretnych metod. Ten atrybut musi stosowane osobno do każdej metody kod, którego nie chcesz dołączyć do obrazu natywnego. NGen.exe rozpoznaje atrybut i nie generuje kodu, obrazów natywnych dla odpowiedniej metody.  
  
 Zauważ, że `BypassNGenAttribute` nie jest zdefiniowana jako typ w bibliotece klas programu .NET Framework. Aby można było korzystać z atrybutu w kodzie, należy najpierw zdefiniować go w następujący sposób:  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 Można użyć atrybutu na podstawie-method. Poniższy przykład powoduje, że Generator obrazu natywnego, nie powinna generować obraz natywny dla `ExampleClass.ToJITCompile` metody.  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje obraz natywny dla `ClientApp.exe`, znajduje się w bieżącym katalogu i instaluje obraz w pamięci podręcznej obrazów natywnych. Jeśli istnieje plik konfiguracji zestawu, program Ngen.exe go użyje. Ponadto obrazy natywne są generowane dla wszystkich plików dll, `ClientApp.exe` odwołania.  
  
```  
ngen install ClientApp.exe  
```  
  
 Obraz instalowany za pomocą programu Ngen.exe jest również nazywany elementem głównym. Elementem głównym może być aplikacja albo składnik współużytkowany.  
  
 Następujące polecenie generuje obraz natywny dla `MyAssembly.exe` z określoną ścieżką.  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 Podczas lokalizowania zestawów i ich zależności program Ngen.exe używa tej samej logiki badania, co środowisko uruchomieniowe języka wspólnego (CLR). Domyślnie katalog, który zawiera `ClientApp.exe` jest używany jako katalog podstawowy aplikacji i wszelkie badania zestawów rozpoczynają się w tym katalogu. To zachowanie można zastąpić za pomocą `/AppBase` opcji.  
  
> [!NOTE]
>  Zachowanie to różni się od zachowania programu Ngen.exe w wersjach 1.0 i 1.1 programu .NET Framework, gdzie podstawa aplikacji znajduje się w bieżącym katalogu.  
  
 Zestaw może mieć zależność bez odwołania, na przykład jeśli ładuje plik dll za pomocą <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Można utworzyć obraz natywny dla takiego pliku dll, przy użyciu informacji o konfiguracji dla zestawu aplikacji `/ExeConfig` opcji. Następujące polecenie generuje obraz natywny dla `MyLib.dll,` używając informacji konfiguracyjnych z `MyApp.exe`.  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 Zestawy instalowane w ten sposób nie są usuwane, gdy jest usuwana aplikacja.  
  
 Aby odinstalować zależność, należy użyć tych samych opcji wiersza polecenia, które zostały użyte podczas jej instalowania. Poniższe polecenie odinstalowuje `MyLib.dll` z poprzedniego przykładu.  
  
```  
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 Aby utworzyć obraz natywny dla zestawu w globalnej pamięci podręcznej zestawów, należy użyć nazwy wyświetlanej zestawu. Na przykład:  
  
```  
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
```  
  
 Program NGen.exe generuje oddzielny zestaw obrazów dla każdego instalowanego scenariusza. Na przykład poniższe polecenia instalują kompletny zestaw obrazów natywnych dla normalnych operacji, drugi kompletny zestaw na potrzeby debugowania i trzeci na potrzeby profilowania:  
  
```  
ngen install MyApp.exe  
ngen install MyApp.exe /debug  
ngen install MyApp.exe /profile  
```  
  
### <a name="displaying-the-native-image-cache"></a>Wyświetlanie pamięci podręcznej obrazów natywnych  
 Obrazy natywne zainstalowane w pamięci podręcznej można wyświetlić przy użyciu programu Ngen.exe. Poniższe polecenie wyświetla wszystkie obrazy natywne znajdujące się w pamięci podręcznej obrazów natywnych.  
  
```  
ngen display  
```  
  
 `display` Lista akcji wszystkie zestawy główne, a następnie listę obrazów natywnych na komputerze.  
  
 Prosta nazwa zestawu służy do wyświetlania informacji dotyczących tylko tego zestawu. Następujące polecenie wyświetla wszystkie obrazy natywne w pamięci podręcznej obrazów natywnych, które pasują do nazwy częściowej `MyAssembly`, ich zależności, a wszystkie elementy główne, które są zależne od `MyAssembly`:  
  
```  
ngen display MyAssembly  
```  
  
 Wiedząc, które elementy główne są zależne od zestawu współużytkowanego składnika są przydatne do oceny wpływu `update` akcji po uaktualnieniu składnika współużytkowanego.  
  
 Aby określić rozszerzenie pliku zestawu, należy określić ścieżkę lub wykonać program Ngen.exe z katalogu zawierającego zestaw:  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 Następujące polecenie wyświetla wszystkie obrazy natywne w pamięci podręcznej obrazów natywnych o nazwie `MyAssembly` i wersji 1.0.0.0.  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a>Aktualizacja obrazów  
 Obrazy są zazwyczaj aktualizowane po uaktualnieniu składnika współużytkowanego. Aby zaktualizować wszystkie obrazy natywne, które zostały zmienione lub których zależności się zmieniły, należy użyć `update` akcji bez argumentów.  
  
```  
ngen update  
```  
  
 Aktualizacja wszystkich obrazów może być długotrwałym procesem. Można kolejkować aktualizacje do wykonania przez usługę obrazów natywnych przy użyciu `/queue` opcji. Aby uzyskać więcej informacji na temat `/queue` priorytetów instalacji i opcji, zobacz [Native Image Service](#native-image-service).  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a>Odinstalowywanie obrazów  
 Program Ngen.exe utrzymuje listę zależności, aby składniki współużytkowane były usuwane tylko wtedy, gdy wszystkie zestawy, które od nich zależą, zostały usunięte. Ponadto współużytkowany składnik nie zostanie usunięty, jeśli został zainstalowany jako element główny.  
  
 Poniższe polecenie Odinstalowuje wszystkie scenariusze dla głównego `ClientApp.exe`:  
  
```  
ngen uninstall ClientApp  
```  
  
 `uninstall` Akcji może służyć do usunięcia konkretnych scenariuszy. Poniższe polecenie Odinstalowuje wszystkie scenariusze debugowania `ClientApp.exe`:  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  Odinstalowywanie `/debug` scenariuszy nie powoduje odinstalowania scenariusza, który zawiera oba `/profile` i `/debug.`  
  
 Poniższe polecenie Odinstalowuje wszystkie scenariusze dla określonej wersji `ClientApp.exe`:  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 Poniższe polecenia odinstalowują wszystkie scenariusze dla `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` lub po prostu scenariusz debugowania dla tego zestawu:  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 Podobnie jak w przypadku `install` akcji, dostarczenie rozszerzenia wymaga wykonywania Ngen.exe z katalogu zawierającego zestaw lub określenia pełnej ścieżki.  
  
 Przykłady dotyczące usługi obrazów natywnych, zobacz [Native Image Service](#native-image-service).  
  
## <a name="native-image-task"></a>Obraz macierzysty — zadanie  
 Obraz macierzysty — zadanie jest zadaniem Windows, który generuje i przechowuje obrazy natywne. Obraz macierzysty — zadanie generuje i odzyskuje obrazów natywnych automatycznie dla obsługiwanych scenariuszach. (Zobacz [tworzenie obrazów natywnych](https://msdn.microsoft.com/library/2bc8b678-dd8d-4742-ad82-319e9bf52418).) Umożliwia ona także instalatorów do użycia [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) do tworzenia i aktualizowania obrazy natywne odroczonego naraz.  
  
 Obraz macierzysty — zadanie jest zarejestrowany, gdy dla każdego Procesora architektura obsługiwana na komputerze, aby umożliwić kompilację dla aplikacji przeznaczonych każdej architektury:  
  
|Nazwa zadania|komputer 32-bitowy|komputer 64-bitowy|  
|---------------|----------------------|----------------------|  
|NET Framework NGEN 4.0.30319|Tak|Tak|  
|NET Framework NGEN 4.0.30319 64|Nie|Tak|  
  
 Obraz macierzysty — zadanie jest dostępna w .NET Framework 4.5 i nowsze wersje, gdy uruchomiony w systemie Windows 8 lub nowszym. We wcześniejszych wersjach systemu Windows, .NET Framework używa [Native Image Service](#native-image-service).  
  
### <a name="task-lifetime"></a>Okres istnienia zadania  
 Ogólnie rzecz biorąc harmonogram zadań Windows uruchamia zadanie obrazu natywnego, każdej nocy, gdy komputer jest w stanie bezczynności. Zadanie sprawdza, czy wszelkie prace odroczonego umieszczonych w kolejce przez programy instalacyjne aplikacji, wszystkie żądania aktualizacji odroczonego obrazu natywnego i wszystkich operacji tworzenia automatycznych obrazu. Zadanie kończy zaległych elementów pracy i zamknięcie. Jeśli komputer nie jest bezczynny, gdy zadanie jest uruchomione, zatrzymuje zadanie.  
  
 Można także uruchomić obraz macierzysty — zadanie ręcznie za pośrednictwem interfejsu użytkownika harmonogramu zadań lub ręcznego wywołania do NGen.exe. Jeśli zadanie zostało uruchomione przy użyciu jednej z tych metod, będzie nadal uruchomione, gdy nie jest już jest w stanie bezczynności. Obrazy utworzone ręcznie przy użyciu NGen.exe są uszeregowane według priorytetów umożliwia zachowanie przewidywalne dla programów instalacyjnych aplikacji.  
  
## <a name="native-image-service"></a>Usługa obrazu macierzystego  
 Usługa obrazów natywnych jest usługa Windows, który generuje i przechowuje obrazy natywne. Usługa obrazów natywnych umożliwia deweloperowi odroczenie instalacji i aktualizacji obrazów natywnych na okresy, gdy komputer jest w stanie bezczynności.  
  
 Zazwyczaj usługa obrazów natywnych jest inicjowane przez program instalacyjny (Instalator) dla aplikacji lub aktualizacji. Dla akcji z priorytetem 3 usługa była wykonywana w czasie bezczynności na komputerze. Usługa zapisuje swój stan i jest w stanie kontynuować przez wiele ponownego uruchomienia, jeśli to konieczne. Wiele kompilacji obrazu można umieścić w kolejce.  
  
 Usługa również współdziała z ręcznego polecenia Ngen.exe. Ręczne polecenia mają pierwszeństwo przed aktywności w tle.  
  
> [!NOTE]
>  Windows Vista, nazwa jest wyświetlana na dla usługi obrazów natywnych "v2.0.50727_X86 NGEN Microsoft.NET Framework" lub "v2.0.50727_X64 NGEN Microsoft.NET Framework". We wszystkich wcześniejszych wersjach systemu Microsoft Windows nazwa jest "V2.0.50727_X86 usługi optymalizacji środowiska uruchomieniowego .NET" lub "Usługi optymalizacji środowiska uruchomieniowego .NET v2.0.50727_X64".  
  
### <a name="launching-deferred-operations"></a>Uruchamianie operacji odroczone  
 Przed rozpoczęciem instalacji lub uaktualniania, zaleca się wstrzymanie usługi. Daje to gwarancję, że usługa nie jest wykonywane, gdy Instalator jest kopiowanie plików lub umieszczając zestawów w globalnej pamięci podręcznej. Następujące polecenie w wierszu Ngen.exe wstrzymuje usługę:  
  
```  
ngen queue pause  
```  
  
 Gdy wszystkie operacje odroczonego zostały umieszczone w kolejce, następujące polecenie umożliwia usługę, aby wznowić:  
  
```  
ngen queue continue  
```  
  
 Mają być odroczone generowanie obrazu natywnego, podczas instalowania nowej aplikacji lub podczas aktualizowania współużytkowany składnik, należy użyć `/queue` z opcją `install` lub `update` akcji. Następujące wiersze polecenia Ngen.exe Zainstaluj obraz natywny dla składnika współużytkowanego i wykonać aktualizację wszystkich katalogów głównych, które może mieć wpływ:  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 `update` Akcji generuje wszystkie obrazy natywne, które zostały unieważnione, nie tylko te, które używają `MyComponent`.  
  
 Jeśli aplikacja składa się z wielu katalogów głównych, możesz kontrolować priorytet odroczonego akcji. Następujące polecenia w kolejce instalacji trzech głównych. `Assembly1` jest zainstalowany jako pierwszy, bez czekania na okres bezczynności. `Assembly2` jest również instalowany bez oczekiwania na okres bezczynności, ale po zakończeniu wszystkich akcji z priorytetem 1. `Assembly3` jest zainstalowana, gdy usługa wykrywa, że komputer jest w stanie bezczynności.  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 Można wymusić akcji w kolejce nastąpi synchronicznie przy użyciu `executeQueuedItems` akcji. Jeśli podasz opcjonalne priorytet, ta akcja dotyczy tylko umieszczonych w kolejce akcje, które mają taki sam lub niższy priorytet. Domyślnym priorytetem jest 3, dzięki czemu polecenie Ngen.exe przetwarza wszystkich akcji w kolejce natychmiast i nie może zwracać dopóki nie zostaną one ukończone:  
  
```  
ngen executeQueuedItems  
```  
  
 Synchroniczne polecenia są wykonywane przez Ngen.exe i nie używaj usługi obrazów natywnych. Można wykonywać akcji przy użyciu Ngen.exe, gdy jest uruchomiona usługa obrazów natywnych.  
  
### <a name="service-shutdown"></a>Zamykanie usługi  
 Po jest inicjowane przez wykonanie polecenia Ngen.exe, która obejmuje `/queue` opcja, usługa jest uruchamiana w tle do momentu zakończenia wszystkich akcji. Usługa zapisuje stanu tak, aby w razie potrzeby można kontynuować przez wiele ponownego uruchomienia. Kiedy usługa wykryje, że istnieją żadnych więcej akcji w kolejce resetuje stan tak, aby nie zostanie uruchomiony ponownie przy następnym rozruchu komputera i jej zamknięcie się.  
  
### <a name="service-interaction-with-clients"></a>Usługa interakcji z klientami  
 W .NET Framework w wersji 2.0 jedyna interakcja z usługi obrazów natywnych jest przy użyciu wiersza polecenia narzędzia Ngen.exe. Narzędzie wiersza polecenia w skryptach instalacji do kolejki akcji dla usługi obrazów natywnych i interakcji z usługą.  
  
## <a name="see-also"></a>Zobacz także
- [Narzędzia](../../../docs/framework/tools/index.md)
- [Proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
