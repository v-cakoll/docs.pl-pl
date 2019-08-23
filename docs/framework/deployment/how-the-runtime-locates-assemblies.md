---
title: Sposoby lokalizowania zestawów przez środowisko uruchomieniowe
ms.date: 03/30/2017
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ddec748dc400418c21bfa8fab6fd2735d74af6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941784"
---
# <a name="how-the-runtime-locates-assemblies"></a>Sposoby lokalizowania zestawów przez środowisko uruchomieniowe
Aby pomyślnie wdrożyć aplikację .NET Framework, należy zrozumieć, jak środowisko uruchomieniowe języka wspólnego lokalizuje i tworzy powiązania z zestawami tworzącymi aplikację. Domyślnie środowisko uruchomieniowe próbuje powiązać z dokładną wersją zestawu, z którym została skompilowana aplikacja. To zachowanie domyślne można przesłonić przez ustawienia pliku konfiguracji.  
  
 Środowisko uruchomieniowe języka wspólnego wykonuje kilka czynności podczas próby zlokalizowania zestawu i rozpoznania odwołania do zestawu. Każdy krok został wyjaśniony w poniższych sekcjach. Termin sondowania jest często używany podczas opisywania, jak środowisko uruchomieniowe lokalizuje zestawy. odwołuje się do zestawu algorytmów heurystycznych używanych do lokalizowania zestawu na podstawie jego nazwy i kultury.  
  
