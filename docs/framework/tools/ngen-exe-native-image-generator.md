---
title: Ngen.exe (Generator obrazu natywnego)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "57"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20c120323356171d78da35a490488f4654baece6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (Generator obrazu natywnego)
Generator obrazów natywnych (Ngen.exe) jest narzędziem, które poprawia wydajność zarządzanych aplikacji. Program Ngen.exe tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy specyficzny dla procesora, i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.  
  
 Zmienia się na Ngen.exe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:  
  
-   Program Ngen.exe obecnie kompiluje zestawy w trybie pełnego zaufania, a zasady zabezpieczeń dostępu kodu (CAS) nie są już uwzględniane.  
  
-   Obrazy natywne generowane przez program Ngen.exe nie mogą już być ładowane do aplikacji, które działają w trybie częściowego zaufania.  
  
 Zmiany w programie Ngen.exe wprowadzone w programie .NET Framework w wersji 2.0:  
  
-   Instalacja zestawu powoduje także instalację jego zależności, co upraszcza składnię programu Ngen.exe.  
  
-   Obrazy natywne mogą być współużytkowane w różnych domenach aplikacji.  
  
-   Nowa akcja, `update`, ponownie tworzy obrazy, które zostały unieważnione.  
  
-   Akcje mogą być odraczane w celu wykonania przez usługę, która korzysta z czasu bezczynności komputera, aby generować i instalować obrazy.  
  
