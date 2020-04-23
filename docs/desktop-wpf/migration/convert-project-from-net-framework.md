---
title: Migrowanie aplikacji WPF do platformy .NET Core 3.0
description: Dowiedz się, jak przeprowadzić migrację aplikacji Windows Presentation Foundation (WPF) do platformy .NET Core 3.0.
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: f52005e7c8a6312b8c4e09a950f1f635af1894e4
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "82071312"
---
# <a name="migrating-wpf-apps-to-net-core"></a>Migrowanie aplikacji WPF do platformy .NET Core

W tym artykule opisano kroki niezbędne do migracji aplikacji Windows Presentation Foundation (WPF) z programu .NET Framework do platformy .NET Core 3.0. Jeśli nie masz aplikacji WPF pod ręką do portu, ale chcesz wypróbować proces, możesz użyć przykładowej aplikacji **Bean Trader** dostępnej na [GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader). Oryginalna aplikacja (targetowanie .NET Framework 4.7.2) jest dostępna w folderze NetFx\BeanTraderClient. Najpierw wyjaśnimy kroki niezbędne do przenoszenia aplikacji w ogóle, a następnie przejdziemy przez konkretne zmiany, które mają zastosowanie do próbki **Bean Trader.**

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Aby przeprowadzić migrację do platformy .NET Core, należy najpierw:

01. Zrozumienie i aktualizowanie zależności NuGet:

    01. Uaktualnij zależności NuGet, `<PackageReference>` aby użyć formatu.
    01. Przejrzyj zależności nuget najwyższego poziomu dla zgodności .NET Core lub .NET Standard.
    01. Uaktualnij pakiety NuGet do nowszych wersji.
    01. Użyj [analizatora przenoszenia platformy .NET,](../../standard/analyzers/portability-analyzer.md) aby zrozumieć zależności .NET.

01. Migrowanie pliku projektu do nowego formatu w stylu SDK:

    01. Wybierz, czy mają być przeznaczone zarówno dla platformy .NET Core, jak i platformy .NET Framework, czy tylko do programu .NET Core.
    01. Skopiuj odpowiednie właściwości i elementy pliku projektu do nowego pliku projektu.

01. Rozwiązywanie problemów z kompilacją:

    01. Dodaj odwołanie do pakietu [Microsoft.Windows.Compatibility.](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/)
    01. Znajdź i napraw różnice na poziomie interfejsu API.
    01. Usuń sekcje *app.config* inne niż `appSettings` lub `connectionStrings`.
    01. W razie potrzeby ponownie wygeneruj wygenerowany kod.

01. Testowanie środowiska uruchomieniowego:

    01. Upewnij się, że przeniesiona aplikacja działa zgodnie z oczekiwaniami.
    01. Uważaj <xref:System.NotSupportedException> na wyjątki.

## <a name="about-the-sample"></a>Informacje o próbce

