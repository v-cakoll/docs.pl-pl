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
ms.openlocfilehash: 867bf0812e54c33dbe84737b67091fc87e3b0651
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661870"
---
# <a name="how-the-runtime-locates-assemblies"></a>Sposoby lokalizowania zestawów przez środowisko uruchomieniowe
Aby pomyślnie wdrożyć aplikacji środowiska .NET Framework, trzeba zrozumieć, jak środowisko uruchomieniowe języka wspólnego lokalizuje i wiąże się do zestawów, które składają się na aplikację. Domyślnie środowisko uruchomieniowe podejmuje próbę powiązania z dokładną wersją zestawu, który aplikacja została skompilowana przy użyciu. To zachowanie domyślne można przesłonić, ustawień pliku konfiguracji.  
  
 Środowisko uruchomieniowe języka wspólnego wykonuje kilka kroków, podczas próby zlokalizowania zestawu i rozwiązać odwołania do zestawu. Każdy krok jest szczegółowo opisane w poniższych sekcjach. Sondowanie termin jest często używana, gdy opisujące, jak środowisko uruchomieniowe lokalizuje zestawy; odwołuje się do zestawu algorytmów heurystycznych używana do lokalizowania zestawów na podstawie jego nazwy i kultury.  
  
> [!NOTE]
>  Informacje o powiązaniu można wyświetlić w pliku dziennika, używając [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), który znajduje się w [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
## <a name="initiating-the-bind"></a>Inicjowanie powiązania  
 Rozpocznie się proces lokalizowania i powiązanie zestawu, gdy środowisko uruchomieniowe próbuje rozpoznać odwołania do innego zestawu. Ta dokumentacja może być statyczne lub dynamiczne. Kompilator odwołań statycznych rekordów w metadanych manifestu zestawu w czasie kompilacji. Odwołania dynamiczne są zbudowane na bieżąco w wyniku wywołania różnych metod, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
 Preferowanym sposobem odwołanie do zestawu jest używać pełną dokumentację, w tym nazwę zestawu, wersji, kulturę i token klucza publicznego (jeśli istnieje). Środowisko wykonawcze używa tych informacji do lokalizowania zestawów, wykonując kroki opisane w dalszej części w tej sekcji. Środowisko wykonawcze używa tego samego procesu rozpoznawania niezależnie od tego, czy odwołanie do zestawu statyczne lub dynamiczne.  
  
 Należy również wybrać dynamiczny odwołania do zestawu, udostępniając wywoływania metody tylko częściowe informacje o zestawie, takich jak określanie tylko nazwę zestawu. W tym przypadku katalogu aplikacji jest wyszukiwana w zestawie, a nie inne sprawdzanie jest wykonywane. Wprowadzić częściowe odwołanie przy użyciu dowolnej z różnych metod, takich jak ładowanie zestawów <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>.  
  
 Na koniec można zrobić Odnośnik dynamicznych przy użyciu metody, takie jak <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> i zapewnia tylko częściowe informacje; następnie kwalifikujesz się do odwołania, za pomocą [ \<qualifyassembly — >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) elementu w aplikacji plik konfiguracji. Ten element umożliwia podanie pełne informacje (nazwę, wersję, kulturę i, jeśli ma to zastosowanie, token klucza publicznego) w pliku konfiguracyjnym aplikacji zamiast w kodzie. Należy użyć tej techniki Chcąc pełnej kwalifikacji odwołania do zestawu poza katalogiem aplikacji lub jeśli chcesz odwołać się do zestawu w globalnej pamięci podręcznej, ale potrzebowała wygodę określający pełną dokumentację w plik konfiguracji zamiast w kodzie.  
  
> [!NOTE]
>  Nie można używać tego rodzaju częściowe odwołanie za pomocą zestawów, które są współużytkowane przez kilka aplikacji. Ponieważ ustawienia konfiguracji są stosowane na aplikację, a nie zestaw, zestaw współużytkowany przy użyciu tego typu częściowe odwołanie wymagałoby każdej aplikacji przy użyciu zestaw współużytkowany kwalifikacji informacje znajdują się w jego pliku konfiguracji.  
  
 Środowisko wykonawcze używa następujące kroki, aby rozwiązać odwołania do zestawu:  
  
1.  [Określa wersję poprawny zestaw](#step1) , sprawdzając właściwych plików konfiguracji, w tym pliku konfiguracji aplikacji, plik zasad wydawcy i plik konfiguracji komputera. Jeśli plik konfiguracji znajduje się na komputerze zdalnym, środowisko uruchomieniowe należy zlokalizować i najpierw pobrać plik konfiguracji aplikacji.  
  
2.  [Sprawdza, czy nazwa zestawu została powiązana z przed](#step2) i jeśli tak, korzysta z wcześniej załadowanych zestawów. Jeśli poprzednie żądanie załadowania zestawu nie powiodło się żądanie nie powiodło się natychmiast bez próby załadowania zestawu.  
  
    > [!NOTE]
    >  Buforowanie niepowodzenia powiązań zestawu jest nowa w .NET Framework w wersji 2.0.  
  
3.  [Sprawdza, czy global assembly cache](#step3). Jeśli zestaw zostanie znaleziony istnieje, środowisko wykonawcze używa tego zestawu.  
  
4.  [Sondy dla zestawu](#step4) wykonując następujące czynności:  
  
    1.  Jeśli zasady konfiguracji i wydawca nie wpływają na pierwotne odniesienie, a żądania powiązania został utworzony przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody, środowisko uruchomieniowe sprawdza, czy wskazówki dotyczące lokalizacji.  
  
    2.  Jeśli baza kodu znajduje się w plikach konfiguracji, środowisko uruchomieniowe sprawdza tylko w tej lokalizacji. Jeśli sonda nie powiedzie się, środowisko wykonawcze określa, że żądania powiązania nie powiodło się, a nie inne sondowanie występuje.  
  
    3.  Sondy dla zestawu przy użyciu algorytmów heurystycznych opisanego w [sondowania, sekcja](#step4). Jeśli zestaw nie zostanie znaleziony po badania, środowisko uruchomieniowe zażąda Instalatora Windows, aby zapewnić zestawu. Jest to zabezpieczenie jako funkcja instalacji na żądanie.  
  
        > [!NOTE]
        >  Wersja sprawdzania pod kątem zestawy bez silnej nazwy nie jest ani środowisko uruchomieniowe sprawdza w globalnej pamięci podręcznej zestawy bez silnej nazwy.  
  
<a name="step1"></a>   
## <a name="step-1-examining-the-configuration-files"></a>Krok 1. Przeglądanie plików konfiguracji  
 Zachowanie powiązań zestawów, można skonfigurować na różnych poziomach w oparciu o trzy pliki XML:  
  
-   Plik konfiguracji aplikacji.  
  
-   Plik zasad wydawcy.  
  
-   Plik konfiguracji komputera.  
  
 Te pliki, postępuj zgodnie z tej samej składni i podać informacje takie jak przekierowania, lokalizację kodu, powiązań i powiązania tryby dla danego zestawów. Każdy plik konfiguracji może zawierać [ \<assemblyBinding > element](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) który przekierowuje proces wiązania. Elementy podrzędne [ \<assemblyBinding > element](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) obejmują [ \<dependentAssembly > element](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md). Elementy podrzędne [ \<dependentAssembly > element](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) obejmują [ \<assemblyIdentity > element](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), [ \<bindingRedirect > element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)i [ \<codeBase > element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).  
  
> [!NOTE]
>  Informacje o konfiguracji można znaleźć w plikach konfiguracyjnych trzy; nie wszystkie elementy są prawidłowe we wszystkich plikach konfiguracji. Na przykład powiązanie tryb i informacje o ścieżce prywatnej można tylko w pliku konfiguracyjnym aplikacji. Aby uzyskać pełną listę informacji, który znajduje się w każdym pliku, zobacz [Konfigurowanie aplikacji przy użyciu plików konfiguracyjnych](../../../docs/framework/configure-apps/index.md).  
  
### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji  
 Środowisko uruchomieniowe języka wspólnego sprawdza najpierw, pliku konfiguracji aplikacji, aby uzyskać informacje, które zastępuje informacje o wersji przechowywanych w manifeście zestawu wywołującego. Plik konfiguracji aplikacji można wdrożyć za pomocą aplikacji, ale nie jest wymagany do wykonania aplikacji. Pobieranie tego pliku jest zazwyczaj niemal natychmiast, ale w sytuacjach, gdzie podstawa aplikacji jest na komputerze zdalnym, takie jak w scenariuszu z programu Internet Explorer na podstawie pliku konfiguracji należy go najpierw pobrać.  
  
 Dla plików wykonywalnych klienta pliku konfiguracji aplikacji znajduje się w tym samym katalogu co plik wykonywalny aplikacji i ma taką samą nazwę jak plik wykonywalny z dołączonym rozszerzeniem .config. Na przykład plik konfiguracji C:\Program Files\Myapp\Myapp.exe jest C:\Program Files\Myapp\Myapp.exe.config. W przypadku scenariusza opartego na przeglądarce, należy użyć pliku HTML  **\<link >** element, aby jawnie wskazać plik konfiguracji.  
  
 Poniższy kod stanowi prosty przykład plik konfiguracji aplikacji. Ten przykład dodaje <xref:System.Diagnostics.TextWriterTraceListener> do <xref:System.Diagnostics.Debug.Listeners%2A> kolekcji, aby włączyć rejestrowanie informacji debugowania do pliku.  
  
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
 Po drugie środowisko uruchomieniowe sprawdza, czy plik zasad wydawcy, jeśli taka istnieje. Pliki zasad wydawcy są dystrybuowane przez wydawcę składnika jako poprawki lub aktualizacji, aby współużytkowanego składnika. Te pliki zawierają informacje o zgodności wydany przez wydawcę współużytkowanego składnika, który kieruje odwołania do zestawu do nowej wersji. W przeciwieństwie do aplikacji i plików konfiguracji maszyny pliki zasad wydawcy znajdują się w ich własnych zestawu, który musi być zainstalowany w globalnej pamięci podręcznej.  
  
 Oto przykładowy plik konfiguracji zasad wydawcy:  
  
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
  
 Aby utworzyć zespół, można użyć [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md) narzędzie za pomocą polecenia podobny do następującego:  
  
```  
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0  
```  
  
 `compatkey.dat` jest plik klucza o silnej nazwie. To polecenie tworzy zestaw o silnej nazwie, który można umieścić w globalnej pamięci podręcznej.  
  
> [!NOTE]
>  Zasady wydawcy ma wpływ na wszystkie aplikacje, które używają składnika współużytkowanego.  
  
 Plik konfiguracji zasad wydawcy zastępuje informacje o wersji, który pochodzi z aplikacji (czyli z manifestu zestawu lub pliku konfiguracji aplikacji). Jeśli nie ma żadnego oświadczenia w pliku konfiguracyjnym aplikacji, aby przekierować wersja określona w manifeście zestawu, plik zasad wydawcy zastępuje wersja określona w manifeście zestawu. Jednak w przypadku przekierowania instrukcja w pliku konfiguracyjnym aplikacji, zasady wydawcy zastępuje tę wersję, a nie określona w manifeście.  
  
 Plik zasad wydawcy jest używany, gdy współużytkowany składnik jest aktualizowana, a nową wersję składnika współużytkowanego powinny zostać pobrana przez wszystkie aplikacje używające tego składnika. Ustawienia w pliku zasad wydawcy przesłonić ustawienia w pliku konfiguracyjnym aplikacji, chyba, że plik konfiguracyjny aplikacji wymusza tryb awaryjny.  
  
#### <a name="safe-mode"></a>Tryb awaryjny  
 Pliki zasad wydawcy zazwyczaj jawnie są instalowane w ramach usługi aktualizacji pakietu lub programu. Jeśli występuje problem z uaktualnionego współużytkowanego składnika, możesz zignorować przesłonięć w trybie awaryjnym plik zasad wydawcy. Tryb awaryjny jest określana przez  **\<zastosować publisherPolicy = "tak**&#124;**nie" / >** elementu, znajduje się tylko w pliku konfiguracyjnym aplikacji. Określa, czy informacje o konfiguracji zasad wydawcy, powinny zostać usunięte z proces wiązania.  
  
 Tryb awaryjny można ustawić dla całej aplikacji lub dla wybranych zestawów. Oznacza to możesz wyłączyć zasady dla wszystkich zestawów, które tworzą aplikację lub włącz ją dla niektórych zestawów, ale innych nie. Aby wybiórczo zastosować zasady wydawcy do zestawów tworzących aplikację, należy ustawić  **\<zastosować publisherPolicy\=nie / >** i określić zestawy, które mają zostać zmienione, za pomocą \< **dependentAssembly**> element. Aby zastosować zasady wydawcy do wszystkich zestawów, które tworzą aplikację, należy ustawić  **\<zastosować publisherPolicy\=nie / >** bez elementów zestawu zależnego. Aby uzyskać więcej informacji o konfiguracji, zobacz [Konfigurowanie aplikacji za pomocą plików konfiguracji](../../../docs/framework/configure-apps/index.md).  
  
### <a name="machine-configuration-file"></a>Plik konfiguracji komputera  
 Po trzecie środowisko uruchomieniowe sprawdza, czy plik konfiguracji komputera. Ten plik o nazwie Machine.config — znajduje się na komputerze lokalnym w podkatalogu Config katalog główny, w którym zainstalowano środowiska wykonawczego. Ten plik może służyć przez administratorów do określenia zestawu powiązania ograniczenia, które są lokalne na tym komputerze. Ustawienia w pliku konfiguracji komputera mają pierwszeństwo przed wszystkie inne ustawienia konfiguracji; jednak oznacza to, że wszystkie ustawienia konfiguracji należy umieścić w tym pliku. Wersja określona przez plik zasad administrator jest ostateczne i nie może być zastąpiona. Określone w pliku Machine.config zastąpienia wpływają na wszystkie aplikacje. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie aplikacji za pomocą plików konfiguracji](../../../docs/framework/configure-apps/index.md).  
  
<a name="step2"></a>   
## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Krok 2. Sprawdzanie wcześniej zestawów występujących w odwołaniu  
 Jeśli żądany zestaw zażądano również w poprzednich wywołań, środowisko uruchomieniowe języka wspólnego używa zestawu, który jest już załadowany. Podczas nadawania nazw zestawów tworzących aplikację, może to mieć konsekwencje. Aby uzyskać więcej informacji na temat nazewnictwa zestawów, zobacz [nazw zestawów](../../../docs/framework/app-domains/assembly-names.md).  
  
 Jeśli poprzednie żądanie dla zestawu nie powiodło się, kolejne żądania dla zestawu są nie powiodło się natychmiast bez próby załadowania zestawu. Począwszy od programu .NET Framework w wersji 2.0, niepowodzenia powiązań zestawu są buforowane i buforowane informacje są używane do określenia, czy podejmie próbę załadowania zestawu.  
  
> [!NOTE]
>  Aby przywrócić działanie programu .NET Framework w wersji 1.0 i 1.1, który nie pamięci podręcznej niepowodzenia powiązań, należy dołączyć [ \<disablecachingbindingfailures — > Element](../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) w pliku konfiguracji.  
  
<a name="step3"></a>   
## <a name="step-3-checking-the-global-assembly-cache"></a>Krok 3. Sprawdzanie globalnej pamięci podręcznej  
 W przypadku zestawów o silnych nazwach powiązania proces jest kontynuowany przez wyszukiwanie w globalnej pamięci podręcznej. Global assembly cache przechowuje zestawy, które mogą być używane przez kilka aplikacji na komputerze. Wszystkie zestawy w globalnej pamięci podręcznej muszą mieć silnej nazwy.  
  
<a name="step4"></a>   
## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Krok 4. Lokalizowanie zestawu za pośrednictwem ścieżek bazowych kodu lub sondowanie  
 Po określeniu wersji poprawny zestaw, korzystając z informacji w odwołaniu do wywołującego zestawu i w plikach konfiguracji, a po jego zaewidencjonowanego w globalnej pamięci podręcznej (tylko w przypadku zestawu o silnych nazwach), języka wspólnego środowisko uruchomieniowe próbuje znaleźć zestawu. Proces lokalizowania zestawów obejmuje następujące czynności:  
  
1.  Jeśli [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element zostanie znaleziony w pliku konfiguracyjnym aplikacji, środowisko uruchomieniowe sprawdza określonej lokalizacji. Jeśli zostanie znalezione dopasowanie, że zestaw jest używany i badania nie występuje. Jeśli zestaw nie zostaną znalezione, żądania powiązania nie powiedzie się.  
  
2.  Środowisko uruchomieniowe następnie sondy dla przywoływanego zestawu za pomocą reguł określonych w dalszej części w tej sekcji.  
  
> [!NOTE]
>  Jeśli masz wiele wersji zestawu w katalogu i chcesz odwoływać się do konkretnej wersji tego zestawu, należy użyć [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu zamiast `privatePath` atrybutu [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu. Jeśli używasz [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu, środowisko uruchomieniowe zatrzymuje sondowanie znajdzie zestawu, który jest zgodna z nazwą prostego zestawu, do których odwołuje się, czy jest poprawny dopasowania po raz pierwszy. Jeśli jest to poprawne dopasowanie, tego zestawu jest używana. Jeśli nie ma prawidłowego dopasowania sondowanie zatrzymuje i powiązanie kończy się niepowodzeniem.  
  
### <a name="locating-the-assembly-through-codebases"></a>Lokalizowanie zestawu za pośrednictwem ścieżek bazowych kodu.  
 Codebase informacje mogą być dostępne za pomocą [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu w pliku konfiguracji. Ta baza kodu zawsze jest sprawdzany, zanim spróbuje sondowania dla przywoływanego zestawu środowisko uruchomieniowe. Jeśli zawiera plik zasad wydawcy, która zawiera także przekierowania ostatecznej wersji [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu, który [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element jest ten, który jest używany. Na przykład, jeśli plik konfiguracji aplikacji Określa [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu, a plik zasad wydawcy, która zastępuje informacje o aplikacji określa również [ \< codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element w pliku zasad wydawcy, który jest używany.  
  
 Jeśli nie zostanie znalezione dopasowanie w lokalizacji określonej przez [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu, żądanie powiązania nie powiedzie się i nie trzeba wykonywać dalszych czynności są wykonywane. Jeśli środowisko wykonawcze określa, czy zestaw odpowiadającego kryteriom zestawu wywołującego, używa tego zestawu. Gdy plik określony przez dany [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element jest załadowany, środowisko uruchomieniowe sprawdza, aby upewnić się, czy nazwy, wersji, kultury i klucza publicznego były zgodne z wywołującym zestawem przez odwołanie.  
  
> [!NOTE]
>  Przywoływanych zestawach poza katalog główny aplikacji musi mieć silne nazwy i muszą być zainstalowane w globalnej pamięci podręcznej lub określony za pomocą [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.  
  
### <a name="locating-the-assembly-through-probing"></a>Lokalizowanie zestawów za pomocą sondowania  
 W przypadku nie [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu w pliku konfiguracyjnym aplikacji, środowisko uruchomieniowe sondy dla zestawu przy użyciu czterech kryteriów:  
  
-   Podstawy aplikacji, czyli lokalizację katalogu głównego, w którym aplikacja jest wykonywana.  
  
-   Kultura, co jest atrybut kultury przywoływanego zestawu.  
  
-   Nazwa, która jest nazwą przywoływanego zestawu.  
  
-   `privatePath` Atrybutu [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element, który jest zdefiniowany przez użytkownika lista podkatalogach lokalizację katalogu głównego. Tę lokalizację można określić w pliku konfiguracji aplikacji i przy użyciu kodu zarządzanego <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> właściwości domeny aplikacji. Po określeniu w kodzie zarządzanym kodzie zarządzanym `privatePath` jest sondowany najpierw, a następnie ścieżka określona w pliku konfiguracyjnym aplikacji.  
  
#### <a name="probing-the-application-base-and-culture-directories"></a>Sondowanie podstawy aplikacji i katalogów kultury  
 Środowisko uruchomieniowe zawsze rozpoczyna się, sondowanie w podstawowym aplikacji, który może być adresem URL lub katalogu głównego aplikacji na komputerze. Jeśli przywoływany zestaw nie znajduje się w aplikacji, a podano nie informacji o kulturze, środowisko uruchomieniowe przeszukuje podkatalogów z nazwą zestawu. Katalogi sondowany obejmują:  
  
 [baza aplikacji] / [Nazwa zestawu] .dll  
  
 [baza aplikacji] / [Nazwa zestawu] / [Nazwa zestawu] .dll  
  
 Jeśli informacje o ustawieniach kulturowych jest określony dla przywoływanego zestawu, sondowany są tylko następujące katalogi:  
  
 [baza aplikacji] / [kulturze] / [Nazwa zestawu] .dll  
  
 [baza aplikacji] / [kulturze] / [Nazwa zestawu] / [Nazwa zestawu] .dll  
  
#### <a name="probing-with-the-privatepath-attribute"></a>Sondowanie z privatePath atrybutu  
 Oprócz podkatalogów kultury i podkatalogi, o nazwie dla przywoływanego zestawu, środowisko uruchomieniowe również sondy katalogi określone za pomocą `privatePath` atrybutu [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu. Katalogi określone za pomocą `privatePath` atrybut musi być podkatalogi katalogu głównego aplikacji. Katalogi sondowany różnią się w zależności od tego, czy informacje o ustawieniach kulturowych znajduje się w żądaniu przywoływanego zestawu.  
  
 Środowisko uruchomieniowe zatrzymuje sondowanie znajdzie zestawu, który jest zgodna z nazwą prostego zestawu, do których odwołuje się, czy jest poprawny dopasowania po raz pierwszy. Jeśli jest to poprawne dopasowanie, tego zestawu jest używana. Jeśli nie ma prawidłowego dopasowania sondowanie zatrzymuje i powiązanie kończy się niepowodzeniem.  
  
 Jeśli kultury, sondowany są następujące katalogi:  
  
 [baza aplikacji] / [binpath] / [kulturze] / [Nazwa zestawu] .dll  
  
 [baza aplikacji] / [binpath] / [kulturze] / [Nazwa zestawu] / [Nazwa zestawu] .dll  
  
 Jeśli nie dołączono informacje o ustawieniach kulturowych, sondowany są następujące katalogi:  
  
 [baza aplikacji] / [binpath] / [Nazwa zestawu] .dll  
  
 [baza aplikacji] / [binpath] / [Nazwa zestawu] / [Nazwa zestawu] .dll  
  
#### <a name="probing-examples"></a>Sondowanie przykłady  
 Biorąc pod uwagę następujące informacje:  
  
-   Nazwa zestawu odwołania: myAssembly  
  
-   Katalog główny aplikacji: `http://www.code.microsoft.com`  
  
-   [\<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) określa element w pliku konfiguracyjnym: pojemnika  
  
-   Kultura: Niemcy  
  
 Środowisko uruchomieniowe sondy następujące adresy URL:  
  
 `http://www.code.microsoft.com/de/myAssembly.dll`
  
 `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`
  
 `http://www.code.microsoft.com/bin/de/myAssembly.dll`
  
 `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`
  
##### <a name="multiple-assemblies-with-the-same-name"></a>Wiele zestawów o takiej samej nazwie  
 Poniższy przykład pokazuje, jak skonfigurować wiele zestawów o takiej samej nazwie.  
  
```xml  
<dependentAssembly>  
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />   
   <codeBase version="1.0.0.0" href="v1/Server.dll" />  
   <codeBase version="2.0.0.0" href="v2/Server.dll" />  
</dependentAssembly>  
```  
  
#### <a name="other-locations-probed"></a>Inne lokalizacje sondowany  
 Lokalizacja zestawu można również określić, przy użyciu bieżącego kontekstu powiązania. Najczęstszą przyczyną tego błędu podczas <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metoda jest używana w scenariuszach międzyoperacyjne COM. Jeśli zespół korzysta z <xref:System.Reflection.Assembly.LoadFrom%2A> metodę, aby odwoływać się do innego zestawu lokalizacji zestawu wywołującego jest uważany za wskazówkę o tym, gdzie można znaleźć przywoływanego zestawu. Jeśli zostanie znalezione dopasowanie, że zestaw jest ładowany. Jeśli nie zostanie znalezione dopasowanie, środowisko uruchomieniowe będzie kontynuowane przy użyciu jego semantyka wyszukiwania, a następnie kwerendy Instalatora Windows, aby zapewnić zestawu. Jeśli zestawy nie zostanie podana, które odpowiadają żądania powiązania, jest zgłaszany wyjątek. Ten wyjątek jest <xref:System.TypeLoadException> w kodzie zarządzanym, jeśli odwołanie do typu, lub <xref:System.IO.FileNotFoundException> Jeśli ładowany zestaw nie został znaleziony.  
  
 Na przykład, jeśli odwołuje się Assembly1 Assembly2 i Assembly1 została pobrana z `http://www.code.microsoft.com/utils`, czy lokalizacja jest uważany za wskazówkę o tym, gdzie można znaleźć Assembly2.dll. Środowisko uruchomieniowe, a następnie sondy dla zestawu w `http://www.code.microsoft.com/utils/Assembly2.dll` i `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`. Jeśli Assembly2 nie zostanie znaleziony w jednej z tych lokalizacji, środowisko uruchomieniowe wysyła zapytanie do Instalatora Windows.  
  
## <a name="see-also"></a>Zobacz także
- [Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Wdrażanie](../../../docs/framework/deployment/index.md)
