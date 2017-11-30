---
title: "Sposoby lokalizowania zestawów przez środowisko uruchomieniowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f1a4fd55688f03cbd9de2ceb815c49423aff5fad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-the-runtime-locates-assemblies"></a>Sposoby lokalizowania zestawów przez środowisko uruchomieniowe
Aby pomyślnie wdrożyć aplikacji .NET Framework, trzeba zrozumieć, jak środowisko uruchomieniowe języka wspólnego lokalizuje i wiąże zestawy, które składają się na aplikację. Domyślnie środowisko uruchomieniowe próbuje powiązać dokładnej wersji zestawu, który został skompilowany aplikacji. To zachowanie domyślne można przesłonić ustawienia pliku konfiguracji.  
  
 Środowisko uruchomieniowe języka wspólnego wykonuje kilka kroków, podczas próby zlokalizowania zestawu i rozpoznać odwołania do zestawu. Każdy krok jest szczegółowo w poniższych sekcjach. Sondowanie termin jest często używana, gdy opisujące, jak środowisko uruchomieniowe lokalizuje zestawy; odnosi się do zestawu heurystyki używana do lokalizowania zestawów na podstawie jego nazwy i kultury.  
  
> [!NOTE]
>  Informacje o powiązaniu można wyświetlić w pliku dziennika przy użyciu [Podgląd dziennika powiązań zestawów (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), który znajduje się w [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
## <a name="initiating-the-bind"></a>Inicjowanie powiązania  
 Proces lokalizuje i powiązanie z zestawu rozpoczyna się podczas próby rozpoznania odwołania do innego zestawu środowiska wykonawczego. To odwołanie może być statyczne lub dynamiczne. Kompilatora rekordów statycznych odwołań w manifeście zestawu metadanych na czas kompilacji. Dynamiczne odwołania są zbudowane na bieżąco w wyniku wywołania różnych metod, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
 Preferowany sposób odwołanie do zestawu jest Użyj pełną dokumentację, w tym nazwę zestawu, wersję, kulturę i token klucza publicznego (jeśli istnieje). Środowisko uruchomieniowe używa tych informacji można znaleźć zestawu, zgodnie z krokami w dalszej części tej sekcji. Środowisko uruchomieniowe używa tego samego procesu rozpoznawania niezależnie od tego, czy odwołanie do zestawu statyczne lub dynamiczne.  
  
 Należy również wybrać dynamiczne odwołania do zestawu, zapewniając metody wywołującej tylko częściowe informacje o zestawie, takich jak określanie tylko nazwę zestawu. W takim przypadku katalogu aplikacji jest wyszukiwany w zestawie, a nie inne sprawdzanie jest wykonywane. Wprowadź częściowe odwołanie przy użyciu różnych metod ładowania zestawów, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>.  
  
 Na koniec możesz wprowadzić odwołania dynamicznego za pomocą innej metody, takie jak <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> i zawierają tylko częściowe informacje następnie kwalifikacji przy użyciu odwołania [ \<qualifyassembly — >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) elementu w aplikacji plik konfiguracji. Ten element umożliwia podanie informacji pełną dokumentację (nazwę, wersję, kulturę i, jeśli to konieczne, token klucza publicznego) w pliku konfiguracyjnym aplikacji zamiast w kodzie. Czy użyć tej metody, jeśli do pełnej kwalifikacji odwołania do zestawu poza katalogiem aplikacji lub jeśli chcesz odwołanie do zestawu w globalnej pamięci podręcznej zestawów, ale chce wygodne określenie pełną dokumentację w plik konfiguracji zamiast w kodzie.  
  
> [!NOTE]
>  Tego rodzaju częściowe odwołanie nie powinny być stosowane z zestawy, które są współużytkowane przez kilka aplikacji. Ponieważ ustawienia konfiguracji są stosowane dla poszczególnych aplikacji i nie zestawu, zestaw udostępnionego przy użyciu tego typu częściowe odwołanie wymagają każdej aplikacji przy użyciu zestaw udostępnionego posiadanie kwalifikacji informacji w pliku konfiguracji.  
  
 Środowisko uruchomieniowe używa poniższe kroki można rozpoznać odwołania do zestawu:  
  
1.  [Określa wersję zestawu poprawne](#step1) , sprawdzając pliki mające zastosowanie konfiguracji, w tym pliku konfiguracji aplikacji, pliku zasad wydawcy i pliku konfiguracji komputera. Jeśli plik konfiguracji znajduje się na komputerze zdalnym, środowiska uruchomieniowego musi zlokalizować i najpierw pobrać plik konfiguracji aplikacji.  
  
2.  [Sprawdza, czy nazwa zestawu została powiązana z przed](#step2) i jeśli tak, korzysta z wcześniej załadowanego zestawu. Jeśli poprzednie żądanie można załadować zestawu nie powiodła się, żądanie nie powiodło się natychmiast bez podjęto próbę załadowania zestawu.  
  
    > [!NOTE]
    >  Buforowanie niepowodzenia powiązań zestawu jest nowa w programie .NET Framework w wersji 2.0.  
  
3.  [Globalna pamięć podręczna zestawów sprawdza](#step3). Jeśli odnaleziono zestawu, środowisko uruchomieniowe korzysta z tego zestawu.  
  
4.  [Sondy dla zestawu](#step4) wykonując następujące czynności:  
  
    1.  Jeśli zasady konfiguracji i wydawca nie wpływają na oryginalne odwołanie i powiązania zostało utworzone przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody środowiska uruchomieniowego wyszukuje wskazówki lokalizacji.  
  
    2.  Jeśli codebase zostanie znaleziony w plikach konfiguracji, środowisko uruchomieniowe sprawdza tylko w tej lokalizacji. W przypadku niepowodzenia sonda środowiska uruchomieniowego Określa, że żądanie powiązania nie powiodło się, a nie inne sondowanie występuje.  
  
    3.  Sondy dla zestawu przy użyciu algorytmu heurystycznego, opisanego w [sondowanie sekcji](#step4). Jeśli nie odnaleziono zestawu po sondowanie, środowisko uruchomieniowe żądań Instalatora Windows w celu zapewnienia zestawu. To dodatkowe funkcji instalacji na żądanie.  
  
        > [!NOTE]
        >  Wersja sprawdzanie dla zestawów bez silnych nazw nie jest ani środowiska uruchomieniowego sprawdza w pamięci podręcznej GAC dla zestawów bez silnych nazw.  
  
<a name="step1"></a>   
## <a name="step-1-examining-the-configuration-files"></a>Krok 1. Badanie plików konfiguracji  
 Zachowanie wiązania zestawu można skonfigurować na różnych poziomach oparte na trzy pliki XML:  
  
-   Plik konfiguracji aplikacji.  
  
-   Plik zasad wydawcy.  
  
-   Plik konfiguracji maszyny.  
  
 Te pliki wykonaj takiej samej składni i zawierają informacje, takie jak przekierowania, położenie kodu, powiązań i powiązanie tryby dla konkretnego zestawów. Każdy plik konfiguracji może zawierać [ \<assemblybinding — > element](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) który przekierowuje proces wiązania. Elementy podrzędne [ \<assemblybinding — > element](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) obejmują [ \<dependentAssembly > elementu](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md). Elementy podrzędne [ \<dependentAssembly > element](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) obejmują [ \<assemblyIdentity > element](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), [ \<bindingRedirect > element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)i [ \<codeBase > elementu](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).  
  
> [!NOTE]
>  Informacje o konfiguracji można znaleźć w plikach konfiguracji trzy; nie wszystkie elementy są prawidłowe we wszystkich plikach konfiguracji. Na przykład powiązanie trybu i informacje o ścieżce prywatnej można tylko w pliku konfiguracyjnym aplikacji. Aby uzyskać pełną listę informacje zawarte w każdym pliku, zobacz [Konfigurowanie aplikacji przy użyciu plików konfiguracyjnych](../../../docs/framework/configure-apps/index.md).  
  
### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji  
 Środowisko uruchomieniowe języka wspólnego sprawdza najpierw, informacji zastępujący przechowywane w manifeście zestawu wywoływania informacje o wersji pliku konfiguracji aplikacji. Plik konfiguracji aplikacji można wdrożyć przy użyciu aplikacji, ale nie jest wymagana do wykonania aplikacji. Pobieranie tego pliku jest zazwyczaj niemal natychmiast, ale w sytuacjach, gdy baza aplikacji jest na komputerze zdalnym, takich jak w scenariuszu z programu Internet Explorer na podstawie pliku konfiguracji musi zostać pobrana.  
  
 Dla plików wykonywalnych klienta w pliku konfiguracyjnym aplikacji znajduje się w tym samym katalogu co plik wykonywalny aplikacji i ma taką samą nazwę podstawową jako pliku wykonywalnego z rozszerzeniem config. Na przykład pliku konfiguracyjnego C:\Program Files\Myapp\Myapp.exe to C:\Program Files\Myapp\Myapp.exe.config. W przypadku przeglądarki, należy użyć pliku w formacie HTML  **\<link >** element, aby jawnie wskazać plik konfiguracji.  
  
 Następujący kod stanowi przykład pliku konfiguracji aplikacji. W tym przykładzie dodaje <xref:System.Diagnostics.TextWriterTraceListener> do <xref:System.Diagnostics.Debug.Listeners%2A> kolekcji, aby włączyć rejestrowanie informacji o debugowaniu w pliku.  
  
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
 Drugie środowisko uruchomieniowe sprawdza, czy plik zasad wydawcy, jeśli taka istnieje. Pliki zasad wydawcy są dystrybuowane przez wydawcę składnika jako poprawki lub aktualizacji do udostępnionego elementu. Te pliki zawierają informacje o zgodności wydany przez wydawcę składnika współużytkowanego kierujący odwołania do zestawu do nowej wersji. W przeciwieństwie do aplikacji i plików konfiguracji maszyny pliki zasad wydawcy znajdują się w ich własnych zestawu, który musi być zainstalowany w globalnej pamięci podręcznej zestawów.  
  
 Poniżej przedstawiono przykładowy plik konfiguracji zasad wydawcy:  
  
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
  
 Aby utworzyć zestaw, można użyć [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md) narzędzia za pomocą polecenia, takie jak następujące:  
  
```  
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0  
```  
  
 `compatkey.dat`jest to plik klucza silnej nazwy. To polecenie tworzy zestawu o silnej nazwie, w którym można umieścić w globalnej pamięci podręcznej zestawów.  
  
> [!NOTE]
>  Zasady wydawcy ma wpływ na wszystkie aplikacje, które używają udostępnionego składnika.  
  
 Plik konfiguracji zasad wydawcy przesłania informacji o wersji, która pochodzi z aplikacji (czyli z manifestu zestawu lub pliku konfiguracji aplikacji). Jeśli nie ma żadnego oświadczenia w pliku konfiguracji aplikacji, aby przekierować wersja określona w manifeście zestawu, pliku zasad wydawcy przesłania wersja określona w manifeście zestawu. Jednak w przypadku instrukcji przekierowanie w pliku konfiguracyjnym aplikacji zasad wydawcy zastępuje tej wersji zamiast określona w manifeście.  
  
 Plik zasad wydawcy jest używana, gdy jest aktualizowana składnika współużytkowanego i nowa wersja składnika współużytkowanego powinny zostać pobrana przez wszystkie aplikacje używające tego składnika. W pliku zasad wydawcy zastępują ustawienia w pliku konfiguracyjnym aplikacji, chyba że tryb awaryjny wymusza pliku konfiguracji aplikacji.  
  
#### <a name="safe-mode"></a>Tryb awaryjny  
 Pliki zasad wydawcy zazwyczaj jawnie są instalowane w ramach usługi aktualizacji pakietu lub programu. Jeśli występuje problem z uaktualniony składnik udostępnionego, możesz zignorować zastąpień w trybie awaryjnym pliku zasad wydawcy. Tryb awaryjny jest określany przez  **\<zastosować publisherPolicy = "tak**&#124; **nie "/ >** element znajduje się tylko w pliku konfiguracyjnym aplikacji. Określa, czy informacje o konfiguracji zasad wydawcy powinna zostać usunięta z proces wiązania.  
  
 Tryb awaryjny można ustawić dla całej aplikacji lub dla wybranych zestawów. Oznacza to możesz wyłączyć zasady dla wszystkich zestawów, które tworzą aplikacji lub ją włączyć na niektórych zestawy, a innych nie. Aby wybiórczo zastosować zasad wydawcy zestawy, które tworzą aplikacji, ustaw  **\<zastosować publisherPolicy\=nie / >** i określ zestawy, które mają zostać zmienione, przy użyciu \< **dependentAssembly**> elementu. Aby zastosować zasady wydawcy wszystkie zestawy, które tworzą aplikacji, ustaw  **\<zastosować publisherPolicy\=nie / >** z żadnych elementów zestawu zależnego. Aby uzyskać więcej informacji o konfiguracji, zobacz [Konfigurowanie aplikacji za pomocą plików konfiguracji](../../../docs/framework/configure-apps/index.md).  
  
### <a name="machine-configuration-file"></a>Plik konfiguracji maszyny  
 Trzecie środowisko uruchomieniowe sprawdza, czy plik konfiguracji maszyny. Ten plik o nazwie Machine.config, znajduje się na komputerze lokalnym w podkatalogu Config katalogu głównego, w którym zainstalowano środowiska wykonawczego. Ten plik może posłużyć administratorom pozwala określić ograniczenia powiązanie zestawu, które znajdują się lokalnie na tym komputerze. Ustawienia w pliku konfiguracji komputera mają pierwszeństwo przed wszystkie inne ustawienia konfiguracji; jednak nie oznacza to, że wszystkie ustawienia konfiguracji należy umieścić w tym pliku. Wersja określona przez plik zasad administratora jest ostateczny i nie może zostać zastąpiona. Określona w pliku Machine.config zastąpienia wpływają na wszystkie aplikacje. Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [Konfigurowanie aplikacji za pomocą plików konfiguracji](../../../docs/framework/configure-apps/index.md).  
  
<a name="step2"></a>   
## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Krok 2. Sprawdzanie zestawów poprzednio występujących w odwołaniu  
 Jeśli w poprzednim wywołania również zażądano żądany zestaw, środowisko uruchomieniowe języka wspólnego używa zestawu, który został już załadowany. Może to mieć konsekwencje w nazwach zestawów, które tworzą aplikacji. Aby uzyskać więcej informacji na temat nazw zestawów, zobacz [nazwy zestawu](../../../docs/framework/app-domains/assembly-names.md).  
  
 Jeśli poprzednie żądanie dla zestawu nie powiodła się, kolejne żądania dla zestawu są nie powiodło się natychmiast bez podjęto próbę załadowania zestawu. W programie .NET Framework w wersji 2.0, niepowodzenia powiązań zestawu znajdują się w pamięci podręcznej i buforowane informacje są używane do określenia, czy próba załadowania zestawu.  
  
> [!NOTE]
>  Aby przywrócić działanie wersje programu .NET Framework 1.0 i 1.1, który nie pamięci podręcznej niepowodzenia powiązań, obejmują [ \<disablecachingbindingfailures — > elementu](../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) w pliku konfiguracji.  
  
<a name="step3"></a>   
## <a name="step-3-checking-the-global-assembly-cache"></a>Krok 3. Sprawdzanie globalnej pamięci podręcznej zestawów  
 Dla zestawów o silnych nazwach powiązanie proces jest kontynuowany przez wyszukiwanie w globalnej pamięci podręcznej zestawów. Globalna pamięć podręczna zestawów przechowuje zestawy, które mogą być używane przez kilka aplikacji na komputerze. Wszystkie zestawy w globalnej pamięci podręcznej zestawów muszą mieć silnej nazwy.  
  
<a name="step4"></a>   
## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Krok 4. Lokalizowanie zestawu za pośrednictwem ścieżek bazowych kodu lub sondowania  
 Po określeniu wersja zestawu poprawny, korzystając z informacji w odwołaniu do wywołującego zestawu i w plikach konfiguracji, a po jego sprawdzeniu w globalnej pamięci podręcznej zestawów (tylko w przypadku o silnych nazwach zestawów), języka wspólnego środowisko uruchomieniowe próbuje znaleźć zestawu. Proces lokalizowania zestawów obejmuje następujące kroki:  
  
1.  Jeśli [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element zostanie znaleziony w pliku konfiguracyjnym aplikacji Sprawdzanie czasu wykonania określonej lokalizacji. Jeśli zostanie znaleziony dopasowanie, ten zestaw jest używany i badania nie występuje. Zestaw nie zostaną znalezione, żądanie powiązanie kończy się niepowodzeniem.  
  
2.  Środowisko uruchomieniowe następnie sondy dla przywoływanego zestawu przy użyciu reguł określone później w tej sekcji.  
  
> [!NOTE]
>  Jeśli masz wiele wersji zestawu w katalogu i chcesz odwołać konkretnej wersji tego zestawu, należy użyć [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu zamiast `privatePath` atrybutu [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu. Jeśli używasz [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu środowiska uruchomieniowego zatrzymuje sondowanie znajdzie zestawu, który odpowiada nazwie zestawu prostych odwołać się do, czy nie jest on obiektem po raz pierwszy. Jeśli jest poprawny dopasowanie, ten zestaw jest używany. Jeśli nie ma prawidłowego dopasowania sondowanie zatrzymuje i powiązanie kończy się niepowodzeniem.  
  
### <a name="locating-the-assembly-through-codebases"></a>Lokalizowanie zestawów za pośrednictwem Codebases  
 Codebase informacje mogą być dostępne za pomocą [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracji. Ta ścieżka jest zawsze zaznaczone przed środowisko wykonawcze próbuje sondować przywoływanego zestawu. Jeśli plik zasad wydawcy zawiera także przekierowania ostateczną wersją zawiera [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element, który [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element jest elementem, który jest używany. Na przykład, jeśli w pliku konfiguracyjnym aplikacji Określa [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu i pliku zasad wydawcy, który zastępuje informacje o aplikacji określa również [ \< codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) służy element w pliku zasad wydawcy.  
  
 Jeśli nie znaleziono w lokalizacji określonej przez [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu, żądanie bind nie powiedzie się i są pobierane żadne dodatkowe czynności. Jeśli środowisko uruchomieniowe Określa, że zestaw kryteria wywołującego zestawu, używa tego zestawu. Gdy plik określony przez dany [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element został załadowany, środowisko uruchomieniowe sprawdza, aby upewnić się, że nazwy, wersji, kultury i klucz publiczny zgodne wywołującego zestawu do odwołania.  
  
> [!NOTE]
>  Zestawy występujące w odwołaniach poza katalog główny aplikacji musi mieć silne nazwy i muszą być zainstalowane w globalnej pamięci podręcznej zestawów lub podana przy użyciu [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.  
  
### <a name="locating-the-assembly-through-probing"></a>Lokalizowanie zestawów za pośrednictwem sondowanie  
 W przypadku nie [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu w pliku konfiguracyjnym aplikacji, środowisko uruchomieniowe sondy dla zestawu przy użyciu czterech kryteriów:  
  
-   Baza aplikacji jest lokalizację katalogu głównego, w którym aplikacja jest wykonywana.  
  
-   Kultura, który jest atrybutem kultury jest odwołanie do zestawu.  
  
-   Nazwa, która jest nazwą zestawu, do którego istnieje odwołanie.  
  
-   `privatePath` Atrybutu [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element, który jest zdefiniowany przez użytkownika lista podkatalogi znajdujące się w lokalizacji głównej. Tej lokalizacji można określić w pliku konfiguracyjnym aplikacji i za pomocą kodu zarządzanego <xref:System.AppDomain.AppendPrivatePath%2A> właściwości dla domeny aplikacji. Jeśli określona w kodzie zarządzanym kodu zarządzanego `privatePath` jest najpierw sondowany, następuje ścieżka określona w pliku konfiguracyjnym aplikacji.  
  
#### <a name="probing-the-application-base-and-culture-directories"></a>Sondowanie baza aplikacji i kultury katalogów  
 Środowisko uruchomieniowe zawsze rozpoczyna sondowanie w podstawowej aplikacji, który może być adresem URL lub katalog główny aplikacji na komputerze. Jeśli podano nie informacji o kulturze przywoływanego zestawu nie znajduje się w bazie danych aplikacji, środowisko uruchomieniowe wyszukuje podkatalogów z nazwą zestawu. Katalogi sondowany obejmują:  
  
 [baza aplikacji] / [Nazwa zestawu] .dll  
  
 [baza aplikacji] / [Nazwa zestawu] / [Nazwa zestawu] .dll  
  
 Jeśli informacje o ustawieniach kulturowych jest określona dla przywoływanego zestawu, sondowany są tylko następujące katalogi:  
  
 [baza aplikacji] / [kultury] / [Nazwa zestawu] .dll  
  
 [baza aplikacji] / [kultury] / [Nazwa zestawu] / [Nazwa zestawu] .dll  
  
#### <a name="probing-with-the-privatepath-attribute"></a>Sondowanie z privatePath atrybutu  
 Oprócz podkatalogi kultury i podkatalogi o nazwie odpowiadającej przywoływanego zestawu środowiska wykonawczego również sondy katalogi określone za pomocą `privatePath` atrybutu [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu. Katalogi określone za pomocą `privatePath` atrybut musi być podkatalogach katalogu głównego aplikacji. Katalogi sondowany się różnić w zależności od tego, czy informacje o ustawieniach kulturowych znajduje się w żądaniu przywoływanego zestawu.  
  
 Środowisko uruchomieniowe zatrzymuje sondowanie znajdzie zestawu, który odpowiada nazwie zestawu prostych odwołać się do, czy nie jest on obiektem po raz pierwszy. Jeśli jest poprawny dopasowanie, ten zestaw jest używany. Jeśli nie ma prawidłowego dopasowania sondowanie zatrzymuje i powiązanie kończy się niepowodzeniem.  
  
 Jeśli kultury jest włączone, sondowany są następujące katalogi:  
  
 [baza aplikacji] / [binpath] / [kultury] / [Nazwa zestawu] .dll  
  
 [baza aplikacji] / [binpath] / [kultury] / [Nazwa zestawu] / [Nazwa zestawu] .dll  
  
 Jeśli nie dołączono informacji o kulturze, sondowany są następujące katalogi:  
  
 [baza aplikacji] / [binpath] / [Nazwa zestawu] .dll  
  
 [baza aplikacji] / [binpath] / [Nazwa zestawu] / [Nazwa zestawu] .dll  
  
#### <a name="probing-examples"></a>Sondowanie przykłady  
 Podane następujące informacje:  
  
-   Nazwa przywoływanego zestawu: myAssembly  
  
-   Katalog główny aplikacji: http://www.code.microsoft.com  
  
-   [\<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) określa element w pliku konfiguracyjnym: bin  
  
-   Kultura: de  
  
 Środowisko uruchomieniowe sondy następujące adresy URL:  
  
 http://www.code.microsoft.com/de/myAssembly.dll  
  
 http://www.code.microsoft.com/de/myAssembly/myAssembly.dll  
  
 http://www.code.microsoft.com/bin/de/myAssembly.dll  
  
 http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll  
  
##### <a name="multiple-assemblies-with-the-same-name"></a>Wiele zestawów o takiej samej nazwie  
 Poniższy przykład przedstawia sposób konfigurowania wielu zestawów o takiej samej nazwie.  
  
```xml  
<dependentAssembly>  
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />   
      <codeBase version="1.0.0.0" href="v1/Server.dll"/>  
      <codeBase version="2.0.0.0" href="v2/Server.dll"/>  
</dependentAssembly>  
```  
  
#### <a name="other-locations-probed"></a>Inne lokalizacje sondowany  
 Lokalizacji zestawu można również określić, używając bieżącego kontekstu powiązania. Najczęstszą przyczyną tego błędu podczas <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metoda jest używana w scenariuszach międzyoperacyjnego COM. Jeśli zestaw używa <xref:System.Reflection.Assembly.LoadFrom%2A> metody odwołać się do innego zestawu lokalizacji wywołującego zestawu jest traktowany jako wskazówka o tym, gdzie można znaleźć przywoływanego zestawu. Jeśli zostanie znaleziony dopasowanie, że zestaw jest ładowany. Jeśli nie znaleziono, środowisko uruchomieniowe kontynuuje jego semantyki wyszukiwania, a następnie sprawdza Instalatora Windows w celu zapewnienia zestawu. Jeśli zestawu nie została podana, które odpowiadają żądania powiązanie, jest zwracany wyjątek. Ten wyjątek jest <xref:System.TypeLoadException> w kodzie zarządzanym, jeśli istnieje odwołanie do typu, lub <xref:System.IO.FileNotFoundException> Jeśli zestaw ładowany nie został znaleziony.  
  
 Na przykład zestaw1 został pobrany z http://www.code.microsoft.com/utils zestaw1 odwołuje się do Assembly2, tej lokalizacji jest uważany za wskazówkę o tym, gdzie można znaleźć Assembly2.dll. Środowisko uruchomieniowe następnie badania zestawu w http://www.code.microsoft.com/utils/Assembly2.dll i http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll. Jeśli Assembly2 nie zostanie znaleziony w jednej z tych lokalizacji, środowisko uruchomieniowe wysyła zapytanie do Instalatora Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 [Wdrożenia](../../../docs/framework/deployment/index.md)
