---
title: Przykład migracji do programu .NET Core 3.1
description: Przedstawiamy sposób migrowania przykładowych aplikacji przeznaczonych dla .NET Framework do programu .NET Core 3,1.
ms.date: 05/12/2020
ms.openlocfilehash: ef8a0c24ec81a21eb89411ed4c9a543d4d70d89f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423384"
---
# <a name="example-of-migrating-to-net-core-31"></a>Przykład migracji do programu .NET Core 3.1

W tym rozdziale przedstawimy praktyczne wskazówki ułatwiające przeprowadzenie migracji istniejącej aplikacji z .NET Framework na platformę .NET Core.

Oferujemy dobrze strukturalny proces, który można wykonać, i najważniejsze zagadnienia, które należy wziąć pod uwagę w każdym kroku.

Następnie należy udokumentować proces migracji krok po kroku dla przykładowej aplikacji klasycznej, zarówno z WinForms, jak i wersji WPF.

## <a name="migration-process-overview"></a>Przegląd procesu migracji

Proces migracji składa się z czterech kolejnych kroków:

1. **Przygotowanie**: zrozumienie zależności, dla których projekt musi mieć pomysł dotyczący tego, co dzieje się z wyprzedzeniem. W tym kroku przeniesiesz bieżący projekt do stanu, który upraszcza punkt startowy migracji.

2. **Migruj plik projektu:** projekty platformy .NET Core używają nowego formatu projektu w stylu zestawu SDK. Utwórz nowy plik projektu o tym formacie lub zaktualizuj go, aby użyć stylu zestawu SDK.

3. **Napraw kod i skompiluj:** Kompilowanie kodu w programie .NET Core — różnice na poziomie interfejsu API między .NET Framework i .NET Core. W razie potrzeby zaktualizuj pakiety innych firm do tych, które obsługują platformę .NET Core.

4. **Uruchom i Testuj:** Mogą występować różnice, które nie są wyświetlane do czasu uruchomienia. Dlatego nie zapomnij uruchomić aplikacji i przetestuj, że wszystko działa zgodnie z oczekiwaniami.

### <a name="preparation"></a>Przygotowanie

#### <a name="migrate-packagesconfig-file"></a>Migruj plik Packages. config

W aplikacji .NET Framework wszystkie odwołania do pakietów zewnętrznych są deklarowane w pliku *Packages. config* . W programie .NET Core nie ma już potrzeby używania pliku *Packages. config* . Zamiast tego należy użyć właściwości [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) wewnątrz pliku projektu, aby określić pakiety NuGet dla aplikacji.

Dlatego należy przejść z jednego formatu na inny. Aktualizację można wykonać ręcznie, biorąc pod uwagę zależności zawarte w pliku *Packages. config* i migruje je do pliku projektu `PackageReference` . Możesz również pozwolić programowi Visual Studio na wykonywanie zadań: kliknij prawym przyciskiem myszy plik *Packages. config* i wybierz opcję **Migruj pakiety. config do PackageReference** .

#### <a name="verify-every-dependency-compatibility-in-net-core"></a>Weryfikowanie każdej zgodności zależności w programie .NET Core

