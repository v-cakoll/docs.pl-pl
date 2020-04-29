---
title: Migrowanie aplikacji WPF do programu .NET Core 3,0
description: Dowiedz się, jak przeprowadzić migrację aplikacji Windows Presentation Foundation (WPF) do programu .NET Core 3,0.
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: ccd2fc5a49d9c2d31c693e48099732614b568c7b
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507458"
---
# <a name="migrating-wpf-apps-to-net-core"></a>Migrowanie aplikacji WPF do platformy .NET Core

W tym artykule opisano kroki niezbędne do przeprowadzenia migracji aplikacji Windows Presentation Foundation (WPF) z .NET Framework do programu .NET Core 3,0. Jeśli nie masz dostępnej aplikacji WPF do portu, ale chcesz wypróbować ten proces, możesz użyć przykładowej aplikacji dla **handlowców** w witrynie [GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader). Oryginalna aplikacja (docelowa .NET Framework 4.7.2) jest dostępna w folderze NetFx\BeanTraderClient. Najpierw wyjaśnimy kroki niezbędne do przetestowania aplikacji w ogólny sposób, a następnie przeprowadzimy Cię przez szczegółowe zmiany, które dotyczą przykładu **handlowca** .

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Aby przeprowadzić migrację do platformy .NET Core, należy najpierw:

01. Zrozumienie i aktualizowanie zależności NuGet:

    01. Uaktualnij zależności NuGet, aby `<PackageReference>` użyć tego formatu.
    01. Przejrzyj zależności NuGet najwyższego poziomu dla platformy .NET Core lub .NET Standard zgodności.
    01. Uaktualnij pakiety NuGet do nowszych wersji.
    01. Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) , aby zrozumieć zależności platformy .NET.

01. Migruj plik projektu do nowego formatu w stylu zestawu SDK:

    01. Zdecyduj, czy ma być przeznaczony zarówno dla platformy .NET Core, jak i .NET Framework, czy tylko na platformie .NET Core.
    01. Skopiuj odpowiednie właściwości pliku projektu i elementów do nowego pliku projektu.

01. Rozwiąż problemy z kompilacją:

    01. Dodaj odwołanie do pakietu [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/) .
    01. Znajdź i napraw różnice poziomu interfejsu API.
    01. Usuń sekcje *App. config* inne niż `appSettings` lub `connectionStrings`.
    01. W razie potrzeby ponownie Generuj wygenerowany kod.

01. Testowanie środowiska uruchomieniowego:

    01. Potwierdź, że port działa zgodnie z oczekiwaniami.
    01. Uważaj na <xref:System.NotSupportedException> wyjątki.

## <a name="about-the-sample"></a>Informacje o przykładzie

