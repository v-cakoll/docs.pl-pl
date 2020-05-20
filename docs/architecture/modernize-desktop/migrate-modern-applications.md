---
title: Migrowanie nowoczesnych aplikacji klasycznych
description: Wszystko, czego potrzebujesz, aby poznać proces migracji nowoczesnych aplikacji klasycznych.
ms.date: 05/12/2020
ms.openlocfilehash: 2108aa0b99cabfbb0f3263f094ba8277f953ed6a
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423300"
---
# <a name="migrating-modern-desktop-applications"></a>Migrowanie nowoczesnych aplikacji klasycznych

W tym rozdziale poznasz najczęstsze problemy i wyzwania, które można wykorzystać podczas migrowania istniejącej aplikacji z .NET Framework do platformy .NET Core.

Złożona aplikacja klasyczna nie działa w izolacji i wymaga pewnego rodzaju interakcji z podsystemami, które mogą znajdować się na komputerze lokalnym lub na serwerze zdalnym. Prawdopodobnie będzie potrzebny pewien rodzaj bazy danych do łączenia się jako trwałość magazynu lokalnego lub zdalnego. Dzięki wykorzystaniu architektur internetowych i opartych na usługach często aplikacja jest połączona z niektórymi powiązanymi usługami na serwerze zdalnym lub w chmurze. Może być konieczne uzyskanie dostępu do systemu plików komputera w celu zaimplementowania niektórych funkcji. Alternatywnie, może być używana funkcja, która znajduje się wewnątrz obiektu COM poza aplikacją, co jest typowym scenariuszem, jeśli na przykład integrujesz zestawy pakietu Office w aplikacji.

Oprócz tego istnieją różnice w powierzchni interfejsu API, które są udostępniane przez .NET Framework i .NET Core, a niektóre funkcje, które są dostępne w .NET Framework nie są dostępne w programie .NET Core. W związku z tym ważne jest, aby znać i wziąć pod uwagę podczas planowania migracji.

## <a name="configuration-files"></a>Pliki konfiguracji

Pliki konfiguracji oferują możliwość przechowywania zestawów właściwości, które są odczytywane w czasie wykonywania i wpływają na zachowanie naszych aplikacji, takich jak lokalizowanie bazy danych lub ile razy wykonać pętlę. Estetyki tej techniki polega na modyfikacji niektórych aspektów aplikacji bez konieczności firmy Recode i ponownego kompilowania. Jest to przydatne, gdy na przykład ten sam kod aplikacji jest uruchamiany w środowisku programistycznym z określonym zestawem wartości konfiguracyjnych i w produkcji z inną.

### <a name="configuration-on-net-framework"></a>Konfiguracja na .NET Framework

Jeśli masz działającą .NET Frameworkową aplikację klasyczną, prawdopodobnie masz dostęp do pliku *App. config* za pośrednictwem <xref:System.Configuration.AppSettingsSection> klasy z `System.Configuration` przestrzeni nazw.

W ramach infrastruktury .NET Framework istnieje hierarchia plików konfiguracji, które dziedziczą właściwości z obiektów nadrzędnych. Można znaleźć plik *Machine. config* , który definiuje wiele właściwości i sekcji konfiguracyjnych, które mogą być używane lub zastępowane w dowolnym pliku konfiguracji podrzędnej.

### <a name="configuration-on-net-core"></a>Konfiguracja w programie .NET Core

W świecie .NET Core nie ma pliku *Machine. config* . Mimo że można nadal używać starej <xref:System.Configuration> przestrzeni nazw, można rozważyć przełączenie do nowoczesnej <xref:Microsoft.Extensions.Configuration> , która oferuje dobrą liczbę ulepszeń.

Interfejs API konfiguracji obsługuje koncepcję dostawcy konfiguracji, który definiuje źródło danych do użycia w celu załadowania konfiguracji. Istnieją różne rodzaje wbudowanych dostawców, takie jak:

- Obiekty w pamięci .NET
- Pliki INI
- Pliki JSON
- Pliki XML
- Argumenty wiersza polecenia
- Zmienne środowiskowe
- Zaszyfrowany magazyn użytkowników

 Możesz też utworzyć własne.

Nowa konfiguracja umożliwia listę par nazwa-wartość, które mogą być pogrupowane w hierarchię wielopoziomową. Wszystkie przechowywane wartości są mapowane na ciąg i wbudowana obsługa powiązań, która umożliwia deserializacja ustawień w niestandardowym, starym obiekcie CLR (POCO).

<xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>Obiekt umożliwia dodanie tylu dostawców konfiguracji, które mogą być potrzebne dla aplikacji, przy użyciu reguły pierwszeństwa do rozwiązywania preferencji. W związku z tym ostatni dostawca dodany w kodzie zastąpi pozostałe. Jest to świetna funkcja zarządzania różnymi środowiskami do wykonania, ponieważ można definiować różne konfiguracje dla środowisk programistycznych, testowych i produkcyjnych oraz zarządzać nimi w ramach jednej funkcji w kodzie.