Po przeprowadzeniu migracji odwołań do pakietów należy sprawdzić wszystkie odwołania w celu zapewnienia zgodności. Możesz zapoznać się z zależnościami poszczególnych pakietów NuGet, których aplikacja używa w [NuGet.org](https://www.nuget.org/). Jeśli pakiet ma .NET Standard zależności, wówczas będzie działał w środowisku .NET Core, ponieważ program .NET Core 3,1 [obsługuje](../../standard/net-standard.md#net-implementation-support) wszystkie wersje .NET Standard. Na poniższej ilustracji przedstawiono zależności `Castle.Windsor` pakietu:

![Zrzut ekranu przedstawiający zależności NuGet dla pakietu Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

Aby sprawdzić zgodność pakietu, można użyć narzędzia <http://fuget.org> oferującego bardziej szczegółowe informacje o wersjach i zależnościach.

Być może projekt odwołuje się do starszych wersji pakietu, które nie obsługują platformy .NET Core, ale mogą znaleźć nowsze wersje, które je obsługują. Dlatego aktualizowanie pakietów do nowszych wersji jest generalnie dobrym zaleceniem. Należy jednak wziąć pod uwagę, że aktualizacja wersji pakietu może wprowadzić pewne istotne zmiany, które wymusić zaktualizowanie kodu.

Co się stanie, jeśli nie znajdziesz zgodnej wersji? Co zrobić, jeśli nie chcesz zaktualizować wersji pakietu ze względu na te zmiany? Nie martw się, ponieważ można zależeć od .NET Framework pakietów z aplikacji .NET Core. Nie zapomnij go przetestować w szerokim stopniu, ponieważ może to spowodować błędy w czasie wykonywania, jeśli pakiet zewnętrzny wywoła interfejs API, który nie jest dostępny w programie .NET Core. Jest to doskonałe rozwiązanie w przypadku korzystania ze starego pakietu, który nie zostanie zaktualizowany i można go przekierować do pracy z platformą .NET Core.

#### <a name="check-for-api-compatibility"></a>Sprawdź zgodność interfejsu API

Ze względu na to, że powierzchnia interfejsu API w .NET Framework i .NET Core jest podobna, ale nie identyczna, należy sprawdzić, które interfejsy API są dostępne w środowisku .NET Core, a które nie. Można użyć narzędzia analizatora przenośności platformy .NET do wykorzystania interfejsów API, które nie są dostępne w programie .NET Core. Sprawdza on poziom binarny swojej aplikacji, wyodrębnia wszystkie interfejsy API, które są wywoływane, a następnie wyświetla listę interfejsów API, które nie są dostępne w ramach platformy docelowej (w tym przypadku .NET Core 3,1).

Więcej informacji o tym narzędziu można znaleźć pod adresem:

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

Interesujący aspekt tego narzędzia polega na tym, że tylko prezentuje różnice wynikające z własnego kodu, a nie kodu z pakietów zewnętrznych, których nie można zmienić. Należy pamiętać, że należy zaktualizować większość z tych pakietów, aby działały one z platformą .NET Core.

### <a name="migrate-project-file"></a>Migruj plik projektu

#### <a name="create-the-new-net-core-project"></a>Utwórz nowy projekt platformy .NET Core

W większości przypadków należy zaktualizować istniejący projekt do nowego formatu .NET Core. Można jednak również utworzyć nowy projekt przy zachowaniu Starego. Główną wadą z aktualizacji starego projektu jest utrata wsparcia projektanta, co może być dla Ciebie ważne. Jeśli chcesz nadal korzystać z projektanta, musisz utworzyć nowy projekt .NET Core równolegle ze starym i współużytkowanymi zasobami. Jeśli musisz zmodyfikować elementy interfejsu użytkownika w projektancie, możesz przełączyć się do starego projektu, aby to zrobić. Ze względu na to, że zasoby są połączone, zostaną również zaktualizowane w projekcie .NET Core.

[Projekt w stylu zestawu SDK](../../core/project-sdk/msbuild-props.md) dla platformy .NET Core jest znacznie prostszy niż format projektu .NET Framework. Oprócz powyższych `PackageReference` wpisów nie trzeba robić więcej. Nowy format projektu [Domyślnie](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects)zawiera pewne rozszerzenia plików, takie jak `.cs` i `.xaml` pliki, bez konieczności jawnego umieszczania ich w pliku projektu.

#### <a name="assemblyinfo-considerations"></a>Zagadnienia dotyczące Assembly.info

Atrybuty są generowane automatycznie w projektach .NET Core. Jeśli projekt zawiera plik *AssemblyInfo.cs* , definicje zostaną zduplikowane, co spowoduje konflikty kompilacji. Możesz usunąć starszy plik *AssemblyInfo.cs* lub wyłączyć automatyczne generowanie, dodając następujący wpis do pliku projektu .NET Core:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a>Zasoby

Zasoby osadzone są uwzględniane automatycznie, ale zasoby nie są, więc należy przeprowadzić migrację zasobów do nowego pliku projektu.

#### <a name="package-references"></a>Odwołania do pakietu

Za pomocą opcji **Migruj pakiety. config do PackageReference** można łatwo przenieść odwołania do pakietów zewnętrznych do nowego formatu, jak wspomniano wcześniej.

#### <a name="update-package-references"></a>Aktualizuj odwołania do pakietów

Zaktualizuj wersje odnalezionych pakietów jako zgodne, jak pokazano w poprzedniej sekcji.

### <a name="fix-the-code-and-build"></a>Popraw kod i skompiluj

#### <a name="microsoftwindowscompatibility"></a>Microsoft. Windows. Compatibility

Jeśli aplikacja jest zależna od interfejsów API, które nie są dostępne w środowisku .NET Core, takich jak rejestr, listy ACL lub WCF, należy dołączyć odwołanie do `Microsoft.Windows.Compatibility` pakietu w celu dodania tych interfejsów API właściwych dla systemu Windows. Działają one na platformie .NET Core, ale nie są uwzględniane, ponieważ nie są na wielu platformach.

Istnieje narzędzie o nazwie API Analyzer ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ), które pomaga identyfikować interfejsy API, które nie są zgodne z kodem.

#### <a name="use-if-directives"></a>Użyj \# dyrektywy if

Jeśli potrzebujesz różnych ścieżek wykonywania podczas określania wartości docelowej .NET Framework i .NET Core, musisz użyć stałych kompilacji. Dodaj kilka \# dyrektyw if do kodu, aby zachować tę samą bazę kodu dla obu celów.

#### <a name="technologies-not-available-on-net-core"></a>Technologie niedostępne w programie .NET Core

Niektóre technologie nie są dostępne na platformie .NET Core, na przykład:

* Domen aplikacji
* Komunikacji zdalnej
* Zabezpieczenia dostępu kodu
* Serwer WCF
* Przepływ pracy systemu Windows

Dlatego należy znaleźć zamiennik dla tych technologii, jeśli są one używane w aplikacji. Aby uzyskać więcej informacji, zobacz [technologie .NET Framework niedostępne w artykule .NET Core](../../core/porting/net-framework-tech-unavailable.md) .

#### <a name="regenerate-autogenerated-clients"></a>Wygeneruj ponownie generowanych klientów

Jeśli aplikacja używa automatycznie generowanego kodu, takiego jak klient WCF, może być konieczne ponowne wygenerowanie tego kodu dla programu .NET Core. Czasami można znaleźć brakujące odwołania, ponieważ mogą one nie być dołączone jako część domyślnego zestawu zestawów .NET Core. Za pomocą narzędzia takiego jak <https://apisof.net/> , można łatwo zlokalizować zestaw, w którym brakuje brakujące odwołanie, i dodać go z NuGet.

#### <a name="rolling-back-package-versions"></a>Wycofywanie wersji pakietu

Zgodnie z ogólną zasadą zalecamy, aby lepiej zaktualizować każdą wersję pakietu, aby była zgodna z platformą .NET Core. Można jednak znaleźć, że dla zaktualizowanej i zgodnej wersji zestawu nie jest to płatność wyłączona. Jeśli koszt zmiany nie jest akceptowalny, można rozważyć wycofywanie wersji pakietu, zachowując te, które są używane w .NET Framework. Chociaż mogą nie być ukierunkowane na platformę .NET Core, powinny one działać prawidłowo, chyba że wywoła nieobsługiwane interfejsy API.

### <a name="run-and-test"></a>Uruchamianie i testowanie

Po skompilowaniu aplikacji bez błędów można uruchomić ostatni krok migracji, testując każdą funkcję.

W tym ostatnim kroku można znaleźć kilka różnych problemów w zależności od złożoności aplikacji oraz zależności i interfejsów API, których używasz.

Na przykład w przypadku korzystania z plików konfiguracji (*App. config*) mogą wystąpić błędy w czasie wykonywania, podobnie jak w przypadku nieobecnych sekcji konfiguracyjnych. Korzystanie z `Microsoft.Extensions.Configuration` pakietu NuGet powinno rozwiązać ten problem.

Kolejną przyczyną błędów jest użycie `BeginInvoke` metod i, `EndInvoke` ponieważ nie są one obsługiwane przez platformę .NET Core. Nie są one obsługiwane przez platformę .NET Core, ponieważ mają one zależność od komunikacji zdalnej, która nie istnieje w programie .NET Core. Aby rozwiązać ten problem, spróbuj użyć `await` słowa kluczowego (jeśli jest dostępne) lub <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody.

Analizatory zgodności umożliwiają identyfikowanie interfejsów API i wzorców kodu w kodzie, które mogą powodować problemy w czasie wykonywania za pomocą platformy .NET Core. Przejdź do programu <http://github.com/dotnet/platform-compat> i użyj analizatora interfejsów API platformy .NET.

## <a name="migrating-a-windows-forms-application"></a>Migrowanie aplikacji Windows Forms

Aby zaprezentować pełny proces migracji aplikacji Windows Forms, wybrano migrację przykładowej aplikacji eShop <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> . Pełny wynik migracji można znaleźć pod adresem <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .

Ta aplikacja pokazuje katalog produktów i umożliwia użytkownikowi nawigację, filtrowanie i wyszukiwanie produktów. Z punktu widzenia architektury aplikacja korzysta z zewnętrznej usługi WCF, która służy jako elewacja bazy danych zaplecza.

Główne okno aplikacji można zobaczyć na poniższej ilustracji:

![Główne okno aplikacji](./media/example-migration-core/main-application-window.png)

Jeśli otworzysz plik projektu *. csproj* , zobaczysz coś w następujący sposób:

![Zrzut ekranu przedstawiający zawartość pliku csproj](./media/example-migration-core/csproj-file.png)

Jak wspomniano wcześniej, projekt .NET Core ma bardziej zwarty styl i należy zmigrować strukturę projektu do nowego stylu zestaw .NET Core SDK.

W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt Windows Forms i wybierz polecenie **Zwolnij**  >  **edycję**projektu.

Teraz można zaktualizować plik. csproj. Usuniesz całą zawartość i zastąpisz ją przy użyciu następującego kodu:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

Zapisz i Załaduj ponownie projekt. Teraz zakończysz aktualizowanie pliku projektu, a projekt jest przeznaczony dla platformy .NET Core.

Jeśli kompilujesz projekt w tym momencie, znajdziesz pewne błędy związane z odwołaniem klienta programu WCF. Ponieważ ten kod jest generowany automatycznie, należy ponownie wygenerować go w celu utworzenia docelowej platformy .NET Core.

![Zrzut ekranu przedstawiający błędy kompilacji w programie Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

Usuń plik *Reference.cs* i Wygeneruj nowego klienta usługi.

Kliknij prawym przyciskiem myszy pozycję **połączone usługi** i wybierz opcję **Dodaj usługę połączoną** .

![Zrzut ekranu przedstawiający menu połączone usługi z wybraną opcją Dodaj podłączoną usługę](./media/example-migration-core/add-connected-service.png)

Zostanie otwarte okno połączone usługi. Wybierz opcję **usługi sieci Web Microsoft WCF** .

![Zrzut ekranu okna połączone usługi](./media/example-migration-core/connected-services-window.png)

Jeśli masz usługę WCF w tym samym rozwiązaniu, co w tym przykładzie, możesz wybrać opcję **odnajdywania** zamiast określania adresu URL usługi.

![Zrzut ekranu przedstawiający okno Konfigurowanie odwołania do usługi sieci Web WCF](./media/example-migration-core/configure-wcf-reference.png)

Po zlokalizowaniu usługi narzędzie odzwierciedla kontrakt interfejsu API zaimplementowany przez usługę. Zmień nazwę przestrzeni nazw, aby była `eShopServiceReference` wyświetlana na poniższym obrazie:

![Zrzut ekranu kontraktu interfejsu API i zmieniono przestrzeń nazw](./media/example-migration-core/api-contract-namespace.png)

Wybierz przycisk **Zakończ** . Po czasie zobaczysz wygenerowany kod.

Powinny być widoczne trzy automatycznie generowane pliki:

1. *Wprowadzenie*: link do usługi GitHub w celu udostępnienia pewnych informacji na temat usługi WCF.
2. *Usługę połączoną. JSON*: parametry konfiguracji do nawiązania połączenia z usługą.
3. *Reference.cs*: rzeczywisty kod klienta WCF.

![Zrzut ekranu okna Eksplorator rozwiązań z trzema generowanymi automatycznie plikami](./media/example-migration-core/autogenerated-files.png)

Jeśli kompilujesz ponownie, zobaczysz wiele błędów pochodzących z plików *. cs* w folderze *pomocnika* . Ten folder był obecny w wersji .NET Framework, ale nie znajduje się w starej *csproj*. Ale z nowym projektem w stylu zestawu SDK każdy plik kodu znajdujący się poniżej lokalizacji pliku projektu jest domyślnie uwzględniany. Oznacza to, że nowy projekt .NET Core próbuje skompilować pliki w folderze *pomocnika* . Ponieważ ten folder nie jest wymagany, można go bezpiecznie usunąć.

Po ponownym skompilowaniu projektu i jego wykonaniu nie będą widoczne obrazy produktu. Problem polega na tym, że ścieżka do plików jest nieco nieznacznie zmieniana. Aby rozwiązać ten problem, należy dodać kolejny poziom głębokości w ścieżce, a następnie zaktualizować w pliku `CatalogView.cs` wiersz:

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

na

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

Po tej zmianie można sprawdzić, czy aplikacja jest uruchamiana i uruchamiana zgodnie z oczekiwaniami w programie .NET Core.

## <a name="migrating-a-wpf-application"></a>Migrowanie aplikacji WPF

Użyjemy `Shop.ClassicWPF` przykładowej aplikacji do przeprowadzenia migracji. Na poniższej ilustracji przedstawiono zrzut ekranu aplikacji przed migracją:

![Przykładowa aplikacja przed migracją](./media/example-migration-core/app-before-migration.png)

Ta aplikacja używa lokalnej bazy danych SQL Server Express do przechowywania informacji o katalogu produktów. Ta baza danych jest dostępna bezpośrednio z aplikacji WPF.

Najpierw należy zaktualizować plik *. csproj* do nowego stylu zestawu SDK używanego przez aplikacje platformy .NET Core. Wykonaj te same czynności, które zostały opisane w Windows Forms migracji: spowoduje to zwolnienie projektu, otwarcie pliku *. csproj* , zaktualizowanie jego zawartości i ponowne załadowanie projektu.

W takim przypadku Usuń całą zawartość pliku *. csproj* i zastąp go następującym kodem:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWPF>true</UseWPF>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

Jeśli załadujesz ponownie projekt i skompilujesz go, zostanie wyświetlony następujący błąd:

![Zrzut ekranu przedstawiający błędy kompilacji w programie Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

Ze względu na to, że usunięto całą zawartość *. csproj* , w starym projekcie brakuje specyfikacji odwołania do projektu. Wystarczy dodać ten wiersz do pliku *. csproj* , aby uwzględnić odwołanie do projektu z powrotem:

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

Możesz również pozwolić programowi Visual Studio na pomoc, klikając prawym przyciskiem myszy węzeł **zależności** i wybierając polecenie **Dodaj odwołanie do projektu**. Wybierz projekt z rozwiązania i kliknij przycisk **OK**:

![Zrzut ekranu okna dialogowego Menedżera odwołań z wybranym projektem eshop.](./media/example-migration-core/reference-manager.png)

Po dodaniu brakującego odwołania do projektu aplikacja kompiluje i uruchamia się zgodnie z oczekiwaniami w programie .NET Core.

>[!div class="step-by-step"]
>[Poprzedni](windows-migration.md) 
> [Dalej](deploy-modern-applications.md)