Ten artykuł odwołuje się do [przykładowej aplikacji handlowca w języku fasoli](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) , ponieważ używa wielu zależności podobnych do tych, które mogą mieć rzeczywiste aplikacje WPF. Aplikacja nie jest duża, ale ma stanowić krok w górę od "Hello world" pod względem złożoności. W aplikacji przedstawiono niektóre problemy, które użytkownicy mogą napotkać podczas przenoszenia prawdziwych aplikacji. Aplikacja komunikuje się z usługą WCF, dlatego aby działała prawidłowo, należy również uruchomić projekt BeanTraderServer (dostępny w tym samym repozytorium GitHub) i upewnić się, że konfiguracja BeanTraderClient wskazuje właściwy punkt końcowy. (Domyślnie przykład zakłada, że serwer jest uruchomiony na tym samym komputerze, co *http://localhost:8090*ma wartość true, jeśli uruchomisz lokalnie BeanTraderServer).

Należy pamiętać, że ta Przykładowa aplikacja ma na celu przedstawienie wyzwań i rozwiązań związanych z portem .NET Core. Nie ma potrzeby przedstawienia najlepszych rozwiązań WPF. W rzeczywistości z tego względu zawiera pewne antywzorce, aby upewnić się, że będziesz mieć co najmniej kilka interesujących wyzwań podczas przenoszenia.

## <a name="getting-ready"></a>Przygotowanie

Podstawowym wyzwaniem migrowania aplikacji .NET Framework do programu .NET Core jest to, że jego zależności mogą współpracować inaczej lub wcale. Migracja jest znacznie łatwiejsza niż jej użycie; wiele pakietów NuGet teraz docelowo .NET Standard. Począwszy od platformy .NET Core 2,0, obszary powierzchni .NET Framework i .NET Core stają się podobne. Nawet dlatego niektóre różnice (zarówno w przypadku obsługi pakietów NuGet, jak i dostępnych interfejsów API platformy .NET) pozostają. Pierwszym krokiem w migrowaniu jest sprawdzenie zależności aplikacji i upewnienie się, że odwołania znajdują się w formacie, który można łatwo zmigrować do programu .NET Core.

### <a name="upgrade-to-packagereference-nuget-references"></a>Uaktualnij `<PackageReference>` do odwołań NuGet

Starsze projekty .NET Framework zwykle wykazują zależności NuGet w pliku *Packages. config* . Nowy format pliku projektu w stylu zestawu SDK odwołuje się do [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) pakietów NuGet jako elementy w samym pliku csproj, a nie w osobnym pliku konfiguracyjnym.

Podczas migracji istnieją dwie zalety korzystania `<PackageReference>`z odwołań do stylów:

- Jest to styl odwołania NuGet, który jest wymagany dla nowego pliku projektu .NET Core. Jeśli już używasz `<PackageReference>`, te elementy pliku projektu można skopiować i wkleić bezpośrednio do nowego projektu.
- W przeciwieństwie do pliku Packages. `<PackageReference>` config elementy odnoszą się tylko do zależności najwyższego poziomu, od których projekt zależy bezpośrednio. Wszystkie inne przechodnie pakiety NuGet zostaną określone w czasie przywracania i zapisane w pliku obj\project.assets.JSON. Dzięki temu można znacznie łatwiej określić, jakie zależności ma projekt, co jest przydatne podczas określania, czy wymagane zależności będą działały na platformie .NET Core, czy nie.

Pierwszym krokiem migrowania aplikacji .NET Framework do programu .NET Core jest zaktualizowanie jej do korzystania `<PackageReference>` z odwołań NuGet. Program Visual Studio ułatwia to proste. Po prostu kliknij prawym przyciskiem myszy plik *Packages. config* projektu w **Eksplorator rozwiązań**programu Visual Studio, a następnie wybierz polecenie **Migruj pakiety. config do PackageReference**.

![Uaktualnianie do PackageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

Zostanie wyświetlone okno dialogowe z obliczonymi zależnościami programu NuGet najwyższego poziomu i pytaniem, które inne pakiety NuGet mają być podwyższenie poziomu. Żaden z tych pozostałych pakietów nie musi być najwyższego poziomu dla przykładu handlowca fasoli, więc można usunąć zaznaczenie wszystkich pól. Następnie kliknij przycisk **OK** , a plik *Packages. config* zostanie usunięty `<PackageReference>` , a elementy zostaną dodane do pliku projektu.

`<PackageReference>`-Style References nie przechowują pakietów NuGet lokalnie w folderze Packages. Zamiast tego są one przechowywane globalnie jako Optymalizacja. Po zakończeniu migracji Edytuj plik CSPROJ i Usuń wszystkie `<Analyzer>` elementy odwołujące się do analizatorów, które wcześniej pochodziły z *.. Katalog \packages* . Nie martw się; ponieważ nadal masz odwołania do pakietu NuGet, analizatory zostaną dołączone do projektu. Wystarczy wyczyścić stare elementy style `<Analyzer>` Packages. config.

### <a name="review-nuget-packages"></a>Przejrzyj pakiety NuGet

Teraz, gdy widzisz pakiety NuGet najwyższego poziomu, od których zależy projekt, możesz sprawdzić, czy te pakiety są dostępne w środowisku .NET Core. Można określić, czy pakiet obsługuje platformę .NET Core, sprawdzając jego zależności od [NuGet.org](https://www.nuget.org/). Witryna [fuget.org](https://www.fuget.org/) utworzona przez społeczność ukazuje te informacje w widocznym miejscu w górnej części strony informacji o pakiecie.

W przypadku określania platformy .NET Core 3,0 wszystkie pakiety przeznaczone dla platformy .NET Core lub .NET Standard powinny funkcjonować (ponieważ platforma .NET Core implementuje obszar powierzchni .NET Standard). W niektórych przypadkach określona wersja pakietu, która jest używana, nie będzie ukierunkowana na platformę .NET Core lub .NET Standard, ale będzie dostępna nowsza wersja. W takim przypadku należy rozważyć uaktualnienie do najnowszej wersji pakietu.

Można używać pakietów przeznaczonych do .NET Framework, a także, które wprowadzają pewne ryzyko. Elementy .NET Core do .NET Framework zależności są dozwolone, ponieważ obszary powierzchni .NET Core i .NET Framework Surface są podobne, że takie zależności *często* działają. Jeśli jednak pakiet próbuje użyć interfejsu API platformy .NET, który nie jest obecny w środowisku .NET Core, wystąpi wyjątek w czasie wykonywania. Z tego względu należy odwoływać się tylko do .NET Framework pakietów, gdy nie są dostępne żadne inne opcje i nie rozumieją, że nie nastąpi obciążenie testem.

Jeśli istnieją pakiety, które nie są przeznaczone do programu .NET Core lub .NET Standard, należy wziąć pod uwagę inne alternatywy:

- Czy istnieją inne podobne pakiety, których można użyć zamiast tego? Czasami autorzy NuGet publikują oddzielne ". Podstawowe wersje ich bibliotek przeznaczonych dla platformy .NET Core. Pakiety biblioteki przedsiębiorstwa to przykład publikacji społecznościowej. Rozwiązania alternatywne. W innych przypadkach dla .NET Standard są dostępne nowsze zestawy SDK dla określonej usługi (czasami z różnymi nazwami pakietów). Jeśli nie są dostępne żadne alternatywy, możesz korzystać z do.NET Frameworkch pakietów, biorąc pod uwagę, że należy przetestować je dokładnie po uruchomieniu na platformie .NET Core.

Przykład handlowy ziarna fasoli ma następujące zależności najwyższego poziomu NuGet:

- [**Castle. Windsor, wersja 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Ten pakiet jest przeznaczony dla .NET Standard 1,6, dlatego działa w środowisku .NET Core.

- [**Microsoft. CodeAnalysis. FxCopAnalyzers, wersja 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Jest to Meta-pakiet, dlatego nie jest od razu oczywisty, które platformy obsługują, ale [Dokumentacja](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) wskazuje, że jej Najnowsza wersja (2.9.2) będzie działała zarówno dla .NET Framework, jak i .NET Core.

- [**Nito. AsyncEx, wersja 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Ten pakiet nie jest przeznaczony dla platformy .NET Core, ale nowsza wersja 5,0. Jest to typowe w przypadku migrowania, ponieważ wiele pakietów NuGet .NET Standard obsługiwać ostatnio, ale starsze wersje projektu będą wskazywać tylko .NET Framework. Jeśli różnica wersji jest tylko niewielką różnicą wersji, często można łatwo przeprowadzić uaktualnienie do nowszej wersji. Ze względu na to, że jest to główna zmiana wersji, należy zachować ostrożność uaktualniania, ponieważ w pakiecie mogą wystąpić pewne zmiany. Istnieje ścieżka do przodu, ale jest dobry.

- [**MahApps. Metro, wersja 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Ten pakiet nie jest również przeznaczony dla programu .NET Core, ale ma nowszą wersję wstępną (2,0-Alpha). Ponownie musisz wyszukać istotne zmiany, ale nowy pakiet zachęca.

Pakiet NuGet przykładowego elementu danych firmy fasoli jest zależny od wszystkich elementów docelowych .NET Standard/. NET Core lub mających nowsze wersje, co oznacza, że w tym miejscu nie można znaleźć żadnych problemów z blokowaniem.

### <a name="upgrade-nuget-packages"></a>Uaktualnij pakiety NuGet

Jeśli to możliwe, warto uaktualnić wersje pakietów, które są przeznaczone tylko dla platformy .NET Core lub .NET Standard z nowszymi wersjami w tym momencie (z projektem, który ma nadal służyć .NET Framework), aby odszukać i rozwiązać wszystkie istotne zmiany na początku.

Jeśli wolisz nie wprowadzać żadnych istotnych zmian do istniejącej wersji .NET Framework aplikacji, może to potrwać do momentu, gdy nowy plik projektu jest przeznaczony dla platformy .NET Core. Jednak Uaktualnienie pakietów NuGet do wersji programu .NET Core zgodnych ze standardem czasu sprawia, że proces migracji będzie jeszcze łatwiejszy po utworzeniu nowego pliku projektu i zmniejszeniu liczby różnic między wersjami .NET Framework i .NET Core aplikacji.

Za pomocą przykładu handlowca można łatwo wykonać wszystkie niezbędne uaktualnienia (przy użyciu Menedżera pakietów NuGet programu Visual Studio) z jednym wyjątkiem: uaktualnienie z **MahApps. Metro 1.6.5** do **2,0** ujawnia istotne zmiany związane z interfejsami API zarządzania motywem i akcentem.

W idealnym przypadku aplikacja zostanie zaktualizowana tak, aby korzystała z nowszej wersji pakietu (ponieważ najprawdopodobniej będzie działać na platformie .NET Core). Jednak w niektórych przypadkach może to nie być możliwe. W takich przypadkach nie należy aktualizować **MahApps. Metro** , ponieważ niezbędne zmiany nie są proste i ten samouczek koncentruje się na migrowaniu do platformy .NET Core 3, a nie do **MahApps. Metro 2.** Jest to również zależność .NET Framework o niskim ryzyku, ponieważ aplikacja handlowca jest oparta tylko na niewielkiej części **MahApps. Metro**. W takim przypadku należy wymagać testowania, aby upewnić się, że wszystko działa po zakończeniu migracji. Jeśli był to rzeczywisty scenariusz, warto zaplikować problem, aby śledzić pracę, która zostanie przeniesiona do **MahApps. Metro** w wersji 2,0, ponieważ nie spowoduje to przeprowadzenia migracji.

Gdy pakiety NuGet zostaną zaktualizowane do najnowszych wersji, Grupa `<PackageReference>` elementów w pliku projektu przykładowej firmy ziarna fasoli powinna wyglądać następująco.

```xml
<ItemGroup>
  <PackageReference Include="Castle.Windsor">
    <Version>4.1.1</Version>
  </PackageReference>
  <PackageReference Include="MahApps.Metro">
    <Version>1.6.5</Version>
  </PackageReference>
  <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers">
    <Version>2.9.2</Version>
  </PackageReference>
  <PackageReference Include="Nito.AsyncEx">
    <Version>5.0.0</Version>
  </PackageReference>
</ItemGroup>
```

### <a name="net-framework-portability-analysis"></a>.NET Framework analiza przenośności

Gdy zrozumiesz stan zależności NuGet projektu, następnym krokiem, który należy wziąć pod uwagę, jest .NET Framework zależności interfejsu API. Narzędzie [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) jest przydatne w celu ustalenia, które z interfejsów API platformy .NET są używane przez projekt, są dostępne na innych platformach platformy .NET.

Narzędzie jest dostępne jako [wtyczka programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), [Narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)lub opakowane w [prosty graficzny interfejs użytkownika](https://github.com/Microsoft/dotnet-apiport-ui), co upraszcza jego opcje. Więcej informacji o używaniu analizatora przenośności platformy .NET (port interfejsu API) przy użyciu graficznego interfejsu użytkownika w [usłudze portów aplikacji klasycznych na platformie .NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) . Jeśli wolisz używać wiersza polecenia, konieczne są następujące czynności:

1. Pobierz [Analizator przenośności platformy .NET](https://github.com/Microsoft/dotnet-apiport/releases) , jeśli jeszcze go nie masz.
1. Upewnij się, że aplikacja .NET Framework, która ma zostać przeniesiena do portu, została pomyślnie skompilowana (dobrym pomysłem przed migracją).
1. Uruchom port interfejsu API z wierszem polecenia podobnym do tego.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    `-f` Argument określa ścieżkę zawierającą pliki binarne do analizy. `-r` Argument określa format pliku wyjściowego. `-t` Argument określa platformę .NET, w której ma być analizowane użycie interfejsu API. W takim przypadku potrzebny jest program .NET Core.

Po otwarciu raportu HTML w pierwszej sekcji zostanie wystawiona lista wszystkich przeanalizowanych plików binarnych i jaki procent interfejsów API platformy .NET są dostępne na platformie dostosowanej. Wartość procentowa nie jest istotna dla siebie. To, co jest bardziej przydatne, jest wyświetlenie określonych interfejsów API, które nie istnieją. W tym celu wybierz nazwę zestawu lub przewiń w dół do raportów dla poszczególnych zestawów.

Skup się na zestawach, do których należy kod źródłowy. Na przykład w raporcie fasola handlowa ApiPort istnieje wiele plików binarnych, ale większość z nich należy do pakietów NuGet. `Castle.Windsor`pokazuje, że zależy od niektórych interfejsów API System. Web, których brakuje w programie .NET Core. Nie jest to problem, ponieważ został wcześniej zweryfikowany, który `Castle.Windsor` obsługuje program .NET Core. Pakiety NuGet często korzystają z różnych plików binarnych, które mogą być używane z różnymi platformami .NET, więc czy .NET Framework `Castle.Windsor` wersja używa interfejsów API System. Web, czy nie ma znaczenia, o ile pakiet jest również przeznaczony dla .NET Standard lub .NET Core.

Za pomocą przykładu handlowca, jedyną binarną, którą należy wziąć pod uwagę, jest **BeanTraderClient** , a raport pokazuje, że brakuje tylko dwóch `System.ServiceModel.ClientBase<T>.Close` interfejsów `System.ServiceModel.ClientBase<T>.Open`API platformy .NET: i.

![BeanTraderClient przenośności](./media/convert-project-from-net-framework/portability-report.png)

Te problemy nie mogą być blokowane, ponieważ interfejsy API klienta WCF są (głównie) obsługiwane przez platformę .NET Core, dlatego dla tych centralnych interfejsów API muszą być dostępne alternatywy. W rzeczywistości szukasz `System.ServiceModel`obszaru powierzchni .NET Core (przy użyciu <https://apisof.net>), zobaczysz, że zamiast tego istnieją asynchroniczne alternatywy w programie .NET Core.

W oparciu o ten raport i poprzednią analizę zależności NuGet wygląda na to, że nie powinno być żadnych poważnych problemów z migracją przykładowego handlowca do programu .NET Core. Jesteś gotowy do następnego kroku, w którym faktycznie rozpocznie się migracja.

## <a name="migrating-the-project-file"></a>Migrowanie pliku projektu

Jeśli aplikacja nie korzysta z nowego [formatu pliku projektu w stylu zestawu SDK](../../core/tools/csproj.md), potrzebny będzie nowy plik projektu do docelowego środowiska .NET Core. Można zastąpić istniejący plik CSPROJ lub, jeśli wolisz zachować istniejący projekt bez zmian w bieżącym stanie, można dodać nowy plik CSPROJ przeznaczony dla platformy .NET Core. Możesz tworzyć wersje aplikacji dla .NET Framework i .NET Core z pojedynczym plikiem projektu w stylu zestawu SDK z [wieloma](../../standard/library-guidance/cross-platform-targeting.md) obiektami docelowymi (określając wiele `<TargetFrameworks>` obiektów docelowych).

Aby utworzyć nowy plik projektu, można utworzyć nowy projekt WPF w programie Visual Studio lub użyć `dotnet new wpf` polecenia w katalogu tymczasowym do wygenerowania pliku projektu, a następnie skopiować go lub zmienić jego nazwę na poprawną lokalizację. Istnieje również narzędzie stworzone przez społeczność, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017), które umożliwia automatyzację niektórych migracji plików projektu. Narzędzie jest przydatne, ale nadal wymaga od ludzi sprawdzenia wyników, aby upewnić się, że wszystkie szczegóły migracji są poprawne. Jednym z obszarów, które narzędzie nie obsługuje optymalnie, jest Migrowanie pakietów NuGet z plików *Packages. config* . Jeśli narzędzie działa w pliku projektu, który nadal używa pliku *Packages. config* do odwoływania się do pakietów NuGet, zostanie automatycznie `<PackageReference>` zmigrowane do elementów, ale doda `<PackageReference>` elementy dla *wszystkich* pakietów, a nie tylko najwyższego poziomu. Jeśli przeprowadzono już migrację`<PackageReference>` do elementów z programem Visual Studio (jak zostało to zrobione w tym przykładzie), narzędzie może pomóc w pozostałej części konwersji. Podobnie jak Scott Hanselman zaleca w [swoim wpisie w blogu dotyczącym migrowania plików csproj](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx), przenoszenie odbywa się w sposób edukacyjny i zapewni lepsze wyniki, jeśli masz tylko kilka projektów do portów. Ale jeśli przenosisz dziesiątki lub setki plików projektu, to narzędzie takie jak [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) może być pomoc.

Aby utworzyć nowy plik projektu dla przykładowego handlowca, `dotnet new wpf` Uruchom w katalogu tymczasowym i Przenieś wygenerowany plik *csproj* do folderu *BeanTraderClient* i zmień jego nazwę na **BeanTraderClient. Core. csproj**.

Ponieważ nowy format pliku projektu automatycznie zawiera pliki języka C#, pliki *resx* i pliki XAML, które znajdują się w lub w katalogu, plik projektu jest już prawie ukończony. Aby zakończyć migrację, Otwórz stare i nowe pliki projektu obok siebie i zapoznaj się ze starym, aby sprawdzić, czy zawarte w nim informacje wymagają migracji. W przypadku przykładowego podmiotu gospodarczego fasoli następujące elementy powinny zostać skopiowane do nowego projektu:

- Wszystkie `<RootNamespace>`właściwości `<AssemblyName>`, i `<ApplicationIcon>` powinny być kopiowane.

- Należy również dodać `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` właściwość do nowego pliku projektu, ponieważ przykład handlowca fasoli zawiera atrybuty na poziomie zestawu (takie jak `[AssemblyTitle]`) w pliku AssemblyInfo.cs. Domyślnie nowe projekty w stylu zestawu SDK automatycznie generują te atrybuty na podstawie właściwości w pliku csproj. Ponieważ nie chcesz tego zrobić w tym przypadku (automatycznie generowane atrybuty byłyby sprzeczne z tymi z AssemblyInfo.cs), wygenerowane automatycznie atrybuty można wyłączyć za pomocą `<GenerateAssemblyInfo>`.

- Mimo że pliki *resx* są automatycznie dołączane jako zasoby `<Resource>` osadzone, inne elementy, takie jak obrazy, nie są obsługiwane. Skopiuj `<Resource>` elementy do osadzania plików obrazów i ikon. Można uprościć odwołania PNG do pojedynczego wiersza przy użyciu nowego formatu pliku projektu do obsługi wzorców obsługi symboli wieloznacznych: `<Resource Include="**\*.png" />`.

- Podobnie `<None>` elementy są uwzględniane automatycznie, ale nie są domyślnie kopiowane do katalogu wyjściowego. `<None>` Ponieważ projekt handlowca zawiera element, który *jest* kopiowany do katalogu wyjściowego (przy użyciu `PreserveNewest` zachowań), należy zaktualizować automatycznie wypełniony `<None>` element dla tego pliku, na przykład.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Przykład handlowy fasoli zawiera plik XAML (default. akcent. XAML) jako `Content` (a nie jako `Page`), ponieważ motywy i akcenty zdefiniowane w tym pliku są ładowane z pliku XAML w środowisku uruchomieniowym, a nie osadzane w samej aplikacji. Nowy system projektu automatycznie uwzględnia ten plik jako `<Page>`plik XAML. Należy więc zarówno usunąć plik XAML jako stronę (`<Page Remove="**\Default.Accent.xaml" />`), jak i dodać go jako zawartość.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Na koniec Dodaj odwołania NuGet poprzez skopiowanie `<ItemGroup>` `<PackageReference>` elementu z wszystkimi elementami. Jeśli nie poprzednio uaktualnione pakiety NuGet do wersji zgodnych z platformą .NET Core, można to zrobić teraz, gdy odwołania do pakietu znajdują się w projekcie specyficznym dla platformy .NET Core.

W tym momencie powinno być możliwe dodanie nowego projektu do rozwiązania BeanTrader i otwarcie go w programie Visual Studio. Projekt powinien wyglądać poprawnie w **Eksplorator rozwiązań**i `dotnet restore BeanTraderClient.Core.csproj` powinien pomyślnie przywrócić pakiety (z dwoma oczekiwanymi ostrzeżeniami związanymi z wersją MahApps. Metro, do której korzystasz .NET Framework).

Chociaż istnieje możliwość równoczesnego zachowania obu plików projektu (i może być pożądane, jeśli chcesz zachować stary projekt dokładnie tak, jak był), komplikuje proces migracji (te dwa projekty będą próbować korzystać z tych samych folderów bin i obj) i zwykle nie jest to konieczne. Jeśli chcesz skompilować zarówno dla programu .NET Core, jak i .NET Framework obiektów docelowych, możesz `<TargetFramework>netcoreapp3.0</TargetFramework>` `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` zamiast tego zastąpić właściwość w nowym pliku projektu. W przypadku przykładowego ziarna fasoli Usuń stary plik projektu (BeanTraderClient. csproj), ponieważ nie jest już wymagany. Jeśli wolisz zachować oba pliki projektu, upewnij się, że są one kompilowane do różnych wyjściowych i pośrednich ścieżek wyjściowych.

## <a name="fix-build-issues"></a>Rozwiązywanie problemów z kompilacją

Trzeci krok procesu przenoszenia pozwala uzyskać projekt do skompilowania. Niektóre aplikacje zostaną już pomyślnie skompilowane, gdy plik projektu zostanie przekonwertowany na projekt w stylu zestawu SDK. Jeśli tak, to w przypadku Twojej aplikacji gratulacje! Możesz przejść do kroku 4. Inne aplikacje będą potrzebować niektórych aktualizacji w celu ich skompilowania dla platformy .NET Core. Jeśli spróbujesz uruchomić `dotnet build` w przykładowym projekcie w języku ziarna fasoli teraz, na przykład (lub skompilować go w programie Visual Studio), wystąpi wiele błędów, ale nastąpi szybkie naprawienie.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>Odwołania do elementu System. ServiceModel i Microsoft. Windows. Compatibility

W przypadku wszystkich interfejsów API, które są dostępne dla platformy .NET Core, ale nie są automatycznie dołączane do pakietu aplikacji .NET Core. Aby rozwiązać ten konieczność, należy odwołać się `Microsoft.Windows.Compatibility` do pakietu. Pakiet zgodności zawiera szeroki zestaw interfejsów API, które są wspólne w aplikacjach klasycznych systemu Windows, takich jak klient WCF, usługi katalogowe, rejestr, konfiguracja, interfejsy API list ACL i inne.

Z próbką handlowca fasoli większość błędów kompilacji wynika z brakujących <xref:System.ServiceModel> typów. Można je rozwiązać, odwołując się do niezbędnych pakietów NuGet WCF. Interfejsy API klienta programu WCF znajdują się wśród `Microsoft.Windows.Compatibility` tych, które znajdują się w pakiecie, chociaż odwołujące się do pakietu zgodności jest jeszcze lepszym rozwiązaniem (ponieważ dotyczy to również wszystkich problemów związanych z interfejsami API, a także rozwiązań dotyczących problemów z usługą WCF, które udostępnia pakiet zgodności). Pakiet `Microsoft.Windows.Compatibility` jest pomocny w większości scenariuszy obejmujących platformy .net Core 3,0 i WinForms. Po dodaniu odwołania do programu `Microsoft.Windows.Compatibility`NuGet do programu pozostanie tylko jeden błąd kompilacji!

### <a name="cleaning-up-unused-files"></a>Czyszczenie nieużywanych plików

Jeden z typów problemów migracji, które są często odnoszą się do plików języka C# i XAML, które nie zostały wcześniej dołączone do kompilacji, które zostały pobrane przez nowe projekty w stylu zestawu SDK, które zawierają automatycznie *wszystkie* źródła.

Następny błąd kompilacji widoczny w przykładzie handlowca w języku fasoli odnosi się do nieprawidłowej implementacji interfejsu w *OldUnusedViewModel.cs*. Nazwa pliku jest wskazówką, ale po inspekcji znajdziesz ten plik źródłowy jest nieprawidłowy. Nie powodowały one wcześniej problemów, ponieważ nie zostały uwzględnione w oryginalnym projekcie .NET Framework. Pliki źródłowe, które znajdowały się na dysku, ale nie zostały uwzględnione w starym *csproj* , są teraz automatycznie dostępne.

W przypadku jednorazowych problemów, takich jak ten, można łatwo porównać z poprzednią *csproją* , aby potwierdzić, że plik nie jest wymagany, `<Compile Remove="" />` a następnie lub, jeśli plik źródłowy nie jest już wymagany, usuń go. W takim przypadku można bezpiecznie usunąć *OldUnusedViewModel.cs*.

Jeśli masz wiele plików źródłowych, które należy wykluczyć w ten sposób, możesz wyłączyć funkcję dołączania plików języka C#, ustawiając `<EnableDefaultCompileItems>` właściwość na false w pliku projektu. Następnie można skopiować `<Compile Include>` elementy ze starego pliku projektu do nowego, aby utworzyć tylko źródła przeznaczone do uwzględnienia. Podobnie, `<EnableDefaultPageItems>` można użyć, aby wyłączyć AUTOUZUPEŁNIANIE stron XAML i `<EnableDefaultItems>` kontrolować obydwa właściwości.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>W odniesieniu do kompilatora wieloprzebiegowego

Po usunięciu błędnego pliku z przykładu handlowca w postaci ziarna można ponownie skompilować i uzyskać cztery błędy. Nie masz tego wcześniej? Dlaczego została wystawiona liczba błędów? Kompilator języka C# jest [kompilatorem wielodostępnym](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes). Oznacza to, że poszczególne pliki źródłowe przechodzą dwa razy. Najpierw kompilator analizuje metadane i deklaracje w każdym pliku źródłowym i identyfikuje wszelkie problemy na poziomie deklaracji. Są to błędy, które zostały naprawione. Następnie ponownie przechodzi przez kod w celu skompilowania źródła C# do języka IL; są to drugi zestaw błędów, które są teraz wyświetlane.

> [!NOTE]
> Kompilator języka C# wykonuje [więcej niż dwa przebiegi](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes), ale wynikiem jest to, że błędy kompilatora dla dużych zmian kodu, takie jak ta, zachodzą na dwie fale.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Poprawki zależności innych firm (Castle. Windsor)

Inną klasą problemu, który występuje w niektórych scenariuszach migracji, jest różnice interfejsu API między wersjami zależności .NET Framework i .NET Core. Nawet jeśli pakiet NuGet jest przeznaczony dla .NET Framework i .NET Standard lub .NET Core, mogą istnieć różne biblioteki do użycia z różnymi obiektami docelowymi platformy .NET. Dzięki temu pakiety obsługują wiele różnych platform .NET, które mogą wymagać innych implementacji. Oznacza to również, że w bibliotekach może być małych różnic interfejsu API w przypadku różnych platform .NET.

Następny zestaw błędów, które zobaczysz w próbce handlowca fasoli, jest `Castle.Windsor` związany z interfejsami API. Projekt platformy .NET Core fasoli korzysta z tej samej wersji `Castle.Windsor` programu co projekt .NET Framework (4.1.1), ale implementacje tych dwóch platform są nieco inne.

W takim przypadku zobaczysz następujące problemy, które muszą zostać naprawione:

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`nie jest dostępny w programie .NET Core. Istnieje jednak podobny `Classes.FromAssemblyContaining` dostępny interfejs API, dlatego można zastąpić oba zastosowania `Classes.FromThisAssembly()` z wywołaniami do `Classes.FromAssemblyContaining(t)`, gdzie `t` jest typem wywołującym wywołanie.
1. Podobnie, w *Bootstrapper.cs*, `Castle.Windsor.Installer.FromAssembly`. Jest to niedostępne w programie .NET Core. Zamiast tego to wywołanie może zostać zastąpione `FromAssembly.Containing(typeof(Bootstrapper))`przez.

### <a name="updating-wcf-client-usage"></a>Aktualizowanie użycia klienta WCF

Po naprawieniu `Castle.Windsor` różnic, ostatni pozostały błąd kompilacji w projekcie handlowca programu .NET Core `BeanTraderServiceClient` to, że ( `DuplexClientBase`który pochodzi z) `Open` nie ma metody. Nie jest to zaskakujące, ponieważ jest to interfejs API, który został wyróżniony przez analizator przenośności platformy .NET na początku tego procesu migracji. Spojrzenie na `BeanTraderServiceClient` to, co jest bardziej związane z większą ilością problemu. Ten klient WCF został automatycznie wygenerowany przez narzędzie [Svcutil. exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .

**Klienci WCF wygenerowane przez Svcutil są przeznaczone do użycia w .NET Framework.**

Rozwiązania, które korzystają z klientów WCF generowanych przez Svcutil, muszą ponownie wygenerować klientów zgodnych z .NET Standardymi do użycia z platformą .NET Core. Jednym z głównych powodów, dla których stara klienci nie będzie działały, jest to, że zależą od konfiguracji aplikacji w celu zdefiniowania powiązań i punktów końcowych usługi WCF. Ponieważ .NET Standard interfejsów API WCF mogą współdziałać na wielu platformach (w których nie są dostępne interfejsy API System. Configuration), klienci programu WCF dla scenariuszy .NET Core i .NET Standard muszą definiować powiązania i punkty końcowe zamiast w konfiguracji.

W rzeczywistości każde użycie klienta programu WCF zależne od sekcji `<system.serviceModel>` App. config (niezależnie od tego, czy utworzone za pomocą Svcutil lub ręcznie) będzie musiało zostać zmienione w celu pracy z platformą .NET Core.

Istnieją dwa sposoby automatycznego generowania klientów WCF zgodnych z .NET Standard:

- `dotnet-svcutil` Narzędzie jest narzędziem platformy .NET, które GENERUJE klientów WCF w taki sposób, który jest podobny do tego, jak Svcutil działał wcześniej.
- Program Visual Studio może generować klientów WCF przy użyciu opcji [referencyjnej usługi sieci Web programu WCF](../../core/additional-tools/wcf-web-service-reference-guide.md) funkcji usługi połączone.

Jedno z tych rozwiązań działa prawidłowo. Alternatywnie możesz napisać kod klienta WCF samodzielnie. W tym przykładzie wybrano opcję korzystania z funkcji usługi połączonej programu Visual Studio. Aby to zrobić, kliknij prawym przyciskiem myszy projekt *BeanTraderClient. Core* w Eksploratorze rozwiązań programu Visual Studio i wybierz polecenie **Dodaj** > **podłączoną usługę**. Następnie wybierz dostawcę odwołań usługi sieci Web programu WCF. Spowoduje to wyświetlenie okna dialogowego, w którym można określić adres usługi sieci Web handlowca zaplecza (`localhost:8080` Jeśli serwer jest uruchomiony lokalnie), a przestrzeń nazw, która wygenerowała typy powinna być używana (**BeanTrader. Service**, na przykład).

![Okno dialogowe usługi połączonej z usługą sieci Web WCF](./media/convert-project-from-net-framework/connected-service-dialog.png)

Po wybraniu przycisku **Zakończ** do projektu zostanie dodany nowy węzeł usługi połączone, a w tym węźle zostanie dodany plik Reference.cs zawierający nowy klient WCF .NET Standard na potrzeby uzyskiwania dostępu do usługi handlowca. Jeśli przeszukasz metody `GetEndpointAddress` lub `GetBindingForEndpoint` w tym pliku, zobaczysz, że powiązania i punkty końcowe są teraz generowane programowo (a nie za pomocą konfiguracji aplikacji). Funkcja "Dodaj połączone usługi" może także dodawać odwołania do niektórych pakietów system. ServiceModel w pliku projektu, które nie są potrzebne, ponieważ wszystkie niezbędne pakiety WCF są dołączone do firmy Microsoft. Windows. Compatibility. Sprawdź csproj, aby sprawdzić, czy dodaliśmy dodatkowe elementy `<PackageReference>` system. ServiceModel, i jeśli tak, usuń je.

Nasz projekt ma teraz nowe klasy klienta WCF (w *Reference.cs*), ale również nadal ma stare (w BeanTrader.cs). W tym momencie dostępne są dwie opcje:

- Jeśli chcesz mieć możliwość kompilowania oryginalnego projektu .NET Framework (wraz z nowym celem platformy .NET Core), możesz użyć `<Compile Remove="BeanTrader.cs" />` elementu w pliku csproj projektu .NET Core, aby .NET Framework i .NET Core wersji aplikacji używały różnych klientów programu WCF. Jest to zaletą pozostawienia istniejącego projektu .NET Framework bez zmian. jednak ma wadą, że kod korzystający z wygenerowanych klientów WCF może być nieznacznie różny w przypadku platformy .NET Core niż w projekcie .NET Framework, więc prawdopodobnie trzeba będzie użyć `#if` dyrektyw w celu warunkowego skompilowania niektórych zastosowań klienta WCF (na przykład w przypadku tworzenia klientów) w taki sposób, aby działały w sposób oparty na platformie .NET Core i w inny sposób po skompilowaniu dla .NET Framework.

- Jeśli z drugiej strony, niektóre zmiany kodu w istniejącym .NET Framework projekcie są akceptowalne, można usunąć wszystkie razem *BeanTrader.cs* . Ponieważ nowy klient WCF został skompilowany dla .NET Standard, będzie działał zarówno w scenariuszach .NET Core, jak i .NET Framework. Jeśli tworzysz dla .NET Framework oprócz platformy .NET Core (przez wiele obiektów docelowych lub mających dwa pliki csproj), możesz użyć tego nowego pliku *Reference.cs* dla obu celów. Takie podejście ma zaletę, że kod nie musi bifurcate do obsługi dwóch różnych klientów WCF. ten sam kod będzie używany wszędzie. Wadą jest to, że wymaga zmiany (najprawdopodobniej stabilnej) .NET Framework projektu.

W przypadku przykładu handlowca w postaci ziarna można wprowadzać niewielkie zmiany w oryginalnym projekcie, jeśli ułatwia to migrację, więc wykonaj następujące kroki, aby uzgodnić użycie klienta WCF:

01. Dodaj nowy plik Reference.cs do projektu .NET Framework *BeanTraderClient. csproj* za pomocą menu kontekstowego "Dodaj istniejący element" z Eksploratora rozwiązań. Pamiętaj, aby dodać "jako link", aby ten sam plik był używany przez oba projekty (w przeciwieństwie do kopiowania pliku C#). W przypadku kompilowania programów .NET Core i .NET Framework przy użyciu jednego csproj (z użyciem wieloelementowego) ten krok nie jest konieczny.

01. Usuń *BeanTrader.cs*.

01. Nowy klient WCF jest podobny do starego, ale liczba przestrzeni nazw w wygenerowanym kodzie jest różna. W związku z tym konieczne jest zaktualizowanie projektu tak, aby typy klientów WCF były używane z BeanTrader. Service (lub dowolnej wybranej nazwy przestrzeni nazw) zamiast BeanTrader. model lub bez przestrzeni nazw. Kompilowanie *BeanTraderClient. Core. csproj* pomoże ustalić, gdzie te zmiany muszą zostać wykonane. Poprawki będą wymagały zarówno w języku C#, jak i w plikach źródłowych XAML.

01. Na koniec wykryjesz, że wystąpił błąd w *BeanTraderServiceClientFactory.cs* , ponieważ dostępne są konstruktory `BeanTraderServiceClient` dla tego typu. Jest to możliwe, aby podać `InstanceContext` argument (który został utworzony przy użyciu `CallbackHandler` z kontenera `Castle.Windsor` IOC). Nowe konstruktory tworzą nowe `CallbackHandler`s. Istnieją jednak konstruktory w typie podstawowym `BeanTraderServiceClient`, które pasują do tego, czego potrzebujesz. Ponieważ wygenerowany automatycznie kod klienta WCF istnieje w klasach częściowych, można go łatwo zwiększyć. W tym celu Utwórz nowy plik o nazwie *BeanTraderServiceClient.cs* , a następnie Utwórz klasę częściową o tej samej nazwie (przy użyciu przestrzeni nazw BeanTrader. Service). Następnie Dodaj jeden Konstruktor do typu częściowego, jak pokazano poniżej.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

Po wprowadzeniu tych zmian przykładowa wartość handlowa fasoli będzie używać nowego klienta WCF zgodnego z .NET Standard i można wprowadzić ostateczną poprawkę zmiany `Open` wywołania w *TradingService.cs* . `await OpenAsync`

Dzięki rozwiązanym problemom z programem WCF wersja platformy .NET Core klasy handlowca jest teraz kompiluje się prawidłowo!

## <a name="runtime-testing"></a>Testowanie środowiska uruchomieniowego

Można łatwo zapomnieć, że prace migracji nie są wykonywane, gdy tylko projekt zostanie oczyszczony w porównaniu z platformą .NET Core. Ważne jest, aby również pozostawić czas na przetestowanie aplikacji przez port. Po pomyślnym skompilowaniu aplikacji upewnij się, że aplikacja działa i działa zgodnie z oczekiwaniami, zwłaszcza jeśli używasz dowolnych pakietów przeznaczonych do .NET Framework.

Spróbujmy uruchomić aplikację sprzedawca z portem fasoli i zobaczyć, co się dzieje. Aplikacja nie jest daleko przed niepowodzeniem z powodu następującego wyjątku.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

Jest to uzasadnione. Należy pamiętać, że usługa WCF nie korzysta już z konfiguracji aplikacji, więc należy usunąć starą sekcję system. serviceModel pliku App. config. Zaktualizowany klient WCF zawiera wszystkie te same informacje w jego kodzie, więc sekcja config nie jest już wymagana. Jeśli chcesz, aby punkt końcowy WCF był konfigurowalny w pliku App. config, możesz go dodać jako ustawienie aplikacji i zaktualizować kod klienta WCF w celu pobrania punktu końcowego usługi WCF z konfiguracji.

Po usunięciu sekcji System. serviceModel *pliku App. config*aplikacja zostanie uruchomiona, ale nie powiedzie się z innym wyjątkiem po zalogowaniu się użytkownika.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

Nieobsługiwany interfejs API `Func<T>.BeginInvoke`to. Zgodnie z objaśnieniem [dotnet/corefx # 5940](https://github.com/dotnet/corefx/issues/5940), platforma .NET Core nie `BeginInvoke` obsługuje `EndInvoke` metod i typów delegatów z powodu podstawowych zależności zdalnych. Ten problem i jego rozwiązanie zostały omówione bardziej szczegółowo w sekcji [Migrowanie delegatów. BeginInvoke wywołań dla platformy .NET Core](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) , ale jest to, `BeginInvoke` że `EndInvoke` wywołania powinny być zastępowane `Task.Run` (lub asynchroniczne alternatywy, jeśli to możliwe). Jeśli w tym miejscu zostanie zastosowane ogólne `BeginInvoke` rozwiązanie, wywołanie może zostać zastąpione `Invoke` wywołaniem `Task.Run`uruchomionym przez.

```csharp
Task.Run(() =>
{
    return userInfoRetriever.Invoke();
}).ContinueWith(result =>
{
    // BeginInvoke's callback is replaced with ContinueWith
    var task = result.ConfigureAwait(false);
    CurrentTrader = task.GetAwaiter().GetResult();
}, TaskScheduler.Default);
```

Po usunięciu `BeginInvoke` użycia aplikacja handlowca języka fasoli zostanie pomyślnie uruchomiona na platformie .NET Core!

![Podmiot gospodarczy języka fasoli działającej na platformie .NET Core](./media/convert-project-from-net-framework/running-on-core.png)

Wszystkie aplikacje są inne, więc określone kroki wymagane do przeprowadzenia migracji własnych aplikacji do programu .NET Core będą się różnić. Ale miejmy nadzieję w przykładzie handlowca prezentuje ogólny przepływ pracy i typy problemów, które mogą być oczekiwane. Mimo że pomimo tego artykułu, rzeczywiste zmiany, które trzeba wykonać na próbce handlowca ziarna, aby działały na platformie .NET Core, były dość ograniczone. Wiele aplikacji jest migrowanych do programu .NET Core w ten sam sposób; bez konieczności wprowadzania zmian w kodzie.