-   Niektóre przyczyny unieważnienia obrazu zostały wyeliminowane.  
  
 W systemie Windows 8, zobacz [zadań obrazu macierzystego](http://msdn.microsoft.com/library/9b1f7590-4e0d-4737-90ef-eaf696932afb).  
  
 Aby uzyskać dodatkowe informacje na temat używania Ngen.exe i usługę obrazu macierzystego, zobacz [usługi obrazu macierzystego][Native Image Service].  
  
> [!NOTE]
>  Składnia ngen.exe w wersjach 1.0 i 1.1 programu .NET Framework, można znaleźć w [składni starszych Generator obrazu natywnego (Ngen.exe)](http://msdn.microsoft.com/library/5a69fc7a-103f-4afc-8ab4-606adcb46324).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a>Akcje  
 W poniższej tabeli przedstawiono składnię każdego `action`. Opis poszczególnych części `action`, zobacz [argumenty](#ArgumentTable), [poziomy priorytetu](#PriorityTable), [scenariusze](#ScenarioTable), i [Config](#ConfigTable)tabel. [Opcje](#OptionTable) tabeli opisano `options` i przełączników pomocy.  
  
|Akcja|Opis|  
|------------|-----------------|  
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|Generuje obrazy natywne dla zestawu i jego zależności, a także instaluje obrazy w pamięci podręcznej obrazów natywnych.<br /><br /> Jeśli `/queue` jest określony, akcja jest w kolejce na usługę obrazu macierzystego. Domyślnym priorytetem jest 3. Zobacz [poziomy priorytetu](#PriorityTable) tabeli.|  
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Usuwa obrazy natywne zestawu i jego zależności z pamięci podręcznej obrazów natywnych.<br /><br /> Aby odinstalować pojedynczy obraz i jego zależności, należy użyć tych samych argumentów wiersza polecenia, które zostały użyte podczas instalacji obrazu. **Uwaga:** począwszy [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Akcja `uninstall` * nie jest już obsługiwana.|  
|`update` [`/queue`]|Aktualizuje obrazy natywne, które stały się nieprawidłowe.<br /><br /> Jeśli `/queue` jest określony, aktualizacje oczekujących w kolejce na usługę obrazu macierzystego. Aktualizacje są zawsze planowane z priorytetem 3, więc są uruchamiane, gdy komputer znajduje się w stanie bezczynności.|  
|`display` [`assemblyName` &#124; `assemblyPath`]|Wyświetla stan obrazów natywnych dla zestawu i jego zależności.<br /><br /> Jeśli nie zostaną dostarczone argumenty, będą wyświetlane wszystkie dane z pamięci podręcznej obrazów natywnych.|  
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> —lub—<br /><br /> `eqi` [1&#124;2&#124;3]|Wykonuje umieszczone w kolejce zadania kompilacji.<br /><br /> Jeśli określono priorytet, wykonywane są zadania kompilacji z większym lub równym priorytetem. Jeśli nie określono priorytetu, wykonywane są wszystkie skolejkowane zadania kompilacji.|  
|`queue` {`pause` &#124; `continue` &#124; `status`}|Wstrzymuje usługę obrazów natywnych, zezwala wstrzymanej usłudze na kontynuowanie działania lub bada stan usługi.|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a>Argumenty  
  
|Argument|Opis|  
|--------------|-----------------|  
|`assemblyName`|Pełna nazwa wyświetlana zestawu. Na przykład `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Uwaga:** można podać nazwę zestawu z częściowa, takich jak `myAssembly`, dla `display` i `uninstall` akcje. <br /><br /> W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.|  
|`assemblyPath`|Jawna ścieżka zestawu. Można określić pełną lub względną ścieżkę.<br /><br /> Jeśli użytkownik określi nazwę pliku bez ścieżki, zestaw musi znajdować się w bieżącym katalogu.<br /><br /> W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a>Poziomy priorytetów  
  
|Priorytet|Opis|  
|--------------|-----------------|  
|`1`|Obrazy natywne są generowane i instalowane natychmiast, bez czekania na okres bezczynności.|  
|`2`|Obrazy natywne są generowane i instalowane bez czekania na okres bezczynności, ale po zakończeniu wszystkich akcji z priorytetem 1 (i ich zależności).|  
|`3`|Obrazy natywne są instalowane, gdy usługa obrazów natywnych wykryje, że komputer jest w stanie bezczynności. Zobacz [obrazu macierzystego usługi][Native Image Service].|  
  
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
|`/ExeConfig:``exePath`|Używa konfiguracji określonego zestawu wykonywalnego.<br /><br /> Program Ngen.exe musi podjąć te same decyzje, co moduł ładowania podczas tworzenia powiązania z zależnościami. Po załadowaniu składnika współużytkowanego w czasie wykonywania za pomocą <xref:System.Reflection.Assembly.Load%2A> metoda, pliku konfiguracji aplikacji określa zależności, które zostały załadowane dla składnika współużytkowanego — na przykład wersję zależności, który jest ładowany. `/ExeConfig` Przełącznika zapewnia wskazówki Ngen.exe, na którym będzie można załadować zależności w czasie wykonywania.|  
|`/AppBase:``directoryPath`|Podczas lokalizowania zależności należy użyć określonego katalogu jako podstawy aplikacji.|  
  
<a name="OptionTable"></a>   
## <a name="options"></a>Opcje  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/nologo`|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|`/silent`|Pomija wyświetlanie komunikatów o sukcesie.|  
|`/verbose`|Wyświetla szczegółowe informacje na potrzeby debugowania. **Uwaga:** ze względu na ograniczenia systemu operacyjnego, ta opcja nie powoduje wyświetlenie tylu informacji dodatkowych Windows 98 i Windows Millennium Edition.|  
|`/help`, `/?`|Wyświetla składnię polecenia i opcje dla aktualnego wydania.|  
  
## <a name="remarks"></a>Uwagi  
 Użytkownik musi mieć uprawnienia administracyjne, aby uruchomić program Ngen.exe.  
  
> [!CAUTION]
>  Nie należy uruchamiać programu Ngen.exe dla zestawów, które nie są w pełni zaufane. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]Ngen.exe kompiluje zestawów o pełnym zaufaniu i zasady zabezpieczeń (CAS) kod dostępu nie była już oceniana.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nie można załadować obrazów macierzystych, które są generowane z Ngen.exe do aplikacji, które są uruchomione w częściowej relacji zaufania. Zamiast tego wywoływany jest kompilator JIT (Just-In-Time).  
  
 Ngen.exe generuje obrazów macierzystych dla zestawu określony przez `assemblyname` argument `install` akcji i wszystkie jego zależności. Zależności są ustalane na podstawie odwołań w manifeście zestawu. Jedyny scenariusz, w którym należy zainstalować oddzielnie zależność jest podczas ładowania aplikacji za pomocą odbicia, na przykład wywołując <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
> [!IMPORTANT]
>  Nie używaj <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody z obrazów macierzystych. Obraz załadowany za pomocą tej metody nie może być używany przez inne zestawy w kontekście wykonywania.  
  
 Program Ngen.exe utrzymuje licznik zależności. Załóżmy na przykład, `MyAssembly.exe` i `YourAssembly.exe` w pamięci podręcznej obrazów natywnych są zainstalowane, a jednocześnie odwołują się do `OurDependency.dll`. Jeśli `MyAssembly.exe` zostanie odinstalowany, `OurDependency.dll` nie został odinstalowany. Jest on tylko usunięte podczas `YourAssembly.exe` również zostanie odinstalowana.  
  
 Jeśli jest generowany obraz natywny dla zestawu przechowywanego w globalnej pamięci podręcznej zestawów, należy określić jego nazwę wyświetlaną. Zobacz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.  
  
 Obrazy natywne, które generuje program Ngen.exe, mogą być współużytkowane w różnych domenach aplikacji. Oznacza to, że można używać programu Ngen.exe w scenariuszach aplikacji, które wymagają współużytkowania zestawów w różnych domenach aplikacji. Aby określić neutralność domeny:  
  
-   Zastosuj <xref:System.LoaderOptimizationAttribute> atrybutu do aplikacji.  
  
-   Ustaw <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> właściwości po utworzeniu informacji Instalatora dla nowej domeny aplikacji.  
  
 Zawsze należy używać kodu neutralnego względem domeny podczas ładowania jego zestawu do wielu domen aplikacji. Jeśli obraz natywny zostanie załadowany do niewspółużytkowanej domeny aplikacji po załadowaniu do domeny współużytkowanej, nie będzie można go użyć.  
  
> [!NOTE]
>  Kod neutralny względem domeny nie może zostać zwolniony i wydajność może być nieco niższa, szczególnie w przypadku uzyskiwania dostępu do statycznych elementów członkowskich.  
  
 W tej sekcji Uwagi:  
  
-   [Trwa generowanie obrazów dla różnych scenariuszy](#Scenarios)  
  
-   [Określanie, kiedy należy używać obrazów macierzystych](#WhenToUse)  
  
    -   [Ulepszone użycia pamięci](#Memory)  
  
    -   [Szybsze uruchamianie aplikacji](#Startup)  
  
    -   [Podsumowanie planowanego sposobu użycia](#UsageSummary)  
  
-   [Znaczenie adres podstawowy zestaw](#BaseAddresses)  
  
-   [Twarde powiązania](#HardBinding)  
  
    -   [Określanie wskazówki powiązanie zależność](#DependencyHint)  
  
    -   [Określanie domyślnego wskazówki powiązania dla zestawu](#AssemblyHint)  
  
-   [Przetwarzanie z opóźnieniem](#Deferred)  
  
-   [Obrazy Native i kompilacja JIT](#JITCompilation)  
  
    -   [Nieprawidłowe obrazy](#InvalidImages)  
  
-   [Rozwiązywanie problemów](#Troubleshooting)  
  
    -   [Podgląd dziennika powiązań zestawów](#Fusion)  
  
    -   [JITCompilationStart zarządzany Asystent debugowania](#MDA)  
  
    -   [Rezygnacja z generowanie obrazu natywnego](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a>Trwa generowanie obrazów dla różnych scenariuszy  
 Po wygenerowaniu obrazu macierzystego dla zestawu środowiska wykonawczego automatycznie próbuje zlokalizować i użyć tego obrazu macierzystego z każdym uruchomieniu zestawu. W zależności od scenariuszy użycia można generować wiele obrazów.  
  
 Na przykład po uruchomieniu zestawu w debugowania lub scenariusz profilowania środowiska uruchomieniowego szuka obrazu macierzystego, który został wygenerowany z `/Debug` lub `/Profile` opcje. Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca standardową kompilację JIT. Jedynym sposobem debugowania obrazów natywnych jest utworzenie obrazu macierzystego z `/Debug` opcji.  
  
 `uninstall` Akcji również rozpoznaje scenariuszy, więc można odinstalować wszystkie scenariusze lub tylko wybranego scenariuszy.  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a>Określanie, kiedy należy używać obrazów macierzystych  
 Obrazy natywne zapewniają poprawę wydajności w dwóch obszarach: ulepszone wykorzystanie pamięci i skrócenie czasu uruchamiania.  
  
> [!NOTE]
>  Wydajność obrazów natywnych zależy od kilku czynników, które utrudniają analizę, takich jak wzorce dostępu kodu i danych, liczba wywołań, jakie miały miejsce między granicami modułów, a także liczba zależności, które zostały już załadowane przez inne aplikacje. Jedynym sposobem ustalenia, czy obrazy natywne przynoszą korzyść aplikacji, są dokładne pomiary wydajności w kluczowych scenariuszach wdrażania.  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a>Ulepszone użycia pamięci  
 Obrazy natywne mogą znacznie poprawić wykorzystanie pamięci, gdy kod jest współużytkowany w różnych procesach. Obrazy natywne są plikami środowiska Windows PE, więc pojedyncza kopia pliku dll może być współużytkowana przez wiele procesów, natomiast kod natywny wytworzony przez kompilator JIT jest przechowywany w pamięci prywatnej i nie może być współużytkowany.  
  
 Aplikacje uruchamiane w ramach usług terminalowych również mogą korzystać z udostępnionych stron kodowych.  
  
 Ponadto rezygnacja z ładowania kompilatora JIT umożliwia oszczędzenie określonej ilości pamięci dla każdego wystąpienia aplikacji.  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a>Szybsze uruchamianie aplikacji  
 Wstępna kompilacja zestawów przy użyciu programu Ngen.exe może poprawić czas uruchamiania niektórych aplikacji. Ogólnie rzecz biorąc, współużytkowanie zestawów składnika przez aplikacje przynosi zyski, ponieważ po uruchomieniu pierwszej aplikacji składniki współużytkowane są już załadowane dla kolejnych aplikacji. Podczas zimnego uruchamiania nie występują takie zyski z wykorzystania obrazów natywnych, ponieważ każdy zestaw aplikacji musi zostać załadowany z dysku twardego, przez co czas dostępu do dysku twardego przeważa zyski ze współużytkowania.  
  
 Trwałe powiązania mogą wpływać na czas uruchamiania, ponieważ wszystkie obrazy trwale powiązane z głównym zestawem aplikacji muszą zostać załadowane w tym samym czasie.  
  
> [!NOTE]
>  Przed [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], składniki o silnych nazwach, współdzielonych należy umieścić w globalnej pamięci podręcznej zestawów, ponieważ moduł ładujący przeprowadza weryfikację dodatkowe zestawy o silnych nazwach, które nie w pamięci podręcznej GAC, efektywnie eliminuje poprawy w czasie uruchamiania uzyskane przy użyciu obrazów macierzystych. Funkcje optymalizacji, które zostały wprowadzone w systemie [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] usunięte dodatkowej weryfikacji.  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a>Podsumowanie planowanego sposobu użycia  
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
## <a name="importance-of-assembly-base-addresses"></a>Znaczenie adres podstawowy zestaw  
 Obrazy natywne są plikami środowiska Windows PE, więc dotyczą ich te same problemy zmiany podstawy, co innych plików wykonywalnych. Spadek wydajności przy relokacji jest jeszcze bardziej widoczny, jeśli są stosowane powiązania trwałe.  
  
 Aby ustawić adres podstawowy dla obrazu natywnego, należy użyć odpowiedniej opcji kompilatora, aby ustawić adres podstawowy dla zestawu. Program Ngen.exe używa tego adresu podstawowego dla obrazu natywnego.  
  
> [!NOTE]
>  Obrazy natywne są większe niż zestawy zarządzane, na podstawie których zostały utworzone. Adresy podstawowe muszą być obliczane tak, aby zezwalały na te większe rozmiary.  
  
 Można użyć narzędzia, takiego jak dumpbin.exe, aby wyświetlić preferowany adres podstawowy obrazu natywnego.  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a>Twarde powiązania  
 Trwałe powiązania zwiększają przepustowość i zmniejszają rozmiar zestawu roboczego dla obrazów natywnych. Wadą trwałych powiązań jest fakt, że wszystkie obrazy, które są trwale powiązane z zestawem, muszą być ładowane razem z zestawem. Może to znacznie zwiększyć czas uruchamiania dużych aplikacji.  
  
 Trwałe powiązanie jest odpowiednie dla zależności, które są ładowane we wszystkich krytycznych pod względem wydajności scenariuszach aplikacji. Podobnie jak w przypadku każdego aspektu wykorzystania obrazu natywnego, staranne wykonywanie pomiarów wydajności jest jedynym sposobem ustalenia, czy trwałe powiązanie zwiększa wydajność aplikacji.  
  
 <xref:System.Runtime.CompilerServices.DependencyAttribute> i <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> atrybutów umożliwiają zapewnienie wskazówek twardych powiązanie Ngen.exe.  
  
> [!NOTE]
>  Te atrybuty są wskazówkami dla programu Ngen.exe, a nie poleceniami. Użycie ich nie gwarantuje uzyskania trwałego powiązania. Znaczenie tych atrybutów może się zmieniać w przyszłych wersjach.  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a>Określanie wskazówki powiązanie zależność  
 Zastosuj <xref:System.Runtime.CompilerServices.DependencyAttribute> do zestawu, które wskazują prawdopodobieństwo określona zależność zostanie załadowany. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>Wskazuje, że powiązanie twardym jest odpowiednie, <xref:System.Runtime.CompilerServices.LoadHint.Default> wskazuje, że powinny być używane domyślne dla zależności, i <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> wskazuje twardych powiązania nie jest odpowiedni.  
  
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
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Określanie domyślnego wskazówki powiązania dla zestawu  
 Domyślne wskazówki powiązania potrzebne są tylko zestawom, które będą stosowane natychmiastowo i często przez dowolną aplikację, która jest od nich zależna. Zastosuj <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> z <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> do tych zestawów, aby określić, że używane powiązanie twardych.  
  
> [!NOTE]
>  To nie ma powodu do zastosowania <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> do zestawów .dll, które nie należą do tej kategorii, ponieważ stosowanie atrybutu o wartości innej niż <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> ma ten sam efekt co w ogóle nie stosowanie atrybutu.  
  
 Firma Microsoft używa <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> do określenia, czy powiązanie twardym jest ustawieniem domyślnym dla bardzo małą liczbę zestawów w programie .NET Framework, takie jak mscorlib.dll.  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a>Przetwarzanie z opóźnieniem  
 Generowanie obrazów natywnych dla bardzo dużych aplikacji może zająć znaczną ilość czasu. Podobnie zmiany składnika współużytkowanego lub zmiany w ustawieniach komputera mogą wymagać aktualizacji wielu obrazów natywnych. `install` i `update` akcji ma `/queue` opcję kolejkuje operację dla odroczonego wykonania przez usługę obrazu macierzystego. Ponadto ma Ngen.exe `queue` i `executeQueuedItems` działania, które zapewniają pewną kontrolę nad usługi. Aby uzyskać więcej informacji, zobacz [usługi obrazu macierzystego][Native Image Service].  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a>Obrazy Native i kompilacja JIT  
 Jeśli program Ngen.exe napotka w zestawie jakiekolwiek metody, których nie może wygenerować, wyklucza je z obrazu natywnego. Gdy środowisko uruchomieniowe wykonuje zestaw, przywraca kompilację JIT dla metod, które nie zostały uwzględnione w obrazie natywnym.  
  
 Ponadto obrazy natywne nie są używane, jeśli zestaw został uaktualniony lub jeśli obraz został unieważniony z jakiegokolwiek powodu.  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a>Nieprawidłowe obrazy  
 Użycie programu Ngen.exe w celu utworzenia obrazu natywnego zestawu powoduje, że dane wyjściowe zależą od opcji wiersza polecenia, które można określić, i niektórych ustawień na komputerze. Są to m.in. następujące ustawienia:  
  
-   Wersja programu .NET Framework.  
  
-   Wersja systemu operacyjnego, jeśli zmiana dotyczy z rodziny Windows 9 x z rodziny Windows NT.  
  
-   Dokładna tożsamość zestawu (ponowna kompilacja zmienia tożsamość).  
  
-   Dokładna tożsamość wszystkich zestawów, do których odwołuje się zestaw (ponowna kompilacja zmienia tożsamość).  
  
-   Czynniki związane z zabezpieczeniami.  
  
 Program Ngen.exe rejestruje te informacje podczas generowania obrazu natywnego. Podczas wykonywania zestawu środowisko uruchomieniowe poszukuje obrazu natywnego wygenerowanego z użyciem opcji i ustawień, które odpowiadają bieżącemu środowisku komputera. Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca kompilację JIT zestawu. Następujące zmiany w ustawieniach komputera i środowiska powodują, że obrazy natywne stają się nieprawidłowe:  
  
-   Wersja programu .NET Framework.  
  
     Jeśli zastosowano aktualizację programu .NET Framework, wszystkie obrazy natywne utworzone przy użyciu programu Ngen.exe stają się nieprawidłowe. Z tego powodu wykonania wszystkich aktualizacji platformy .NET `Ngen Update` polecenie, aby upewnić się, że wszystkie obrazów macierzystych są generowane. Program .NET Framework automatycznie tworzy nowe obrazy natywne dla bibliotek programu .NET Framework, które instaluje.  
  
-   Wersja systemu operacyjnego, jeśli zmiana dotyczy z rodziny Windows 9 x z rodziny Windows NT.  
  
     Na przykład jeśli wersja systemu operacyjnego na komputerze z systemem zmieni się z systemu Windows 98 do systemu Windows XP, wszystkich obrazów macierzystych przechowywanych w pamięci podręcznej obrazów natywnych staną się nieprawidłowe. Jednak w przypadku systemu operacyjnego zmiany z systemu Windows 2000 do systemu Windows XP, obrazy nie są unieważniona.  
  
-   Dokładna tożsamość zestawu.  
  
     Jeśli zestaw zostanie ponownie skompilowany, obraz natywny odpowiadający zestawowi staje się nieprawidłowy.  
  
-   Dokładna tożsamość jakichkolwiek zestawów, do których odwołuje się zestaw.  
  
     Jeżeli zestaw zarządzany zostanie zaktualizowany, wszystkie obrazy natywne zależne bezpośrednio lub pośrednio od tego zestawu stają się nieprawidłowe i muszą zostać wygenerowane ponownie. Obejmuje to zarówno zwykłe odwołania, jak i trwale powiązane zależności. Zawsze, gdy aktualizacja oprogramowania nie zostanie zastosowana, program instalacyjny powinien zostać wykonany `Ngen Update` polecenie, aby upewnić się, że wszystkie zależne obrazów macierzystych są generowane.  
  
-   Czynniki związane z zabezpieczeniami.  
  
     Zmiana zasad zabezpieczeń komputera ograniczająca uprawnienia udzielone uprzednio zestawowi może spowodować, że poprzednio skompilowane obrazy natywne dla tego zestawu staną się nieprawidłowe.  
  
     Aby uzyskać szczegółowe informacje dotyczące sposobu środowisko uruchomieniowe języka wspólnego zarządza zabezpieczenia dostępu kodu i sposobu korzystania z uprawnień, zobacz [zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md).  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Następujące tematy dotyczące rozwiązywania problemów umożliwiają wyświetlanie które obrazów macierzystych są używane i nie można użyć przez aplikację, do określania, kiedy przy użyciu kompilatora JIT rozpoczyna się skompilować metody i pokazuje, jak rezygnacji z tworzenia obrazu macierzystego określona metody.  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a>podgląd dziennika powiązań zestawów  
 Aby upewnić się, że obrazów macierzystych są używane przez aplikację, można użyć [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md). Wybierz **obrazów macierzystych** w **kategorie dziennika** pola w oknie Podgląd dziennika powiązań. Program Fuslogvw.exe dostarcza informacje o tym, dlaczego obraz natywny został odrzucony.  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>JITCompilationStart zarządzany Asystent debugowania  
 Można użyć [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) zarządzany Asystent debugowania (MDA), aby określić podczas uruchamiania kompilatora JIT skompilować funkcję.  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a>Rezygnacja z generowanie obrazu natywnego  
 W niektórych przypadkach NGen.exe mogą mieć trudności generowania, który obrazu macierzystego dla określonej metody, lub mogą preferować, że metoda być skompilowana w trybie JIT zamiast skompilowanych do obrazu macierzystego. W takim przypadku można użyć `System.Runtime.BypassNGenAttribute` atrybutu, aby zapobiec NGen.exe generowanie obrazu macierzystego dla określonej metody. Atrybut należy zastosować indywidualnie do każdej metody kodu, których nie chcesz dołączyć do obrazu macierzystego. NGen.exe rozpoznaje atrybutu i nie generuje kod w obrazu macierzystego dla odpowiedniej metody.  
  
 Zauważ, że `BypassNGenAttribute` nie jest zdefiniowany jako typ w bibliotece klas programu .NET Framework. Aby można było korzystać z atrybutu w kodzie, należy najpierw zdefiniować ją w następujący sposób:  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 Można użyć atrybutu na podstawie-method. Poniższy przykład powoduje, że Generator obrazu natywnego czy nie powinna generować obrazu macierzystego dla `ExampleClass.ToJITCompile` metody.  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a>Przykłady  
 Polecenie generuje obrazu macierzystego dla `ClientApp.exe`, znajduje się w bieżącym katalogu i instaluje obraz w pamięci podręcznej obrazów natywnych. Jeśli istnieje plik konfiguracji zestawu, program Ngen.exe go użyje. Ponadto obrazów macierzystych są generowane dla plików dll żadnych `ClientApp.exe` odwołania.  
  
```  
ngen install ClientApp.exe  
```  
  
 Obraz instalowany za pomocą programu Ngen.exe jest również nazywany elementem głównym. Elementem głównym może być aplikacja albo składnik współużytkowany.  
  
 Polecenie generuje obrazu macierzystego dla `MyAssembly.exe` z określoną ścieżką.  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 Podczas lokalizowania zestawów i ich zależności program Ngen.exe używa tej samej logiki badania, co środowisko uruchomieniowe języka wspólnego (CLR). Domyślnie katalog, który zawiera `ClientApp.exe` jest używany jako podstawowego katalogu aplikacji, a wszystkie badania zestawu rozpoczyna się w tym katalogu. To zachowanie można przesłonić przy użyciu `/AppBase` opcji.  
  
> [!NOTE]
>  Zachowanie to różni się od zachowania programu Ngen.exe w wersjach 1.0 i 1.1 programu .NET Framework, gdzie podstawa aplikacji znajduje się w bieżącym katalogu.  
  
 Zestaw może mieć zależności bez odwołania, na przykład jeśli ładuje plik dll za pomocą <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Można utworzyć obrazu macierzystego pliku dll przy użyciu informacji o konfiguracji dla zestawu aplikacji `/ExeConfig` opcji. Polecenie generuje obrazu macierzystego dla `MyLib.dll,` przy użyciu informacji konfiguracyjnych z `MyApp.exe`.  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 Zestawy instalowane w ten sposób nie są usuwane, gdy jest usuwana aplikacja.  
  
 Aby odinstalować zależność, należy użyć tych samych opcji wiersza polecenia, które zostały użyte podczas jej instalowania. Polecenie odinstalowuje `MyLib.dll` z poprzedniego przykładu.  
  
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
  
 `display` Akcji zawiera wszystkie zestawy główne najpierw następuje lista wszystkich obrazów macierzystych na komputerze.  
  
 Prosta nazwa zestawu służy do wyświetlania informacji dotyczących tylko tego zestawu. Następujące polecenie wyświetla wszystkich obrazów natywnych w pamięci podręcznej obrazów natywnych zgodnych z częściowa nazwą `MyAssembly`, ich zależności i wszystkich katalogów głównych, które zależy od `MyAssembly`:  
  
```  
ngen display MyAssembly  
```  
  
 Wiedząc, jakie elementy główne są zależne od zestaw udostępnionego składnika jest przydatny do skalowania wpływ `update` akcji po uaktualnieniu składnika współużytkowanego.  
  
 Aby określić rozszerzenie pliku zestawu, należy określić ścieżkę lub wykonać program Ngen.exe z katalogu zawierającego zestaw:  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 Następujące polecenie wyświetla wszystkich obrazów natywnych w pamięci podręcznej obrazów natywnych o nazwie `MyAssembly` i w wersji 1.0.0.0.  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a>Aktualizacja obrazów  
 Obrazy są zazwyczaj aktualizowane po uaktualnieniu składnika współużytkowanego. Aby zaktualizować wszystkich obrazów macierzystych, które zostały zmienione lub którego zależności zostały zmienione, należy użyć `update` akcji bez argumentów.  
  
```  
ngen update  
```  
  
 Aktualizacja wszystkich obrazów może być długotrwałym procesem. Można dodać do kolejki aktualizacje do wykonywania przez usługę obrazu macierzystego przy użyciu `/queue` opcji. Aby uzyskać więcej informacji na temat `/queue` priorytetów opcji i instalacji, zobacz [usługi obrazu macierzystego][Native Image Service].  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a>Odinstalowywanie obrazów  
 Program Ngen.exe utrzymuje listę zależności, aby składniki współużytkowane były usuwane tylko wtedy, gdy wszystkie zestawy, które od nich zależą, zostały usunięte. Ponadto współużytkowany składnik nie zostanie usunięty, jeśli został zainstalowany jako element główny.  
  
 Polecenie Odinstalowuje wszystkie scenariusze dla głównego `ClientApp.exe`:  
  
```  
ngen uninstall ClientApp  
```  
  
 `uninstall` Akcja może zostać użyta do usunięcia konkretnych scenariuszy. Poniższe polecenie powoduje odinstalowanie wszystkich scenariuszach debugowania dla `ClientApp.exe`:  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  Odinstalowywanie `/debug` scenariuszy nie powoduje odinstalowania scenariusz obejmuje `/profile` i`/debug.`  
  
 Polecenie Odinstalowuje wszystkie scenariusze dla określonej wersji `ClientApp.exe`:  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 Następujące polecenia Odinstaluj wszystkie scenariusze `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` lub po prostu scenariusza debugowania dla tego zestawu:  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 Jak `install` akcja, podając rozszerzenie wymaga albo wykonywania Ngen.exe od katalogu zawierającego zestaw lub określ pełną ścieżkę.  
  
 Przykłady dotyczące obrazu macierzystego usługi można znaleźć [usługi obrazu macierzystego][Native Image Service].  
  
## <a name="native-image-task"></a>Obraz macierzysty — zadanie  
 Zadanie obrazu macierzystego jest zadanie systemu Windows, które generuje i obsługuje obrazów macierzystych. Zadanie obrazu macierzystego generuje i zwraca obrazów macierzystych automatycznie dla obsługiwanych scenariuszach. (Zobacz [tworzenia obrazów macierzystych](http://msdn.microsoft.com/library/2bc8b678-dd8d-4742-ad82-319e9bf52418).) Umożliwia również instalatorów do użycia [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) do tworzenia i aktualizowania obrazów macierzystych odroczonego naraz.  
  
 Zadanie obrazu macierzystego jest zarejestrowany, gdy dla każdego Procesora architektura obsługiwana na komputerze, aby umożliwić kompilacji dla aplikacji przeznaczonych każdej architektury:  
  
|Nazwa zadania|komputer 32-bitowy|komputer 64-bitowy|  
|---------------|----------------------|----------------------|  
|NET Framework NGEN 4.0.30319|Tak|Tak|  
|NET Framework NGEN 4.0.30319 64|Nie|Tak|  
  
 Zadanie obrazu macierzystego jest jest dostępna w .NET Framework 4.5 lub nowszy, podczas uruchamiania w systemie Windows 8 lub nowszym. We wcześniejszych wersjach systemu Windows korzysta z programu .NET Framework [usługi obrazu macierzystego][Native Image Service].  
  
### <a name="task-lifetime"></a>Cykl życia zadania  
 Ogólnie rzecz biorąc harmonogramu zadań systemu Windows uruchamia zadanie obrazu macierzystego, każdej nocy, gdy komputer jest w stanie bezczynności. Zadanie sprawdza, czy odroczonego pracę umieszczonych w kolejce przez programy instalacyjne, żądań aktualizacji odroczonego obrazu macierzystego i tworzenia żadnych obrazów automatycznego. Zadanie kończy zaległych elementów pracy i zamknięcie. Jeśli komputer nie jest bezczynne podczas wykonywania zadania, zatrzymuje zadanie.  
  
 Można również uruchomić ręcznie za pośrednictwem interfejsu użytkownika harmonogramu zadań lub ręcznego wywołania NGen.exe zadania obrazu macierzystego. Jeśli zadanie zostało uruchomione przy użyciu jednej z tych metod, będzie nadal uruchomiona, gdy komputer nie jest już bezczynności. Obrazy utworzone ręcznie za pomocą NGen.exe mają pierwszeństwo umożliwiające przewidywalne zachowanie dla instalatorów aplikacji.  
  
## <a name="native-image-service"></a>Usługa obrazu macierzystego  
 Usługa obrazu macierzystego jest usługa systemu Windows, który generuje i przechowuje obrazów macierzystych. Usługa obrazu macierzystego umożliwia deweloperowi odroczenie instalacji i aktualizacji obrazów macierzystych okresów, gdy komputer jest w stanie bezczynności.  
  
 Zazwyczaj usługa obrazu macierzystego jest inicjowane przez program instalacyjny (Instalator) dla aplikacji lub aktualizacji. Priorytet 3 działań usługa wykonuje w czasie bezczynności na komputerze. Usługa zapisuje swój stan i może ona nadal przez wiele ponownych uruchomień komputera, jeśli to konieczne. Wiele kompilacje obrazu można umieścić w kolejce.  
  
 Usługa także współdziała z ręcznego polecenie Ngen.exe. Ręczne polecenia mają pierwszeństwo przed aktywności w tle.  
  
> [!NOTE]
>  W systemie Windows Vista Nazwa wyświetlana usługi obrazu macierzystego jest "v2.0.50727_X86 NGEN Microsoft.NET Framework" lub "NGEN Microsoft.NET Framework v2.0.50727_X64". We wszystkich wcześniejszych wersjach systemu Microsoft Windows nazwa jest "V2.0.50727_X86 usługi optymalizacji środowiska wykonawczego .NET" lub "Usługi optymalizacji środowiska wykonawczego .NET v2.0.50727_X64".  
  
### <a name="launching-deferred-operations"></a>Uruchamianie operacji odroczone  
 Przed rozpoczęciem instalacji lub uaktualniania, zaleca się wstrzymanie usługi. Dzięki temu, że usługa nie wykonać, gdy Instalator jest kopiowanie plików lub umieszczanie zestawów w globalnej pamięci podręcznej zestawów. Następujące polecenie w wierszu Ngen.exe wstrzymuje usługę:  
  
```  
ngen queue pause  
```  
  
 Gdy wszystkie operacje odroczonego zostały umieszczone w kolejce, polecenie umożliwia usłudze wznowić:  
  
```  
ngen queue continue  
```  
  
 Odroczenie generowanie obrazu natywnego podczas instalowania nowej aplikacji lub podczas aktualizowania składnika współużytkowanego, użyj `/queue` opcję z `install` lub `update` akcje. Następujące wiersze polecenia Ngen.exe zainstalować obrazu macierzystego dla składnika współużytkowanego i wykonać aktualizację wszystkich katalogów głównych, które mogą mieć wpływ:  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 `update` Akcji ponowne wygenerowanie wszystkich obrazów macierzystych, które zostały unieważnione, nie tylko te, które używają `MyComponent`.  
  
 Jeśli aplikacja zawiera wiele elementów głównych, można kontrolować priorytet odroczonego akcje. Następujące polecenia w kolejce instalacji trzech głównych. `Assembly1`jest najpierw zainstalowany bez oczekiwania na czas bezczynności. `Assembly2`jest również instalowany bez oczekiwania przez czas bezczynności, ale po zakończeniu wszystkich akcji o priorytecie 1. `Assembly3`jest zainstalowany, gdy usługa wykryje, że komputer jest w stanie bezczynności.  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 Możesz wymusić akcji w kolejce do pojawia się synchronicznie przy użyciu `executeQueuedItems` akcji. Jeśli podasz opcjonalne priorytet, ta akcja dotyczy tylko akcji w kolejce, które mają taki sam lub niższy priorytet. Priorytet domyślny jest 3, aby polecenie Ngen.exe natychmiast przetwarza wszystkich akcji w kolejce, a nie może zwracać aż do ich zakończono:  
  
```  
ngen executeQueuedItems  
```  
  
 Synchroniczne polecenia są wykonywane przez Ngen.exe i nie jest używana usługa obrazu macierzystego. Można wykonywać akcji przy użyciu Ngen.exe jest uruchomiona usługa obrazu macierzystego.  
  
### <a name="service-shutdown"></a>Zamykanie usługi  
 Po jest inicjowane przez wykonanie polecenia Ngen.exe zawierającą `/queue` opcja, usługa działa w tle, dopóki wszystkie akcje zostały ukończone. Usługa zapisuje swój stan, dzięki czemu w razie potrzeby można kontynuować podczas ponownych rozruchów wiele. Gdy usługa wykryje, że ma żadnych więcej akcji w kolejce, następuje zresetowanie jego stan, aby nie zostanie uruchomiony ponownie przy następnym rozruchu komputera i jej zamknięcie się.  
  
### <a name="service-interaction-with-clients"></a>Usługa interakcji z klientami  
 W programie .NET Framework w wersji 2.0 tylko interakcji z usługą obrazu macierzystego jest przy użyciu wiersza polecenia narzędzia Ngen.exe. Narzędzie wiersza polecenia w skryptach instalacji do kolejki akcji dla usługi obrazu macierzystego i interakcję z usługą.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

[Native Image Service]: #native-image-service