### <a name="migrating-configuration-files"></a>Migrowanie plików konfiguracji

Można nadal korzystać z istniejącego pliku XML App. config. Można jednak skorzystać z tej możliwości, aby przeprowadzić migrację konfiguracji w celu skorzystania z kilku ulepszeń programu .NET Core.

Aby przeprowadzić migrację ze starego pliku *App. config* do nowej konfiguracji, należy wybrać format XML i format JSON.

Jeśli wybierzesz opcję XML, konwersja jest prosta. Ponieważ zawartość jest taka sama, po prostu zmień nazwę pliku *App. config* na plik z rozszerzeniem XML. Następnie Zmień kod, który odwołuje się do AppSettings, aby użyć `ConfigurationBuilder` klasy. Ta zmiana powinna być łatwa.

Jeśli chcesz użyć formatu JSON i nie chcesz migrować ręcznie, istnieje narzędzie o nazwie [dotnet-config2json](https://www.nuget.org/packages/dotnet-config2json/) dostępne na platformie .NET Core, które może skonwertować plik *App. config* do pliku konfiguracji JSON.

W przypadku korzystania z sekcji konfiguracyjnych, które zostały zdefiniowane w pliku *Machine. config* , mogą występować również problemy. Rozważmy na przykład następującą konfigurację:

```xml
<configuration>
    <system.diagnostics>
        <switches>
            <add name="General" value="4" />
        </switches>
        <trace autoflush="true" indentsize="2">
            <listeners>
                <add name="myListener"
                     type="System.Diagnostics.TextWriterTraceListener,
                           System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
                     initializeData="MyListener.log"
                     traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />
            </listeners>
        </trace>
    </system.diagnostics>
</configuration>
```

Jeśli ta konfiguracja zostanie pobrana do programu .NET Core, zostanie wyświetlony wyjątek:

Nierozpoznana sekcja konfiguracji system. Diagnostics

Ten wyjątek występuje, ponieważ ta sekcja i zestaw odpowiedzialny za obsługę tej sekcji został zdefiniowany w pliku *Machine. config* , który już nie istnieje.

Aby łatwo rozwiązać ten problem, można skopiować definicję sekcji ze starego pliku *Machine. config* do nowej konfiguracji:

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a>Uzyskiwanie dostępu do baz danych

Prawie każda aplikacja klasyczna wymaga pewnego rodzaju bazy danych. W przypadku komputerów stacjonarnych często można znaleźć architektury klient-serwer z bezpośrednim połączeniem między aplikacją klasyczną a aparatem bazy danych. Te bazy danych mogą być lokalne lub zdalne w zależności od potrzeb udostępniania informacji między różnymi użytkownikami.

Z punktu widzenia kodu istniały wiele technologii i struktur, które umożliwiają deweloperom łączenie się z bazą danych, wykonywanie zapytań i aktualizowanie ich.

Najczęstszymi przykładami bazy danych, które można znaleźć w przypadku aplikacji klasycznych systemu Windows, są Microsoft Access i Microsoft SQL Server. Jeśli masz ponad 20 lat programowania doświadczenia dla pulpitu, nazwy takie jak ODBC, OLEDB, RDO, ADO, ADO.NET, LINQ i Entity Framework będą wyglądały na dźwięk.

### <a name="odbc"></a>ODBC

Można nadal korzystać z ODBC na platformie .NET Core, ponieważ firma Microsoft udostępnia `System.Data.Odbc` bibliotekę zgodną z .NET Standard 2,0.

### <a name="ole-db"></a>OLE DB

[OLE DB](https://msdn.microsoft.com/library/ms722784(v=vs.85).aspx)   był doskonałym sposobem na dostęp do różnych źródeł danych w jednolity sposób. Jednak była oparta na modelu COM, który jest technologią tylko dla systemu Windows i dlatego nie jest najlepszym rozwiązaniem dla technologii międzyplatformowych, takich jak .NET Core. Jest on również nieobsługiwany w SQL Server wersji 2014 i nowszych. Z tego powodu OLE DB nie będą obsługiwane przez platformę .NET Core.

### <a name="adonet"></a>ADO.NET

Nadal możesz używać ADO.NET z istniejącego kodu Desktop na platformie .NET Core. Wystarczy tylko zaktualizować niektóre pakiety NuGet.

### <a name="ef-core-vs-ef6"></a>EF Core a EF6

Istnieją dwie obecnie obsługiwane wersje programu Entity Framework (EF), Entity Framework 6 (EF6) i EF Core.

Najnowsza technologia wydana jako część świata .NET Framework jest Entity Framework, a 6,4 to Najnowsza wersja. Po uruchomieniu platformy .NET Core firma Microsoft wywołała również nowy stos dostępu do danych na podstawie Entity Framework i o nazwie Entity Framework Core.

Można użyć EF 6,4 i EF Core zarówno z .NET Framework, jak i .NET Core. Jakie są, jakie są sterowniki decyzyjne, aby ułatwić podjęcie decyzji między tymi elementami?

Dr 6,3 to pierwsza wersja EF6, która może być uruchamiana na platformie .NET Core i pracy na wielu platformach. W rzeczywistości głównym celem tej wersji jest ułatwienie migracji istniejących aplikacji, które korzystają z EF6 do platformy .NET Core.

EF Core zaprojektowano w celu udostępnienia środowiska deweloperskiego podobnego do EF6. Większość interfejsów API najwyższego poziomu pozostaje taka sama, więc EF Core będą znane deweloperom, którzy korzystali z EF6.

Chociaż są zgodne, istnieją różnice w implementacji, które należy sprawdzić przed podjęciem decyzji.
Aby uzyskać więcej informacji, zobacz [Compare EF Core & Ef6](/ef/efcore-and-ef6/).

Zaleca się użycie EF Core, jeśli:

* Aplikacja wymaga możliwości platformy .NET Core.
* EF Core obsługuje wszystkie funkcje wymagane przez aplikację.

Rozważ użycie EF6, jeśli są spełnione oba z następujących warunków:

* Aplikacja będzie działać w systemie Windows i .NET Framework 4,0 lub nowszej.
* EF6 obsługuje wszystkie funkcje wymagane przez aplikację.

### <a name="relational-databases"></a>Relacyjne bazy danych

#### <a name="sql-server"></a>SQL Server

SQL Server była jedną z baz danych, które można wybrać w przypadku tworzenia aplikacji dla komputerów stacjonarnych kilka lat temu. Korzystając z programu <xref:System.Data.SqlClient> w .NET Framework, można uzyskać dostęp do wersji SQL Server, które hermetyzują protokoły specyficzne dla bazy danych.

W programie .NET Core można znaleźć nową `SqlClient` klasę, w pełni zgodną z tą, która istnieje w .NET Framework, ale znajdującą się w <xref:Microsoft.Data.SqlClient> bibliotece. Wystarczy dodać odwołanie do pakietu NuGet [Microsoft. Data. SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) i wprowadzić zmiany nazw dla przestrzeni nazw, a wszystko powinno działać zgodnie z oczekiwaniami.

#### <a name="microsoft-access"></a>Microsoft Access

Program Microsoft Access został użyty przez lata w przypadku, gdy zaawansowane i bardziej skalowalne SQL Server nie były jeszcze wymagały. Nadal możesz połączyć się z programem Microsoft Access przy użyciu <xref:System.Data.Odbc> biblioteki.

## <a name="consuming-services"></a>Korzystanie z usług

W przypadku podniesienia architektury zorientowanej na usługę aplikacje klasyczne zaczęły rozwijać się z modelu klient-serwer do podejścia trójwymiarowego. W podejściu klient-serwer jest nawiązywane bezpośrednie połączenie z bazą danych z klienta utrzymującego logikę biznesową zwykle wewnątrz pojedynczego pliku EXE. Z drugiej strony podejście do warstwy pośredniej, która implementuje logikę biznesową i dostęp do bazy danych, pozwala na lepsze zabezpieczenia, skalowalność i ponowne wykorzystywanie. Zamiast bezpośrednio pracować z zestawami danych, podejście warstwy opiera się na zestawie usług implementujących kontrakty i typy obiektów jako sposób implementacji transferu danych.

Jeśli masz aplikację klasyczną przy użyciu usługi WCF i chcesz przeprowadzić migrację do platformy .NET Core, weź pod uwagę pewne zagadnienia.

Pierwszym krokiem jest rozwiązanie konfiguracji w celu uzyskania dostępu do usługi. Ponieważ konfiguracja różni się od platformy .NET Core, musisz wprowadzić pewne aktualizacje w pliku konfiguracji.

Po drugie należy ponownie wygenerować klienta usługi przy użyciu nowych narzędzi dostępnych w programie Visual Studio 2019. W tym kroku należy rozważyć aktywację generacji operacji synchronicznych, aby klient był zgodny z istniejącym kodem.

Po zakończeniu migracji, jeśli okaże się, że istnieją biblioteki, których nie ma w oprogramowaniu .NET Core, można dodać odwołanie do pakietu NuGet [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i sprawdzić, czy brakuje w nim funkcji.

Jeśli używasz <xref:System.Net.WebRequest> klasy do wykonywania wywołań usługi sieci Web, możesz znaleźć pewne różnice w oprogramowaniu .NET Core. Zaleca się użycie zamiast tego systemu .NET. http. HttpClient.

## <a name="consuming-a-com-object"></a>Zużywanie obiektu COM

Obecnie nie ma możliwości dodania odwołania do obiektu COM z programu Visual Studio 2019 do użycia z platformą .NET Core. Dlatego trzeba ręcznie zmodyfikować plik projektu.

Wstaw `COMReference` strukturę wewnątrz pliku projektu, jak w poniższym przykładzie:

```xml
<ItemGroup>
    <COMReference Include="MSHTML">
        <Guid>{3050F1C5-98B5-11CF-BB82-00AA00BDCE0B}\</Guid>
        <VersionMajor>4</VersionMajor>
        <VersionMinor>0</VersionMinor>
        <Lcid>0</Lcid>
        <WrapperTool>primary</WrapperTool>
        <Isolated>false</Isolated>
    </COMReference>
</ItemGroup>
```

## <a name="more-things-to-consider"></a>Więcej rzeczy do rozważenia

Niektóre technologie dostępne dla bibliotek .NET Framework nie są dostępne dla platformy .NET Core. Jeśli Twój kod opiera się na niektórych z tych technologii, weź pod uwagę alternatywne podejścia opisane w tej sekcji.

[Pakiet zgodności systemu Windows](../../core/porting/windows-compat-pack.md) zapewnia dostęp do interfejsów API, które były wcześniej dostępne tylko dla .NET Framework. Może być używany w projektach .NET Core i .NET Standard.

Więcej informacji na temat zgodności interfejsu API można znaleźć w dokumentacji dotyczącej istotnych zmian i przestarzałych/starszych interfejsów API w systemie <https://docs.microsoft.com/dotnet/core/compatibility/fx-core> .

### <a name="appdomains"></a>Domen aplikacji

Domeny aplikacji (AppDomains) izolują aplikacje od siebie. Domeny aplikacji wymagają obsługi środowiska uruchomieniowego i są kosztowne. Tworzenie dodatkowych domen aplikacji nie jest obsługiwane. W przypadku izolacji kodu zaleca się oddzielne procesy lub używanie kontenerów jako alternatywy. W przypadku dynamicznego ładowania zestawów zalecamy nową  <xref:System.Runtime.Loader.AssemblyLoadContext> klasę.

Aby ułatwić migrację kodu z .NET Framework, środowisko .NET Core uwidacznia część powierzchni interfejsu API domeny aplikacji. Niektóre z interfejsów API działają normalnie (na przykład  <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> ), niektórzy członkowie nie wykonują żadnych operacji (na przykład  <xref:System.AppDomain.SetCachePath%2A> ), a niektóre z nich zgłaszają <xref:System.PlatformNotSupportedException> (na przykład  <xref:System.AppDomain.CreateDomain%2A> ).

### <a name="remoting"></a>Komunikacji zdalnej

Komunikacja zdalna platformy .NET została użyta na potrzeby komunikacji między domenami, która nie jest już obsługiwana. Ponadto komunikacja zdalna wymaga obsługi środowiska uruchomieniowego, co jest kosztowne do utrzymania. Z tego względu komunikacja zdalna .NET nie jest obsługiwana w programie .NET Core.

W przypadku komunikacji między procesami należy wziąć pod uwagę mechanizmy komunikacji między procesami (IPC) jako alternatywę dla usług zdalnych, takich jak <xref:System.IO.Pipes?displayProperty=nameWithType> lub <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> klasy.

Na wielu maszynach Użyj rozwiązania sieciowego jako alternatywy. Najlepiej używać protokołu zwykłego tekstu o niskim obciążeniu, takiego jak HTTP. Serwer sieci Web Kestrel, serwer sieci Web używany przez ASP.NET Core, jest opcją w tym miejscu.

### <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)

W przypadku korzystania z trybu piaskownicy, który polega na środowisku uruchomieniowym lub środowisku, aby ograniczyć zasoby, których zarządzana aplikacja lub biblioteka jest uruchomiona, nie jest obsługiwane w programie .NET Core.

Aby uruchamiać procesy z minimalnym zestawem uprawnień, należy używać granic zabezpieczeń zapewnianych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników.

### <a name="security-transparency"></a>Przejrzystość zabezpieczeń

Podobnie jak w przypadku urzędów certyfikacji, przezroczystość zabezpieczeń oddziela kod w trybie piaskownicy od krytycznego kodu zabezpieczeń w sposób deklaratywny, ale nie jest już obsługiwany jako granica zabezpieczeń.

Aby uruchamiać procesy z najmniej zestawem uprawnień, należy używać granic zabezpieczeń zapewnianych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników.

>[!div class="step-by-step"]
>[Poprzedni](whats-new-dotnet-core.md ) 
> [Dalej](windows-migration.md)