> [!NOTE]
> Informacje o powiązaniu można wyświetlić w pliku dziennika za pomocą [przeglądarki dzienników powiązań zestawu (Fuslogvw. exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), która znajduje się w Windows SDK.  
  
## <a name="initiating-the-bind"></a>Inicjowanie powiązania  
 Proces lokalizowania i wiązania z zestawem rozpoczyna się, gdy środowisko uruchomieniowe próbuje rozpoznać odwołanie do innego zestawu. To odwołanie może być statyczne lub dynamiczne. Kompilator rejestruje statyczne odwołania w metadanych manifestu zestawu w czasie kompilacji. Dynamiczne odwołania są konstruowane na bieżąco w wyniku wywoływania różnych metod, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
 Preferowanym sposobem odwoływania się do zestawu jest użycie pełnego odwołania, łącznie z nazwą zestawu, wersją, kulturą i tokenem klucza publicznego (jeśli taki istnieje). Środowisko uruchomieniowe używa tych informacji do zlokalizowania zestawu, wykonując kroki opisane w dalszej części tej sekcji. Środowisko uruchomieniowe używa tego samego procesu rozpoznawania, niezależnie od tego, czy odwołanie dotyczy zestawu statycznego, czy dynamicznego.  
  
 Możesz również uczynić dynamicznym odwołaniem do zestawu, dostarczając metodę wywołującą tylko częściowe informacje o zestawie, na przykład określając tylko nazwę zestawu. W takim przypadku tylko katalog aplikacji jest wyszukiwany dla zestawu i nie są wykonywane żadne inne sprawdzanie. Należy wprowadzić częściowe odwołanie przy użyciu dowolnej z różnych metod ładowania zestawów, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub. <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
 Na koniec można wykonać dynamiczne odwołanie przy użyciu metody, takiej jak <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> i podać tylko częściowe informacje. Możesz następnie zakwalifikować odwołanie [ \<](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) przy użyciu elementu qualifyAssembly > w pliku konfiguracyjnym aplikacji. Ten element umożliwia podanie pełnych informacji referencyjnych (nazwy, wersji, kultury i, jeśli ma zastosowanie, tokenu klucza publicznego) w pliku konfiguracyjnym aplikacji zamiast w kodzie. Tej metody należy użyć, jeśli chcesz w pełni kwalifikować odwołanie do zestawu poza katalogiem aplikacji, lub jeśli chcesz odwołać się do zestawu w globalnej pamięci podręcznej zestawów, ale potrzebujesz wygody do określania pełnego odwołania w plik konfiguracji zamiast w kodzie.  
  
> [!NOTE]
> Tego typu częściowego odwołania nie należy używać z zestawami, które są współużytkowane przez kilka aplikacji. Ponieważ ustawienia konfiguracji są stosowane dla aplikacji, a nie na zestaw, zestaw współużytkowany korzystający z tego typu częściowego odwołania będzie wymagał, aby każda aplikacja używająca zestawu udostępnionego mogła uzyskać informacje kwalifikujące w pliku konfiguracji.  
  
 Środowisko uruchomieniowe używa następujących kroków, aby rozwiązać odwołanie do zestawu:  
  
1. [Określa poprawną wersję zestawu](#step1) , sprawdzając odpowiednie pliki konfiguracji, w tym plik konfiguracyjny aplikacji, plik zasad wydawcy i plik konfiguracji komputera. Jeśli plik konfiguracji znajduje się na komputerze zdalnym, środowisko uruchomieniowe musi najpierw zlokalizować i pobrać plik konfiguracji aplikacji.  
  
2. [Sprawdza, czy nazwa zestawu została powiązana z przed](#step2) i, jeśli tak, używa poprzednio załadowanego zestawu. Jeśli poprzednie żądanie załadowania zestawu nie powiodło się, żądanie kończy się natychmiast bez próby załadowania zestawu.  
  
    > [!NOTE]
    > Buforowanie niepowodzeń powiązań zestawów jest nowe w .NET Framework w wersji 2,0.  
  
3. [Sprawdza globalną pamięć podręczną zestawów](#step3). Jeśli zestaw zostanie tam znaleziony, środowisko uruchomieniowe użyje tego zestawu.  
  
4. [Sondy dla zestawu](#step4) , wykonując następujące czynności:  
  
    1. Jeśli zasady konfiguracji i wydawcy nie wpływają na oryginalne odwołanie i jeśli żądanie powiązania zostało utworzone przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody, środowisko uruchomieniowe sprawdza wskazówki dotyczące lokalizacji.  
  
    2. Jeśli w plikach konfiguracji zostanie znaleziona baza kodu, środowisko uruchomieniowe sprawdzi tylko tę lokalizację. Jeśli sonda nie powiedzie się, środowisko uruchomieniowe określi, że żądanie powiązania nie powiodło się i nie zachodzi żadna inna sonda.  
  
    3. Sondy dla zestawu przy użyciu algorytmów heurystycznych opisanych w [sekcji sondowania](#step4). Jeśli zestaw nie zostanie znaleziony po przeprowadzeniu sondowania, środowisko uruchomieniowe żąda Instalator Windows w celu udostępnienia zestawu. Działa to w ramach funkcji instalacji na żądanie.  
  
        > [!NOTE]
        >  Nie są sprawdzane wersje zestawów bez silnych nazw ani nie są sprawdzane przez środowisko uruchomieniowe w globalnej pamięci podręcznej zestawów dla zestawów bez silnych nazw.  
  
<a name="step1"></a>   
## <a name="step-1-examining-the-configuration-files"></a>Krok 1. Badanie plików konfiguracji  
 Zachowanie powiązania zestawu można skonfigurować na różnych poziomach w oparciu o trzy pliki XML:  
  
- Plik konfiguracji aplikacji.  
  
- Plik zasad wydawcy.  
  
- Plik konfiguracji maszyny.  
  
 Te pliki są zgodne z tą samą składnią i zawierają takie informacje, jak przekierowania powiązań, lokalizacja kodu i tryby powiązań dla konkretnych zestawów. Każdy plik konfiguracyjny może zawierać [ \<element > zestawubinding](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) , który przekierowuje proces powiązania. [ Elementy\<](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) [ \<podrzędne elementu assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) zawierają element dependentAssembly >. Elementy podrzędne [ \<](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) [ elementudependentAssembly\<](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)> zawierają elementu > [ assemblyIdentity,elementu>bindingRedirectikodubazowej>elementu\<](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment) [ \< ](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).  
  
> [!NOTE]
> Informacje o konfiguracji znajdują się w trzech plikach konfiguracji; nie wszystkie elementy są prawidłowe we wszystkich plikach konfiguracyjnych. Na przykład tryb powiązania i informacje o ścieżce prywatnej mogą znajdować się tylko w pliku konfiguracji aplikacji. Aby uzyskać pełną listę informacji zawartych w każdym pliku, zobacz [Konfigurowanie aplikacji przy użyciu plików konfiguracyjnych](../../../docs/framework/configure-apps/index.md).  
  
### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji  
 Najpierw środowisko uruchomieniowe języka wspólnego sprawdza plik konfiguracji aplikacji, aby uzyskać informacje, które zastępują informacje o wersji przechowywane w manifeście zestawu wywołującego. Plik konfiguracji aplikacji można wdrożyć przy użyciu aplikacji, ale nie jest to wymagane do wykonywania aplikacji. Zazwyczaj pobieranie tego pliku jest prawie chwilowe, ale w sytuacjach, gdy baza aplikacji znajduje się na komputerze zdalnym, na przykład w scenariuszu opartym na sieci Web w programie Internet Explorer, należy pobrać plik konfiguracyjny.  
  
 W przypadku plików wykonywalnych klienta plik konfiguracji aplikacji znajduje się w tym samym katalogu co plik wykonywalny aplikacji i ma taką samą nazwę bazową jak plik wykonywalny z rozszerzeniem. config. Na przykład plik konfiguracyjny C:\Program Files\Myapp\Myapp.exe ma wartość C:\Program Files\Myapp\Myapp.exe.config. W scenariuszu opartym na przeglądarce plik HTML musi używać linku  **\<>** elementu, aby jawnie wskazywał plik konfiguracyjny.  
  
 Poniższy kod zawiera prosty przykład pliku konfiguracyjnego aplikacji. Ten przykład dodaje <xref:System.Diagnostics.TextWriterTraceListener> <xref:System.Diagnostics.Debug.Listeners%2A> do kolekcji, aby włączyć rejestrowanie informacji debugowania do pliku.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
### <a name="publisher-policy-file"></a>Plik zasad wydawcy  
 Po drugie środowisko uruchomieniowe bada plik zasad wydawcy, jeśli taki istnieje. Pliki zasad wydawcy są dystrybuowane przez wydawcę składników jako poprawkę lub aktualizację składnika współużytkowanego. Te pliki zawierają informacje o zgodności wystawione przez wydawcę współużytkowanego składnika, który kieruje odwołanie do zestawu do nowej wersji. W przeciwieństwie do plików konfiguracji aplikacji i komputera, pliki zasad wydawcy są zawarte w własnym zestawie, który musi być zainstalowany w globalnej pamięci podręcznej zestawów.  
  
 Poniżej znajduje się przykładowy plik konfiguracji zasad wydawcy:  
  
```xml  
<configuration>  
    <runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
  
            <dependentAssembly>  
                <assemblyIdentity name="asm6" publicKeyToken="c0305c36380ba429" />   
                <bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0"/>    
            </dependentAssembly>  
  
        </assemblyBinding>  
    </runtime>  
</configuration>  
```  
  
 Aby utworzyć zestaw, można użyć narzędzia [Al. exe (Konsolidator zestawu)](../../../docs/framework/tools/al-exe-assembly-linker.md) z następującym poleceniem:  
  
```  
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0  
```  
  
 `compatkey.dat`jest plikiem klucza o silnej nazwie. To polecenie tworzy zestaw o silnej nazwie, który można umieścić w globalnej pamięci podręcznej zestawów.  
  
> [!NOTE]
> Zasady wydawcy mają wpływ na wszystkie aplikacje korzystające ze współużytkowanego składnika.  
  
 Plik konfiguracji zasad wydawcy zastępuje informacje o wersji, które pochodzą z aplikacji (czyli z manifestu zestawu lub z pliku konfiguracyjnego aplikacji). Jeśli w pliku konfiguracji aplikacji nie ma żadnej instrukcji w celu przekierowania wersji określonej w manifeście zestawu, plik zasad wydawcy zastępuje wersję określoną w manifeście zestawu. Jeśli jednak w pliku konfiguracyjnym aplikacji znajduje się instrukcja przekierowania, zasady wydawcy zastępują tę wersję zamiast określonej w manifeście.  
  
 Plik zasad wydawcy jest używany podczas aktualizowania składnika współużytkowanego i Nowa wersja współużytkowanego składnika powinna być pobierana przez wszystkie aplikacje korzystające z tego składnika. Ustawienia w pliku zasad wydawcy zastępują ustawienia w pliku konfiguracji aplikacji, chyba że plik konfiguracyjny aplikacji wymusza Tryb bezpieczny.  
  
#### <a name="safe-mode"></a>Tryb awaryjny  
 Pliki zasad wydawcy są zwykle jawnie instalowane w ramach dodatku Service Pack lub aktualizacji programu. W przypadku wystąpienia problemu z uaktualnionym składnikiem udostępnionym można zignorować zastąpień w pliku zasad wydawcy przy użyciu trybu awaryjnego. Tryb awaryjny jest określany przez  **\<publisherPolicy Apply Zastosuj = "Yes**&#124;**no"/>** element, który znajduje się tylko w pliku konfiguracji aplikacji. Określa, czy informacje o konfiguracji zasad wydawcy powinny zostać usunięte z procesu powiązania.  
  
 Tryb awaryjny można ustawić dla całej aplikacji lub dla wybranych zestawów. Oznacza to, że można wyłączyć zasady dla wszystkich zestawów, które składają się na aplikację, lub włączyć je dla niektórych zestawów, ale nie dla innych. Aby selektywnie zastosować zasady wydawcy do zestawów, które tworzą aplikację, ustaw  **\<publisherPolicy Apply Zastosuj\=no/>** i określ, które zestawy mają być modyfikowane przy użyciu \<elementu **dependentAssembly** > elementu. Aby zastosować zasady wydawcy do wszystkich zestawów, które składają się na aplikację, ustaw  **\<publisherPolicy Apply\=Zastosuj no/>** bez zależnych elementów zestawu. Aby uzyskać więcej informacji na temat konfiguracji, zobacz [Konfigurowanie aplikacji przy użyciu plików konfiguracyjnych](../../../docs/framework/configure-apps/index.md).  
  
### <a name="machine-configuration-file"></a>Plik konfiguracji komputera  
 Po trzecie środowisko uruchomieniowe sprawdzi plik konfiguracji maszyny. Ten plik o nazwie Machine. config znajduje się na komputerze lokalnym w podkatalogu config katalogu głównego, w którym zainstalowano środowisko uruchomieniowe. Ten plik może być używany przez administratorów do określania ograniczeń powiązania zestawu, które są lokalne dla tego komputera. Ustawienia w pliku konfiguracji komputera mają pierwszeństwo przed wszystkimi innymi ustawieniami konfiguracji; nie oznacza to jednak, że wszystkie ustawienia konfiguracji należy umieścić w tym pliku. Wersja określona przez plik zasad administratora jest końcowa i nie można jej zastąpić. Zastąpienia określone w pliku Machine. config mają wpływ na wszystkie aplikacje. Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Konfigurowanie aplikacji przy użyciu plików konfiguracyjnych](../../../docs/framework/configure-apps/index.md).  
  
<a name="step2"></a>   
## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Krok 2. Sprawdzanie zestawów poprzednio występujących w odwołaniu  
 Jeśli żądany zestaw został również żądany w poprzednich wywołaniach, środowisko uruchomieniowe języka wspólnego używa zestawu, który jest już załadowany. Może to mieć konsekwencje podczas nazewnictwa zestawów tworzących aplikację. Aby uzyskać więcej informacji na temat nazewnictwa zestawów, zobacz [nazwy zestawów](../../../docs/framework/app-domains/assembly-names.md).  
  
 Jeśli poprzednie żądanie dotyczące zestawu nie powiodło się, kolejne żądania dla zestawu nie powiodły się natychmiast, bez próby załadowania zestawu. Począwszy od .NET Framework w wersji 2,0, są buforowane błędy powiązań zestawu, a buforowane informacje są używane do określenia, czy próbować załadować zestaw.  
  
> [!NOTE]
> Aby przywrócić zachowanie .NET Framework wersjami 1,0 i 1,1, które nie zawierały błędów powiązań pamięci podręcznej, Uwzględnij [ \<element disableCachingBindingFailures >](../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) w pliku konfiguracji.  
  
<a name="step3"></a>   
## <a name="step-3-checking-the-global-assembly-cache"></a>Krok 3. Sprawdzanie globalnej pamięci podręcznej zestawów  
 W przypadku zestawów o silnych nazwach proces powiązania jest kontynuowany przez wyszukiwanie w globalnej pamięci podręcznej zestawów. Globalna pamięć podręczna zestawów przechowuje zestawy, które mogą być używane przez kilka aplikacji na komputerze. Wszystkie zestawy w globalnej pamięci podręcznej zestawów muszą mieć silne nazwy.  
  
<a name="step4"></a>   
## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Krok 4. Lokalizowanie zestawu za pomocą baz kodu lub sondowania  
 Po ustaleniu poprawnej wersji zestawu przy użyciu informacji z odwołania do zestawu wywołującego i w plikach konfiguracji i po sprawdzeniu globalnej pamięci podręcznej zestawów (tylko dla zestawów o silnej nazwie), common language środowisko uruchomieniowe próbuje znaleźć zestaw. Proces lokalizowania zestawu obejmuje następujące kroki:  
  
1. Jeśli w pliku konfiguracyjnym aplikacji zostanie znaleziona [ bazakodu>,środowiskouruchomieniowesprawdziokreślonąlokalizację.\<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) Jeśli zostanie znalezione dopasowanie, ten zestaw jest używany i nie odbywa się badanie. Jeśli zestaw nie zostanie tam znaleziony, żądanie powiązania nie powiedzie się.  
  
2. Środowisko uruchomieniowe następnie sondy dla przywoływanego zestawu przy użyciu reguł określonych w dalszej części tej sekcji.  
  
> [!NOTE]
> Jeśli masz wiele wersji zestawu w katalogu i chcesz odwołać się do określonej wersji tego zestawu, musisz użyć `privatePath` [ \<bazowej >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu zamiast atrybutu [ \<sondowania >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu. Jeśli używasz [ \<elementu > sondowania](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) , środowisko uruchomieniowe przestanie sondowania podczas pierwszego znalezienia zestawu zgodnego z prostą nazwą zestawu, niezależnie od tego, czy jest to poprawny odpowiednik, czy nie. Jeśli jest to poprawny odpowiednik, ten zestaw jest używany. Jeśli nie jest to poprawna zgodność, sondowanie zakończy się niepowodzeniem.  
  
### <a name="locating-the-assembly-through-codebases"></a>Lokalizowanie zestawu za pomocą baz kodu  
 Informacje o ścieżce bazowej można podać przy użyciu [ \<kodu bazowej >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracyjnym. Ta baza kodu jest zawsze sprawdzana, zanim środowisko uruchomieniowe próbuje sondować przywoływany zestaw. Jeśli plik zasad wydawcy zawierający ostateczną wersję przekierowania również zawiera [ \<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) bazową > element, który [ \<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) jest podbazową > element jest tym, który jest używany. Na przykład, jeśli plik konfiguracyjny aplikacji określa [ \<bazę kodu >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) , a plik zasad wydawcy, który zastępuje [ \<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) informacje o aplikacji, również określa element bazowej >, użyto bazy kodu > w pliku zasad wydawcy. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)  
  
 Jeśli żadne dopasowanie nie zostanie znalezione w lokalizacji określonej przez [ \<>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element, żądanie powiązania zakończy się niepowodzeniem i nie są podejmowane żadne dalsze kroki. Jeśli środowisko uruchomieniowe określa, że zestaw pasuje do kryteriów zestawu wywołującego, używa tego zestawu. Gdy plik określony przez daną [ \<bazę kodu >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element jest ładowany, środowisko uruchomieniowe sprawdzi, czy nazwa, wersja, kultura i klucz publiczny są zgodne z odwołaniem do zestawu wywołującego.  
  
> [!NOTE]
> Zestawy, do których istnieją odwołania poza katalogiem głównym aplikacji, muszą mieć silne nazwy i muszą być zainstalowane w globalnej pamięci podręcznej zestawów lub określone przy użyciu [ \<bazowej >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.  
  
### <a name="locating-the-assembly-through-probing"></a>Lokalizowanie zestawu za pomocą sondowania  
 Jeśli w pliku konfiguracyjnym aplikacji nie [ \<ma kodu bazowej >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) , sondy środowiska uruchomieniowego dla zestawu przy użyciu czterech kryteriów:  
  
- Baza aplikacji, która jest lokalizacją główną, w której jest wykonywana aplikacja.  
  
- Kultura, która jest atrybutem kultury zestawu, którego dotyczy odwołanie.  
  
- Nazwa, która jest nazwą przywoływanego zestawu.  
  
- Atrybut elementu > sondowania, który jest zdefiniowana przez użytkownika lista podkatalogów w lokalizacji głównej. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) `privatePath` Tę lokalizację można określić w pliku konfiguracji aplikacji oraz w kodzie zarządzanym przy użyciu <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> właściwości domeny aplikacji. Gdy jest określony w kodzie zarządzanym, kod `privatePath` zarządzany jest najpierw sondowany, a następnie ścieżką określoną w pliku konfiguracyjnym aplikacji.  
  
#### <a name="probing-the-application-base-and-culture-directories"></a>Badanie katalogów podstawowych aplikacji i kultur  
 Środowisko uruchomieniowe zawsze rozpoczyna sondowanie w bazie aplikacji, która może być adresem URL lub katalogiem głównym aplikacji na komputerze. Jeśli zestaw, do którego się odwoływano, nie został znaleziony w bazie aplikacji i nie podano informacji o kulturze, środowisko uruchomieniowe przeszukuje wszystkie podkatalogi z nazwą zestawu. Dostępne są następujące katalogi:  
  
 [baza aplikacji]/[nazwa zestawu]. dll  
  
 [baza aplikacji]/[nazwa zestawu]/[nazwa zestawu]. dll  
  
 Jeśli dla przywoływanego zestawu określono informacje o kulturze, są badane tylko następujące katalogi:  
  
 [baza aplikacji]/[kultura]/[nazwa zestawu]. dll  
  
 [baza aplikacji]/[kultura]/[nazwa zestawu]/[nazwa zestawu]. dll  
  
#### <a name="probing-with-the-privatepath-attribute"></a>Badanie przy użyciu atrybutu privatePath  
 Oprócz podkatalogów kultury i podkatalogów o nazwie dla przywoływanego zestawu, środowisko uruchomieniowe również sonduje katalogi określone przy użyciu `privatePath` atrybutu > elementu do [ \<sondowania](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) . Katalogi określone przy użyciu `privatePath` atrybutu muszą być podkatalogami katalogu głównego aplikacji. Przeanalizowane katalogi różnią się w zależności od tego, czy informacje o kulturze są zawarte w przywoływanym żądaniu zestawu.  
  
 Środowisko uruchomieniowe przerywa sondowanie przy pierwszym znalezieniu zestawu zgodnego z prostą nazwą zestawu, niezależnie od tego, czy jest to poprawna zgodność, czy nie. Jeśli jest to poprawny odpowiednik, ten zestaw jest używany. Jeśli nie jest to poprawna zgodność, sondowanie zakończy się niepowodzeniem.  
  
 Jeśli jest uwzględniana kultura, następujące katalogi są badane:  
  
 [baza aplikacji]/[binpath]/[kultura]/[nazwa zestawu]. dll  
  
 [baza aplikacji]/[binpath]/[kultura]/[nazwa zestawu]/[nazwa zestawu]. dll  
  
 Jeśli informacje o kulturze nie są uwzględniane, badane są następujące katalogi:  
  
 [baza aplikacji]/[binpath]/[nazwa zestawu]. dll  
  
 [baza aplikacji]/[binpath]/[nazwa zestawu]/[nazwa zestawu]. dll  
  
#### <a name="probing-examples"></a>Przykłady dotyczące sondowania  
 Uwzględniając następujące informacje:  
  
- Nazwa zestawu, do którego istnieje odwołanie: zestaw  
  
- Katalog główny aplikacji:`http://www.code.microsoft.com`  
  
- > elementu do sondowania w pliku konfiguracji określa: bin [ \<](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)  
  
- Kultura: de  
  
 Środowisko uruchomieniowe sonduje następujące adresy URL:  
  
 `http://www.code.microsoft.com/de/myAssembly.dll`
  
 `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`
  
 `http://www.code.microsoft.com/bin/de/myAssembly.dll`
  
 `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`
  
##### <a name="multiple-assemblies-with-the-same-name"></a>Wiele zestawów o tej samej nazwie  
 Poniższy przykład pokazuje, jak skonfigurować wiele zestawów o tej samej nazwie.  
  
```xml  
<dependentAssembly>  
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />   
   <codeBase version="1.0.0.0" href="v1/Server.dll" />  
   <codeBase version="2.0.0.0" href="v2/Server.dll" />  
</dependentAssembly>  
```  
  
#### <a name="other-locations-probed"></a>Inne lokalizacje z sondą  
 Lokalizację zestawu można także określić przy użyciu bieżącego kontekstu powiązania. Najczęściej zdarza się to, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> gdy metoda jest używana i w scenariuszach międzyoperacyjności modelu com. Jeśli zestaw używa <xref:System.Reflection.Assembly.LoadFrom%2A> metody do odwoływania się do innego zestawu, lokalizacja zestawu wywołującego jest uważana za wskazówkę, gdzie znaleźć przywoływany zestaw. Jeśli zostanie znalezione dopasowanie, ten zestaw zostanie załadowany. Jeśli nie zostanie znalezione dopasowanie, środowisko uruchomieniowe kontynuuje działanie z użyciem jego semantyki wyszukiwania, a następnie wysyła zapytanie do Instalator Windows, aby zapewnić zestaw. Jeśli nie dostarczono żadnego zestawu zgodnego z żądaniem powiązania, zostanie zgłoszony wyjątek. Ten wyjątek jest <xref:System.TypeLoadException> w kodzie zarządzanym, jeśli istnieje odwołanie do typu <xref:System.IO.FileNotFoundException> lub nie znaleziono zestawu.  
  
 Na przykład jeśli Assembly1 odwołuje się do Assembly2 i Assembly1 zostało `http://www.code.microsoft.com/utils`pobrane z, Ta lokalizacja jest uważana za wskazówkę, gdzie znaleźć Assembly2. dll. Środowisko uruchomieniowe następnie sonduje zestaw w `http://www.code.microsoft.com/utils/Assembly2.dll` i. `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll` Jeśli Assembly2 nie zostanie znaleziony w żadnej z tych lokalizacji, środowisko uruchomieniowe wyśle zapytanie do Instalator Windows.  
  
## <a name="see-also"></a>Zobacz także

- [Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Wdrażanie](../../../docs/framework/deployment/index.md)