W tym artykule odwołuje [się do przykładowej aplikacji Bean Trader,](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) ponieważ używa różnych zależności podobnych do tych, które mogą mieć aplikacje WPF w świecie rzeczywistym. Aplikacja nie jest duża, ale ma być o krok od "Hello World" pod względem złożoności. Aplikacja pokazuje niektóre problemy, które użytkownicy mogą napotkać podczas przenoszenia prawdziwych aplikacji. Aplikacja komunikuje się z usługą WCF, więc aby działała poprawnie, należy również uruchomić projekt BeanTraderServer (dostępny w tym samym repozytorium GitHub) i upewnij się, że beantraderclient punktów konfiguracji do prawidłowego punktu końcowego. (Domyślnie przykład zakłada, że serwer jest uruchomiony *http://localhost:8090*na tym samym komputerze na poziomie , co będzie prawdą, jeśli uruchomisz BeanTraderServer lokalnie.)

Należy pamiętać, że ta przykładowa aplikacja ma na celu zademonstrowanie problemów i rozwiązań związanych z przenoszeniem .NET Core. Nie jest przeznaczony do wykazania WPF najlepszych praktyk. W rzeczywistości, celowo zawiera pewne anty-wzorców, aby upewnić się, że natkniesz się co najmniej kilka ciekawych wyzwań podczas przenoszenia.

## <a name="getting-ready"></a>Przygotowanie

Podstawowym wyzwaniem związanym z migracją aplikacji .NET Framework do platformy .NET Core jest to, że jej zależności mogą działać inaczej lub wcale. Migracja jest o wiele łatwiejsza niż kiedyś; wiele pakietów NuGet jest teraz kierowanych na standard .NET. Począwszy od .NET Core 2.0, obszary powierzchni .NET Framework i .NET Core stały się podobne. Mimo to niektóre różnice (zarówno w obsłudze pakietów NuGet i dostępnych interfejsów API .NET) pozostają. Pierwszym krokiem w migracji jest przejrzenie zależności aplikacji i upewnienie się, że odwołania są w formacie, który można łatwo migrować do platformy .NET Core.

### <a name="upgrade-to-packagereference-nuget-references"></a>Uaktualnij `<PackageReference>` do odniesień NuGet

Starsze projekty platformy .NET Framework zazwyczaj wyświetlają ich zależności NuGet w pliku *packages.config.* Nowy format pliku projektu w stylu SDK [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) odwołuje się do pakietów NuGet jako elementów w samym pliku csproj, a nie w oddzielnym pliku konfiguracyjnym.

Podczas migracji istnieją dwie zalety `<PackageReference>`korzystania z odwołań do stylu:

- Jest to styl odwołania NuGet, który jest wymagany dla nowego pliku projektu .NET Core. Jeśli już używasz `<PackageReference>`, te elementy pliku projektu mogą być kopiowane i wklejane bezpośrednio do nowego projektu.
- W przeciwieństwie do pliku `<PackageReference>` packages.config, elementy odnoszą się tylko do zależności najwyższego poziomu, od których zależy bezpośrednio projekt. Wszystkie inne przechodnie pakiety NuGet zostaną określone w czasie przywracania i zarejestrowane w automatycznie wygenerowanym pliku obj\project.assets.json. Dzięki temu znacznie łatwiej określić, jakie zależności ma projekt, co jest przydatne przy określaniu, czy niezbędne zależności będą działać na .NET Core, czy nie.

Pierwszym krokiem do migracji aplikacji .NET Framework do platformy .NET Core jest zaktualizowanie jej w celu użycia `<PackageReference>` odwołań NuGet. Visual Studio sprawia, że to proste. Wystarczy kliknąć prawym przyciskiem myszy plik *packages.config* projektu w **Eksploratorze rozwiązań**programu Visual Studio, a następnie wybrać **pozycję Migruj package.config do PackageReference**.

![Uaktualnianie do packageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

Pojawi się okno dialogowe przedstawiające obliczone zależności nuget najwyższego poziomu i pytanie, które inne pakiety NuGet powinny być promowane do najwyższego poziomu. Żaden z tych innych pakietów nie musi być na najwyższym poziomie dla próbki Bean Trader, więc możesz odznaczyć wszystkie te pola. Następnie kliknij przycisk **Ok,** a plik *packages.config* zostanie usunięty, a `<PackageReference>` elementy zostaną dodane do pliku projektu.

`<PackageReference>`-style odwołania nie przechowują pakietów NuGet lokalnie w folderze pakietów. Zamiast tego są one przechowywane globalnie jako optymalizacja. Po zakończeniu migracji edytuj plik csproj i `<Analyzer>` usuń wszystkie elementy odnoszące się do analizatorów, które wcześniej pochodziły z *pliku .. \packages.* Nie martw się; ponieważ nadal masz odwołania do pakietu NuGet, analizatory zostaną uwzględnione w projekcie. Wystarczy oczyścić stare elementy w stylu `<Analyzer>` packages.config.

### <a name="review-nuget-packages"></a>Przejrzyj pakiety NuGet

Teraz, gdy można zobaczyć najwyższego poziomu Pakiety NuGet, od których zależy projekt, można sprawdzić, czy te pakiety są dostępne w programie .NET Core. Można określić, czy pakiet obsługuje program .NET Core, patrząc na jego zależności od [nuget.org](https://www.nuget.org/). Witryna [fuget.org](https://www.fuget.org/) utworzonej przez społeczność pokazuje te informacje w widocznym miejscu u góry strony z informacjami o pakiecie.

Podczas kierowania .NET Core 3.0 wszystkie pakiety przeznaczone na .NET Core lub .NET Standard powinny działać (ponieważ .NET Core implementuje powierzchnię .NET Standard). W niektórych przypadkach określona wersja pakietu, który jest używany nie będzie przeznaczony dla .NET Core lub .NET Standard, ale nowsze wersje będą. W takim przypadku należy rozważyć uaktualnienie do najnowszej wersji pakietu.

Można również użyć pakietów kierowanych na platformę .NET Framework, ale to wprowadza pewne ryzyko. Zależności programu .NET Core to .NET Framework są dozwolone, ponieważ obszary powierzchni .NET Core i .NET Framework są na tyle podobne, że takie zależności *często* działają. Jeśli jednak pakiet spróbuje użyć interfejsu API platformy .NET, który nie jest obecny w systemie .NET Core, wystąpi wyjątek środowiska uruchomieniowego. Z tego powodu należy odwoływać się do pakietów .NET Framework tylko wtedy, gdy żadne inne opcje są dostępne i zrozumieć, że w ten sposób nakłada obciążenie testowe.

Jeśli istnieją pakiety, do których istnieją odwołania, które nie są przeznaczone dla platformy .NET Core lub .NET Standard, musisz pomyśleć o innych alternatywach:

- Czy istnieją inne podobne pakiety, które mogą być używane zamiast? Czasami NuGet autorzy publikują oddzielne . Core' wersje ich bibliotek specjalnie kierowania .NET Core. Pakiety biblioteki przedsiębiorstwa są przykładem publikowania społeczności ". NetCore" alternatywy. W innych przypadkach nowsze pakiety SDK dla określonej usługi (czasami z różnymi nazwami pakietów) są dostępne dla platformy .NET Standard. Jeśli nie są dostępne żadne alternatywy, można kontynuować przy użyciu pakietów .NET Framework ukierunkowane, mając na uwadze, że trzeba będzie przetestować je dokładnie po uruchomieniu na .NET Core.

Próbka Bean Trader ma następujące zależności NuGet najwyższego poziomu:

- [**Castle.Windsor, wersja 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Ten pakiet jest przeznaczony dla platformy .NET Standard 1.6, więc działa na programie .NET Core.

- [**Microsoft.CodeAnalysis.FxCopAnalyzers, wersja 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Jest to meta-pakiet, więc nie jest od razu oczywiste, które platformy obsługuje, ale [dokumentacja](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) wskazuje, że jego najnowsza wersja (2.9.2) będzie działać zarówno dla .NET Framework i .NET Core.

- [**Nito.AsyncEx, wersja 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Ten pakiet nie jest ukierunkowany na .NET Core, ale nowsza wersja 5.0 nie. Jest to typowe podczas migracji, ponieważ wiele pakietów NuGet dodano ostatnio obsługę .NET Standard, ale starsze wersje projektu będą kierowane tylko na platformę .NET Framework. Jeśli różnica wersji jest tylko różnica wersji pomocniczej, często jest to łatwe do uaktualnienia do nowszej wersji. Ponieważ jest to istotna zmiana wersji, należy zachować ostrożność uaktualniania, ponieważ może być istotne zmiany w pakiecie. Jest jednak droga naprzód, która jest dobra.

- [**MahApps.Metro, wersja 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Ten pakiet również nie jest ukierunkowany na .NET Core, ale ma nowszą wersję wstępną (2.0-alpha), która to robi. Ponownie, trzeba zwrócić uwagę na przełomowe zmiany, ale nowszy pakiet jest zachęcający.

Bean Trader próbki NuGet zależności wszystkich docelowych .NET Standard/.NET Core lub nowsze wersje, które to zrobić, więc jest mało prawdopodobne, aby być żadnych problemów blokowania tutaj.

### <a name="upgrade-nuget-packages"></a>Uaktualnianie pakietów NuGet

Jeśli to możliwe, dobrze byłoby uaktualnić wersje wszystkich pakietów, które są przeznaczone tylko dla platformy .NET Core lub .NET Standard z nowszymi wersjami w tym momencie (z projektem nadal przeznaczone dla platformy .NET Framework), aby wcześnie wykryć i rozwiązać wszelkie przełomowe zmiany.

Jeśli wolisz nie wprowadzać żadnych istotnych zmian w istniejącej wersji programu .NET Framework aplikacji, możesz poczekać, aż pojawi się nowy plik projektu docelowy .NET Core. Jednak uaktualnienie pakietów NuGet do wersji zgodnych z rdzeniem .NET z wyprzedzeniem sprawia, że proces migracji jest jeszcze łatwiejszy po utworzeniu nowego pliku projektu i zmniejsza liczbę różnic między wersjami programu .NET Framework i .NET Core aplikacji.

Za pomocą próbki Bean Trader wszystkie niezbędne uaktualnienia można łatwo (przy użyciu menedżera pakietów NuGet programu Visual Studio) z jednym wyjątkiem: uaktualnienie z **MahApps.Metro 1.6.5** do **2.0** ujawnia przełomowe zmiany związane z interfejsami API zarządzania motywem i akcentami.

W idealnym przypadku aplikacja zostanie zaktualizowana, aby użyć nowszej wersji pakietu (ponieważ jest to bardziej prawdopodobne, aby działać na .NET Core). W niektórych przypadkach może to jednak nie być wykonalne. W takich przypadkach nie uaktualniaj **MahApps.Metro,** ponieważ niezbędne zmiany są nietrywialne i ten samouczek koncentruje się na migracji do .NET Core 3, a nie do **MahApps.Metro 2.** Ponadto, jest to zależność .NET Framework niskiego ryzyka, ponieważ aplikacja Bean Trader wykonuje tylko niewielką część **MahApps.Metro**. Będzie to oczywiście wymagać testowania, aby upewnić się, że wszystko działa po zakończeniu migracji. Gdyby to był rzeczywisty scenariusz, dobrze byłoby zgłosić problem, aby śledzić pracę, aby przejść do **MahApps.Metro** w wersji 2.0, ponieważ nie robi migracji teraz pozostawia pewne zadłużenie techniczne.

Po nuget pakiety są aktualizowane `<PackageReference>` do najnowszych wersji, grupa towarów w pliku projektu bean trader powinien wyglądać następująco.

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

### <a name="net-framework-portability-analysis"></a>Analiza przenoszenia programu .NET Framework

Po zrozumieniu stanu zależności NuGet projektu, następną rzeczą do rozważenia jest .NET Framework zależności interfejsu API. Narzędzie [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) jest przydatne do zrozumienia, które interfejsy API platformy .NET są używane przez projekt na innych platformach .NET.

Narzędzie jest dostępne jako [wtyczka programu Visual Studio,](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) [narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)lub zawinięte w [prosty interfejs graficzny,](https://github.com/Microsoft/dotnet-apiport-ui)który upraszcza jego opcje. Więcej informacji na temat korzystania z analizatora przenoszenia platformy .NET (API Port) przy użyciu interfejsu użytkownika w [blogu portingu do programu .NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) jest dostępne w blogu. Jeśli wolisz używać wiersza polecenia, niezbędne kroki to:

1. Pobierz [analizator przenośności platformy .NET,](https://github.com/Microsoft/dotnet-apiport/releases) jeśli jeszcze go nie masz.
1. Upewnij się, że aplikacja .NET Framework do przenoszenia kompilacje pomyślnie (jest to dobry pomysł przed migracją niezależnie).
1. Uruchom port interfejsu API z wierszem polecenia w ten sposób.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    Argument `-f` określa ścieżkę zawierającą pliki binarne do analizy. Argument `-r` określa, który format pliku wyjściowego ma zostać sformatowy. Argument `-t` określa, która platforma .NET do analizy użycia interfejsu API. W takim przypadku chcesz .NET Core.

Po otwarciu raportu HTML pierwsza sekcja wyświetli listę wszystkich analizowanych plików binarnych i jaki procent interfejsów API platformy .NET, których używają, jest dostępny na platformie docelowej. Procent nie ma znaczenia sam w sobie. Co jest bardziej przydatne jest, aby zobaczyć określone interfejsy API, których brakuje. Aby to zrobić, wybierz nazwę zestawu lub przewiń w dół do raportów dla poszczególnych zestawów.

Skoncentruj się na zestawach, dla których jesteś właścicielem kodu źródłowego. Na przykład w raporcie ApiPort dla bean trader znajduje się wiele plików binarnych, ale większość z nich należy do pakietów NuGet. `Castle.Windsor`pokazuje, że zależy to od niektórych interfejsów API systemu.Web, których brakuje w programie .NET Core. Nie jest to problemem, ponieważ wcześniej `Castle.Windsor` zweryfikowano, że obsługuje .NET Core. Często pakiety NuGet mają różne pliki binarne do użytku z różnymi platformami `Castle.Windsor` .NET, więc niezależnie od tego, czy wersja programu .NET Framework używa interfejsów API systemu.Web, czy nie, nie ma znaczenia, o ile pakiet jest również przeznaczony dla platformy .NET Standard lub .NET Core (co robi).

W przykładzie Bean Trader jedynym plikiem binarnym, który należy wziąć pod uwagę, jest **BeanTraderClient,** a raport pokazuje, że brakuje tylko dwóch interfejsów API platformy .NET: `System.ServiceModel.ClientBase<T>.Close` i `System.ServiceModel.ClientBase<T>.Open`.

![Raport przenoszenia BeanTraderClient](./media/convert-project-from-net-framework/portability-report.png)

Jest mało prawdopodobne, aby blokować problemy, ponieważ interfejsy API klienta WCF są (głównie) obsługiwane w programie .NET Core, więc muszą istnieć alternatywy dostępne dla tych centralnych interfejsów API. W rzeczywistości, `System.ServiceModel`patrząc na 's .NET <https://apisof.net>Obszar powierzchni rdzenia (za pomocą ), widać, że istnieją alternatywy asynchronicznej w .NET Core zamiast.

Na podstawie tego raportu i poprzedniej analizy zależności NuGet wygląda na to, że nie powinno być żadnych większych problemów migracji próbki Bean Trader do .NET Core. Możesz przygotować się do następnego kroku, w którym faktycznie rozpoczniesz migrację.

## <a name="migrating-the-project-file"></a>Migrowanie pliku projektu

Jeśli aplikacja nie używa nowego [formatu pliku projektu w stylu SDK,](../../core/tools/csproj.md)potrzebny jest nowy plik projektu, aby kierować reklamy na program .NET Core. Możesz zastąpić istniejący plik csproj lub, jeśli wolisz zachować istniejący projekt nietknięty w jego bieżącym stanie, możesz dodać nowy plik csproj kierowania .NET Core. Można tworzyć wersje aplikacji dla platformy .NET Framework i .NET Core za pomocą jednego pliku projektu `<TargetFrameworks>` w stylu SDK z [wieloma lokalizacjami docelowymi](../../standard/library-guidance/cross-platform-targeting.md) (określając wiele obiektów docelowych).

Aby utworzyć nowy plik projektu, można utworzyć nowy projekt WPF `dotnet new wpf` w programie Visual Studio lub użyć polecenia w katalogu tymczasowym do wygenerowania pliku projektu, a następnie skopiować/zmienić jego nazwę do poprawnej lokalizacji. Istnieje również narzędzie stworzone przez społeczność, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017), które może zautomatyzować niektóre z migracji plików projektu. Narzędzie jest pomocne, ale nadal potrzebuje człowieka do przeglądania wyników, aby upewnić się, że wszystkie szczegóły migracji są poprawne. Jednym z określonych obszarów, które narzędzie nie obsługuje optymalnie jest migracja pakietów NuGet z plików *packages.config.* Jeśli narzędzie działa w pliku projektu, który nadal używa pliku *packages.config* do odwoływania się do pakietów NuGet, będzie automatycznie migrować do `<PackageReference>` elementów, ale doda `<PackageReference>` elementy dla *wszystkich* pakietów, a nie tylko te najwyższego poziomu. Jeśli zostały już zmigrowane do`<PackageReference>` elementów z programu Visual Studio (jak to zrobić w tym przykładzie), a następnie narzędzie może pomóc w pozostałej części konwersji. Podobnie jak Scott Hanselman zaleca w [swoim blogu na temat migracji plików csproj](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx), przenoszenie ręcznie jest edukacyjne i daje lepsze wyniki, jeśli masz tylko kilka projektów do portu. Ale jeśli przenosisz dziesiątki lub setki plików projektu, może pomóc narzędzie takie jak [CsprojToVs2017].

Aby utworzyć nowy plik projektu dla próbki `dotnet new wpf` Bean Trader, uruchom w katalogu tymczasowym i przenieś wygenerowany plik *csproj* do folderu *BeanTraderClient* i zmień jego nazwę **BeanTraderClient.Core.csproj**.

Ponieważ nowy format pliku projektu automatycznie zawiera pliki C#, *pliki resx* i pliki XAML, które znajduje się w katalogu lub w jego katalogu, plik projektu jest już prawie ukończony! Aby zakończyć migrację, otwórz stare i nowe pliki projektu obok siebie i przejrzyj stare, aby sprawdzić, czy jakiekolwiek informacje, które zawiera, muszą zostać zmigrowane. W przypadku przykładu Bean Trader następujące elementy powinny zostać skopiowane do nowego projektu:

- Właściwości `<RootNamespace>` `<AssemblyName>`i `<ApplicationIcon>` właściwości powinny być kopiowane.

- Należy również dodać `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` właściwość do nowego pliku projektu, ponieważ próbka Bean `[AssemblyTitle]`Trader zawiera atrybuty na poziomie zestawu (np. ) w pliku AssemblyInfo.cs. Domyślnie nowe projekty w stylu SDK będą automatycznie generować te atrybuty na podstawie właściwości w pliku csproj. Ponieważ nie chcesz, aby tak się stało w tym przypadku (atrybuty autogenerowane będą kolidować z `<GenerateAssemblyInfo>`tymi z AssemblyInfo.cs), należy wyłączyć atrybuty autogenerowane za pomocą programu .

- Chociaż pliki *resx* są automatycznie uwzględniane jako `<Resource>` zasoby osadzone, inne elementy, takie jak obrazy, nie są. Tak, skopiować `<Resource>` elementy do osadzania plików obrazów i ikon. Można uprościć odwołania png do pojedynczego wiersza przy użyciu obsługi nowego formatu pliku projektu dla wzorców globbing: `<Resource Include="**\*.png" />`.

- Podobnie `<None>` elementy są uwzględniane automatycznie, ale nie są domyślnie kopiowane do katalogu wyjściowego. Ponieważ projekt Bean Trader `<None>` zawiera element, który *jest* kopiowany `PreserveNewest` do katalogu wyjściowego (przy `<None>` użyciu zachowań), należy zaktualizować automatycznie wypełniony element dla tego pliku, na przykład.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Przykład Bean Trader zawiera plik XAML (Default.Accent.xaml) `Content` jako `Page`(a nie jako), ponieważ motywy i akcenty zdefiniowane w tym pliku są ładowane z pliku XAML w czasie wykonywania, a nie są osadzane w samej aplikacji. Nowy system projektu automatycznie zawiera ten `<Page>`plik jako , jednak, ponieważ jest to plik XAML. Tak, trzeba zarówno usunąć plik XAML jako`<Page Remove="**\Default.Accent.xaml" />`stronę ( ) i dodać go jako zawartość.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Na koniec dodaj odwołania NuGet, `<ItemGroup>` kopiując `<PackageReference>` z wszystkich elementów. Jeśli wcześniej nie uaktualniono pakietów NuGet do wersji zgodnych z rdzeniem platformy .NET, można to zrobić teraz, gdy odwołania do pakietu znajdują się w projekcie specyficznym dla rdzenia .NET.

W tym momencie powinno być możliwe, aby dodać nowy projekt do beantrader rozwiązania i otworzyć go w programie Visual Studio. Projekt powinien wyglądać poprawnie w `dotnet restore BeanTraderClient.Core.csproj` **Eksploratorze rozwiązań**i powinien pomyślnie przywrócić pakiety (z dwoma oczekiwanymi ostrzeżeniami związanymi z wersją MahApps.Metro, której używasz kierowania .NET Framework).

Chociaż możliwe jest, aby zachować oba pliki projektu obok siebie (a nawet może być pożądane, jeśli chcesz zachować budowanie starego projektu dokładnie tak, jak było), to komplikuje proces migracji (dwa projekty będą próbowały użyć tego samego bin i obj foldery) i zwykle nie jest konieczne. Jeśli chcesz utworzyć dla obiektów docelowych .NET Core i `<TargetFramework>netcoreapp3.0</TargetFramework>` .NET Framework, możesz `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` zastąpić właściwość w nowym pliku projektu zamiast tego. W przypadku próbki Bean Trader usuń stary plik projektu (BeanTraderClient.csproj), ponieważ nie jest już potrzebny. Jeśli wolisz zachować oba pliki projektu, należy je utworzyć do różnych ścieżek wyjściowych i pośrednich danych wyjściowych.

## <a name="fix-build-issues"></a>Rozwiązywanie problemów z kompilacją

Trzecim etapem procesu przenoszenia jest uzyskanie projektu do kompilacji. Niektóre aplikacje będą już tworzyć pomyślnie po przekonwertowaniu pliku projektu na projekt w stylu SDK. Jeśli tak jest w przypadku aplikacji, gratulacje! Możesz przejść do kroku 4. Inne aplikacje będą potrzebować pewnych aktualizacji, aby je zbudować dla platformy .NET Core. Jeśli spróbujesz `dotnet build` uruchomić w projekcie próbki Bean Trader teraz, na przykład (lub skompilować go w programie Visual Studio), będzie wiele błędów, ale otrzymasz je szybko naprawić.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>Odwołania do systemu.ServiceModel i microsoft.Windows.Compatibility

Typowym źródłem błędów brakuje odwołań do interfejsów API, które są dostępne dla platformy .NET Core, ale nie są automatycznie uwzględniane w metapakiecie aplikacji .NET Core. Aby rozwiązać ten problem, `Microsoft.Windows.Compatibility` należy odwołać się do pakietu. Pakiet zgodności zawiera szeroki zestaw interfejsów API, które są powszechne w aplikacjach klasycznych systemu Windows, takich jak klient WCF, usługi katalogowe, rejestr, konfiguracja, interfejsy API list ACL i inne.

W przypadku próbki Bean Trader większość błędów kompilacji <xref:System.ServiceModel> jest spowodowana brakującymi typami. Można rozwiązać te rozwiązania, odwołując się do niezbędnych pakietów WCF NuGet. Interfejsy API klienta WCF należą `Microsoft.Windows.Compatibility` do tych, które są obecne w pakiecie, więc odwoływanie się do pakietu zgodności jest jeszcze lepszym rozwiązaniem (ponieważ rozwiązuje również wszelkie problemy związane z interfejsami API, a także rozwiązania problemów WCF, które udostępnia pakiet zgodności). Pakiet `Microsoft.Windows.Compatibility` pomaga w większości scenariuszy przenoszenia .NET Core 3.0 WPF i WinForms. Po dodaniu odwołania `Microsoft.Windows.Compatibility`NuGet do , pozostaje tylko jeden błąd kompilacji!

### <a name="cleaning-up-unused-files"></a>Czyszczenie nieużywanych plików

Jeden typ problemu migracji, który pojawia się często odnosi się do plików C# i XAML, które nie zostały wcześniej uwzględnione w kompilacji coraz pobrane przez nowe projekty w stylu SDK, które zawierają *wszystkie* źródła automatycznie.

Następny błąd kompilacji, który widzisz w przykładzie Bean Trader odnosi się do złej implementacji interfejsu w *OldUnusedViewModel.cs*. Nazwa pliku jest wskazówką, ale podczas inspekcji okaże się, że ten plik źródłowy jest niepoprawny. Nie spowodowało to wcześniej problemów, ponieważ nie został uwzględniony w oryginalnym projekcie programu .NET Framework. Pliki źródłowe, które były obecne na dysku, ale nie zawarte w starym *csproj są* teraz automatycznie uwzględniane.

W przypadku jednorazowych problemów, takich jak ten, łatwo jest porównać z poprzednim *csprojem,* `<Compile Remove="" />` aby potwierdzić, że plik nie jest potrzebny, a następnie albo go, albo, jeśli plik źródłowy nie jest już potrzebny nigdzie, usuń go. W takim przypadku można bezpiecznie po prostu usunąć *OldUnusedViewModel.cs*.

Jeśli masz wiele plików źródłowych, które muszą być wykluczone w ten sposób, `<EnableDefaultCompileItems>` można wyłączyć automatyczne dołączanie plików Języka C#, ustawiając właściwość false w pliku projektu. Następnie można skopiować `<Compile Include>` elementy ze starego pliku projektu do nowego, aby utworzyć tylko źródła, które mają zostać uwzględnione. Podobnie `<EnableDefaultPageItems>` może służyć do wyłączania automatycznego dołączania stron `<EnableDefaultItems>` XAML i może kontrolować zarówno za pomocą jednej właściwości.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>Krótki bok na kompilatory multi-pass

Po usunięciu pliku naruszającego z próbki Bean Trader, można odtworzyć i otrzyma cztery błędy. Nie masz go wcześniej? Dlaczego liczba błędów wzrosła? Kompilator języka C# jest [kompilatorem wieloprzebiegowym](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes). Oznacza to, że przechodzi przez każdy plik źródłowy dwa razy. Najpierw kompilator po prostu patrzy na metadanych i deklaracji w każdym pliku źródłowym i identyfikuje wszelkie problemy na poziomie deklaracji. Są to błędy, które zostały naprawione. Następnie przechodzi przez kod ponownie do tworzenia źródła języka C# w IL; to drugi zestaw błędów, które teraz widzisz.

> [!NOTE]
> Kompilator Języka C# ma [więcej niż tylko dwa przebiegi](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes), ale wynik końcowy jest, że błędy kompilatora dla dużych zmian kodu, takich jak ten mają tendencję do dwóch fal.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Poprawki zależności innych firm (Castle.Windsor)

Inną klasą problemu, który pojawia się w niektórych scenariuszach migracji jest różnice interfejsu API między .NET Framework i .NET Core wersje zależności. Nawet jeśli pakiet NuGet jest przeznaczony zarówno dla platformy .NET Framework, jak i platformy .NET Standard lub .NET Core, mogą istnieć różne biblioteki do użycia z różnymi elementami docelowymi platformy .NET. Dzięki temu pakiety do obsługi wielu różnych platform .NET, które mogą wymagać różnych implementacji. Oznacza to również, że mogą występować małe różnice interfejsu API w bibliotekach podczas kierowania na różne platformy .NET.

Następny zestaw błędów, które zobaczysz w próbce Bean `Castle.Windsor` Trader są związane z interfejsami API. Projekt .NET Core Bean Trader używa `Castle.Windsor` tej samej wersji jako projektu docelowego .NET Framework (4.1.1), ale implementacje dla tych dwóch platform są nieco inne.

W takim przypadku zostaną wyświetlenia następujących problemów, które należy rozwiązać:

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`nie jest dostępna w programie .NET Core. Istnieje jednak podobny interfejs `Classes.FromAssemblyContaining` API dostępny, więc możemy zastąpić `Classes.FromThisAssembly()` oba `Classes.FromAssemblyContaining(t)`zastosowania `t` wywołaniem , gdzie jest typ nawiązywania połączenia.
1. Podobnie w *Bootstrapper.cs*. `Castle.Windsor.Installer.FromAssembly` Ta wartość jest niedostępna w programie .NET Core. Zamiast tego wywołanie można `FromAssembly.Containing(typeof(Bootstrapper))`zastąpić .

### <a name="updating-wcf-client-usage"></a>Aktualizowanie użycia klienta WCF

Po `Castle.Windsor` naprawieniu różnic ostatni błąd kompilacji pozostałych w projekcie .NET `BeanTraderServiceClient` Core Bean `DuplexClientBase`Trader jest to, że (który pochodzi z ) nie ma `Open` metody. Nie jest to zaskakujące, ponieważ jest to interfejs API, który został wyróżniony przez analizator przenośności .NET na początku tego procesu migracji. Patrząc `BeanTraderServiceClient` na zwraca naszą uwagę na większy problem, choć. Ten klient WCF został automatycznie wygenerowany przez narzędzie [Svcutil.exe.](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)

**Klienci WCF generowane przez Svcutil są przeznaczone do użytku w programie .NET Framework.**

Rozwiązania korzystające z generowanych przez svcutil klientów WCF będą musiały ponownie wygenerować klientów zgodnych ze standardem .NET do użytku z programem .NET Core. Jednym z głównych powodów, dla których starzy klienci nie będą działać, jest to, że zależą one od konfiguracji aplikacji do definiowania powiązań WCF i punktów końcowych. Ponieważ interfejsy API platformy .NET Standard WCF mogą działać na wielu platformach (gdzie interfejsy API system.configuration nie są dostępne), klienci WCF dla scenariuszy .NET Core i .NET Standard muszą definiować powiązania i punkty końcowe programowo, a nie w konfiguracji.

W rzeczywistości wszelkie użycie klienta WCF, które zależy od sekcji `<system.serviceModel>` app.config (czy utworzone za pomocą Svcutil lub ręcznie) będzie musiał zostać zmieniony, aby pracować na .NET Core.

Istnieją dwa sposoby automatycznego generowania klientów WCF zgodnych ze standardem platformy .NET:

- Narzędzie `dotnet-svcutil` jest narzędziem .NET, które generuje klientów WCF w sposób podobny do tego, jak Svcutil pracował wcześniej.
- Visual Studio może generować klientów WCF przy użyciu opcji [Odwołania do usługi sieci Web WCF](../../core/additional-tools/wcf-web-service-reference-guide.md) funkcji Połączone usługi.

Obu podejść działa dobrze. Alternatywnie, oczywiście, można napisać kod klienta WCF samodzielnie. W tym przykładzie wybrałem funkcję połączonej usługi Visual Studio. Aby to zrobić, kliknij prawym przyciskiem myszy projekt *BeanTraderClient.Core* w Eksploratorze rozwiązań programu Visual Studio i wybierz pozycję **Dodaj** > **połączoną usługę**. Następnie wybierz dostawcę referencyjnego usługi sieci Web WCF. Spowoduje to utworzenie okna dialogowego, w którym można określić adres`localhost:8080` usługi sieci web Backend Bean Trader (jeśli serwer jest uruchomiony lokalnie) i obszar nazw, który wygenerował typy powinny być używane (**BeanTrader.Service**, na przykład).

![Okno dialogowe Połączone usługi sieci Web WCF](./media/convert-project-from-net-framework/connected-service-dialog.png)

Po wybraniu przycisku **Zakończ** do projektu zostanie dodany nowy węzeł Usług połączonych, a w tym węźle zostanie dodany plik Reference.cs zawierający nowy klient .NET Standard WCF umożliwiający dostęp do usługi Bean Trader. Jeśli spojrzeć `GetEndpointAddress` na `GetBindingForEndpoint` lub metod w tym pliku, zobaczysz, że powiązania i punkty końcowe są teraz generowane programowo (zamiast za pośrednictwem konfiguracji aplikacji). Funkcja "Dodaj połączone usługi" może również dodać odwołania do niektórych pakietów System.ServiceModel w pliku projektu, które nie są potrzebne, ponieważ wszystkie niezbędne pakiety WCF są dołączone za pośrednictwem witryny Microsoft.Windows.Compatibility. Sprawdź w csproj, czy dodano dodatkowe `<PackageReference>` elementy System.ServiceModel, a jeśli tak, usuń je.

Nasz projekt ma teraz nowe klasy klientów WCF *(w Reference.cs),* ale nadal ma stare (w BeanTrader.cs). W tym momencie dostępne są dwie opcje:

- Jeśli chcesz mieć możliwość tworzenia oryginalnego projektu .NET Framework (obok nowego .NET Core-targeted jeden), można użyć `<Compile Remove="BeanTrader.cs" />` elementu w pliku csproj projektu .NET Core, tak aby .NET Framework i .NET Core wersje aplikacji używać różnych klientów WCF. Ma to tę zaletę, pozostawiając istniejący projekt .NET Framework bez zmian, ale ma wadę, że kod przy użyciu generowanych klientów WCF może być nieco `#if` inna w przypadku .NET Core niż w projekcie .NET Framework, więc prawdopodobnie trzeba będzie użyć dyrektyw warunkowo skompilować niektóre WCF użycia klienta (tworzenie klientów, na przykład) do pracy w jeden sposób po utworzeniu dla .NET Core i inny sposób, gdy zostanie zbudowany dla .NET Framework.

- Jeśli z drugiej strony niektóre zmiany kodu w istniejącym projekcie .NET Framework jest dopuszczalne, można usunąć *BeanTrader.cs* wszystkich razem. Ponieważ nowy klient WCF jest zbudowany dla platformy .NET Standard, będzie działać zarówno w scenariuszach .NET Core, jak i .NET Framework. Jeśli budujesz dla platformy .NET Framework oprócz platformy .NET Core (przez wiele kierowania lub przez dwa pliki csproj), możesz użyć tego nowego pliku *Reference.cs* dla obu obiektów docelowych. Takie podejście ma tę zaletę, że kod nie będzie musiał rozwidlenia do obsługi dwóch różnych klientów WCF; ten sam kod będzie używany wszędzie. Wadą jest to, że wiąże się ze zmianą (prawdopodobnie stabilny) .NET Framework projektu.

W przypadku próbki Bean Trader można wprowadzić małe zmiany w oryginalnym projekcie, jeśli ułatwia to migrację, więc wykonaj następujące kroki, aby uzgodnić użycie klienta WCF:

01. Dodaj nowy plik Reference.cs do projektu .NET Framework *BeanTraderClient.csproj* przy użyciu menu kontekstowego "Dodaj istniejący element" z eksploratora rozwiązań. Pamiętaj, aby dodać "jako łącze", aby ten sam plik był używany przez oba projekty (w przeciwieństwie do kopiowania pliku C#). Jeśli budujesz dla .NET Core i .NET Framework z jednego csproj (przy użyciu multi-targeting), a następnie ten krok nie jest konieczne.

01. Usuń *BeanTrader.cs*.

01. Nowy klient WCF jest podobny do starego, ale wiele obszarów nazw w wygenerowanym kodzie są różne. Z tego powodu konieczne jest zaktualizowanie projektu, tak aby typy klientów WCF były używane z BeanTrader.Service (lub niezależnie od nazwy obszaru nazw, które zostały wybrane) zamiast BeanTrader.Model lub bez obszaru nazw. Budowanie *BeanTraderClient.Core.csproj* pomoże określić, gdzie te zmiany muszą zostać wprowadzone. Poprawki będą potrzebne zarówno w języku C# i w plikach źródłowych XAML.

01. Na koniec odkryjesz, że wystąpił błąd w *BeanTraderServiceClientFactory.cs,* ponieważ zmieniły `BeanTraderServiceClient` się dostępne konstruktory dla tego typu. Kiedyś możliwe było dostarczenie argumentu `InstanceContext` (który `CallbackHandler` został `Castle.Windsor` utworzony przy użyciu kontenera IoC). Nowe konstruktory `CallbackHandler`tworzą nowe s. Istnieją jednak konstruktory `BeanTraderServiceClient`w 's typ podstawowy, które pasują do tego, co chcesz. Ponieważ automatyczniegenerowany kod klienta WCF istnieje w klasach częściowych, można łatwo rozszerzyć go. Aby to zrobić, należy utworzyć nowy plik o nazwie *BeanTraderServiceClient.cs* a następnie utworzyć klasę częściową o tej samej nazwie (przy użyciu obszaru nazw BeanTrader.Service). Następnie dodaj jeden konstruktor do typu częściowego, jak pokazano w tym miejscu.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

Po tych zmianach, Bean Trader próbki będzie teraz przy użyciu nowego klienta WCF .NET Standard `Open` i można dokonać ostatecznej poprawki zmiany wywołania w *TradingService.cs* zamiast tego. `await OpenAsync`

Z WCF problemy rozwiązane, .NET Core wersja próbki Bean Trader teraz buduje czysto!

## <a name="runtime-testing"></a>Testowanie środowiska uruchomieniowego

Łatwo zapomnieć, że praca migracji nie jest wykonywana, gdy tylko projekt zostanie zbudowany czysto przeciwko .NET Core. Ważne jest, aby pozostawić czas na przetestowanie złącza aplikacji. Gdy wszystko zostanie pomyślnie skompilować, upewnij się, że aplikacja działa zgodnie z oczekiwaniami, zwłaszcza jeśli używasz żadnych pakietów kierowania .NET Framework.

Spróbujmy uruchomić zanużaną aplikację Bean Trader i zobaczmy, co się stanie. Aplikacja nie jest daleko przed niepowodzeniem z następującym wyjątkiem.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

To oczywiście ma sens. Należy pamiętać, że WCF nie używa już konfiguracji aplikacji, więc stara sekcja system.serviceModel pliku app.config musi zostać usunięta. Zaktualizowany klient WCF zawiera wszystkie te same informacje w swoim kodzie, więc sekcja konfiguracji nie jest już potrzebna. Jeśli chcesz, aby punkt końcowy WCF można było skonfigurować w app.config, można dodać go jako ustawienie aplikacji i zaktualizować kod klienta WCF, aby pobrać punkt końcowy usługi WCF z konfiguracji.

Po usunięciu sekcji system.serviceModel *app.config*aplikacja uruchamia się, ale kończy się niepowodzeniem z innym wyjątkiem, gdy użytkownik się zaloguje.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

Nieobsługiwał się `Func<T>.BeginInvoke`interfejs API jest . Jak wyjaśniono w [dotnet/corefx#5940](https://github.com/dotnet/corefx/issues/5940), .NET `BeginInvoke` Core `EndInvoke` nie obsługuje i metody na typy delegatów ze względu na podstawowe zależności komunikacji zdalnej. Ten problem i jego poprawka są wyjaśnione bardziej szczegółowo w [migracji Delegate.BeginInvoke wywołuje .NET](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) `BeginInvoke` Core `EndInvoke` blogu, ale `Task.Run` istotą jest to, że i wywołania powinny być zastąpione (lub async alternatywy, jeśli to możliwe). Stosując ogólne rozwiązanie tutaj, `BeginInvoke` połączenie można zastąpić `Invoke` wywołaniem `Task.Run`rozpoczętym przez .

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

Po usunięciu `BeginInvoke` użycia aplikacja Bean Trader działa pomyślnie na programie .NET Core!

![Bean Trader działa na .NET Core](./media/convert-project-from-net-framework/running-on-core.png)

Wszystkie aplikacje są różne, więc określone kroki potrzebne do migracji własnych aplikacji do platformy .NET Core będą się różnić. Ale miejmy nadzieję, że próbki Bean Trader pokazuje ogólny przepływ pracy i rodzaje problemów, które można się spodziewać. I, pomimo długości tego artykułu, rzeczywiste zmiany potrzebne w próbce Bean Trader, aby działało na .NET Core, były dość ograniczone. Wiele aplikacji migruje do platformy .NET Core w ten sam sposób; z ograniczoną lub nawet nie wymaga żadnych zmian kodu.
