---
title: Migracja systemu Windows 10
description: Głębokie szczegółowe w funkcjach systemu Windows 10, takich jak pakowanie i wyspy XAML.
ms.date: 09/16/2019
ms.openlocfilehash: cd17088b086a32fd3bb37e617d3a1047acedde0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423209"
---
# <a name="windows-10-migration"></a>Migracja systemu Windows 10

Należy wziąć pod uwagę następujące sytuacje: masz działającą aplikację klasyczną, która została opracowana w dniach Windows 7. Korzysta ona z technologii WPF dostępnej w tym czasie i działa prawidłowo, ale ma nieaktualny interfejs użytkownika i zachowania podczas uruchamiania go w systemie Windows 10. Jest to podobne, gdy oglądasz film Futuristic, taki jak macierz i widzisz Neo przy użyciu urządzenia Nokia 8110. Folia działa dobrze po 20 latach, ale będzie raczej korzystać z modernizacji urządzenia.

Dzięki wydaniu systemu Windows 10 firma Microsoft wprowadziła wiele innowacji do obsługi scenariuszy, takich jak tablety i urządzenia dotykowe, oraz zapewnia najlepsze środowisko dla użytkowników systemu operacyjnego firmy Microsoft. Możesz na przykład:

- Zaloguj się przy użyciu funkcji Windows Hello.
- Użyj pióra, aby narysować lub odpisać tekst, który jest rozpoznawany automatycznie i cyfrowo.
- Uruchamiaj lokalnie dostosowane modele AI wbudowane w chmurze przy użyciu WinML.

Wszystkie te funkcje są dostępne dla deweloperów systemu Windows za poorednictwem bibliotek środowisko wykonawcze systemu Windows (WinRT). Można korzystać z tych funkcji w istniejących aplikacjach klasycznych, ponieważ biblioteki są również udostępniane zarówno .NET Framework, jak i .NET Core. Możesz nawet przeprowadzić modernizację interfejsu użytkownika przy użyciu wysp XAML i poprawić wizualizacje i zachowanie aplikacji w zależności od czasu.

Należy pamiętać, że nie trzeba porzucić .NET Framework technologii, aby postępować zgodnie z tą ścieżką modernizacji. Możesz bezpiecznie pozostać na tym komputerze i korzystać z zalet systemu Windows 10 bez naciskania na migrację do platformy .NET Core. Dzięki temu można uzyskać zarówno moc, jak i elastyczność, aby wybrać ścieżkę modernizacji.

## <a name="winrt-apis"></a>Interfejsy API WinRT

Interfejsy API WinRT to zorientowane obiektowo interfejsy programowania aplikacji (API), które umożliwiają deweloperom systemu Windows 10 dostęp do wszystkich systemów operacyjnych. Za poorednictwem interfejsów API WinRT można zintegrować funkcje, takie jak powiadomienia wypychane, interfejsy API urządzeń, programy Microsoft Ink i WinML, między innymi w aplikacjach klasycznych.

Ogólnie rzecz biorąc, interfejsy API WinRT mogą być wywoływane z klasycznej aplikacji klasycznych. Jednak w dwóch głównych obszarach występuje wyjątek dla tej reguły:

* Interfejsy API, które wymagają tożsamości pakietu.
* Interfejsy API, które wymagają wizualizacji, takiej jak XAML lub kompozycja.

### <a name="universal-windows-platform-uwp-packages"></a>Pakiety platforma uniwersalna systemu Windows (platformy UWP)

#### <a name="application-package-identity"></a>Tożsamość pakietu aplikacji

Aplikacje platformy UWP mają system wdrażania, w którym system operacyjny zarządza instalacją i dezinstalacją aplikacji. Wymaga to deklaratywnej instalacji, co oznacza, że kod użytkownika nie jest wykonywany podczas instalacji. Zamiast tego wszystkie aplikacje chcą zintegrować się z systemem, takie jak protokoły, typy plików i rozszerzenia, są zadeklarowane w manifeście aplikacji. W czasie wdrażania potok wdrożenia konfiguruje te punkty integracji. Jedynym sposobem, aby system operacyjny mógł zarządzać wszystkimi tymi funkcjami i śledzić go, jest dla każdego "pakietu" jako tożsamość, unikatowy identyfikator aplikacji.

Niektóre interfejsy API WinRT wymagają, aby ta tożsamość pakietu działała zgodnie z oczekiwaniami. Jednak klasyczne aplikacje klasyczny, takie jak natywne aplikacje C++ lub .NET, korzystają z różnych systemów wdrażania, które nie wymagają tożsamości pakietu. Jeśli chcesz używać tych interfejsów API WinRT w aplikacji klasycznej, musisz podać im tożsamość pakietu.

Jednym ze sposobów na wykonanie tej czynności jest skompilowanie dodatkowego projektu pakietu. Wewnątrz projektu pakietu można wskazać oryginalny projekt kodu źródłowego i określić informacje o tożsamości, które mają być podane.Jeśli zainstalujesz pakiet i uruchomisz zainstalowaną aplikację, zostanie automatycznie wykorzystana identyfikacja umożliwiająca Wywoływanie kodu wszystkich interfejsów API WinRT wymagających tożsamości.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

Możesz sprawdzić, które interfejsy API potrzebują spakowanej tożsamości aplikacji, sprawdzając, czy typ, który zawiera interfejs API jest oznaczony atrybutem [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) .Jeśli tak jest, możesz wywołać, czy z nieopakowanej tradycyjnej aplikacji klasycznej. W przeciwnym razie musisz skonwertować klasyczną aplikację klasycznych na platformy UWP z pomocą projektu pakietu.

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>Zalety pakowania

Oprócz zapewniania dostępu do tych interfejsów API uzyskasz pewne dodatkowe korzyści, tworząc pakiet aplikacji systemu Windows dla aplikacji klasycznej, w tym:

* **Usprawnione wdrożenie**. Aplikacje mają doskonałe doświadczenie w zakresie wdrażania, dzięki czemu użytkownicy mogą bezpiecznie instalować aplikację i aktualizować ją. Jeśli użytkownik zdecyduje się na odinstalowanie aplikacji, zostanie całkowicie usunięty bez śledzenia pozostawionej w tle, co uniemożliwia problem z gniciem systemu Windows.

* **Aktualizacje automatyczne i Licencjonowanie**. Aplikacja może uczestniczyć w wbudowanej licencjonowaniu i funkcjach automatycznych aktualizacji Microsoft Store. Automatyczna aktualizacja to wysoce niezawodny i wydajny mechanizm, ponieważ pobierane są tylko zmienione części plików.

* **Zwiększony zasięg i uproszczony zysków**. Nie może to być przypadek, ale w przypadku wybrania opcji dystrybucji aplikacji za pomocą Microsoft Store dotrzej do milionów użytkowników systemu Windows 10.

* **Dodaj funkcje platformy UWP**. Funkcje platformy UWP można dodawać do pakietu aplikacji we własnym tempie.

#### <a name="prepare-for-packaging"></a>Przygotuj do pakowania

Przed przystąpieniem do tworzenia pakietów aplikacji klasycznych należy zająć się pewnymi punktami przed rozpoczęciem procesu. Aplikacja musi przestrzegać jakichkolwiek zasad i zasad Microsoft Store i uruchamiać je w modelu aplikacji platformy UWP. Na przykład musi zostać uruchomiony na .NET Framework 4.6.2 lub nowszej i zapisuje w `HKEY_CURRENT_USER` gałęzi rejestru, a foldery AppData zostaną zwirtualizowane do lokalizacji lokalnej aplikacji.

Celem projektowania tworzenia pakietów jest oddzielenie stanu aplikacji od stanu systemu przy zachowaniu zgodności z innymi aplikacjami. System Windows 10 osiąga ten cel, umieszczając aplikację w pakiecie platformy UWP. Wykrywa i przekierowuje pewne zmiany w systemie plików i rejestrze w czasie wykonywania, aby spełnić obietnicę zaufanego i czystego zachowania instalacji i dezinstalacji aplikacji dostarczanej przez pakowanie.

Pakiety, które tworzysz dla aplikacji klasycznej, to aplikacje klasyczne, które nie są w trybie piaskownicy, chociaż w aplikacji do zapisu `HKCU` i `AppData` . Ta Wirtualizacja pozwala im na współpracę z innymi aplikacjami w taki sam sposób, jak klasyczne aplikacje klasycznych.

##### <a name="installation"></a>Instalacja

Pakiety aplikacji są instalowane w folderze *% ProgramFiles% \\ WindowsApps \\ package_name*z plikiem wykonywalnym zatytułowanym  `app_name.exe` . Każdy folder pakietu zawiera manifest (o nazwie `AppxManifest.xml` ) zawierający specjalną przestrzeń nazw XML dla spakowanych aplikacji. Wewnątrz tego pliku manifestu jest  `<EntryPoint>`   element, który odwołuje się do aplikacji w pełni zaufanej. Gdy aplikacja jest uruchomiona, nie jest uruchamiana w kontenerze aplikacji, ale zamiast tego jest uruchamiana jako użytkownik w normalnych warunkach.

Po wdrożeniu pliki pakietu są oznaczone jako tylko do odczytu i wielokrotnie blokowane przez system operacyjny. System Windows uniemożliwia uruchamianie aplikacji, jeśli te pliki zostały naruszone.

##### <a name="file-system"></a>System plików

System operacyjny obsługuje różne poziomy operacji systemu plików dla spakowanych aplikacji klasycznych, w zależności od lokalizacji folderu.

W przypadku próby uzyskania dostępu do folderu *AppData* użytkownika system tworzy prywatną lokalizację dla poszczególnych użytkowników. Pozwala to na złudzenie, że spakowana aplikacja edytuje rzeczywisty element *AppData* , gdy rzeczywiście modyfikuje prywatną kopię. Przekierowując zapisy w ten sposób, system może śledzić wszystkie modyfikacje plików wprowadzone przez aplikację. Dzięki temu można czyścić wszystkie pliki podczas odinstalowywania systemu "gnicia" i zapewniające lepsze środowisko usuwania aplikacji dla użytkownika.

##### <a name="registry"></a>Rejestr

Pakiety aplikacji zawierają plik Registry. dat, który służy jako logiczny odpowiednik  `HKLM\Software`   w rzeczywistym rejestrze. W czasie wykonywania ten rejestr wirtualny Scala zawartość tej gałęzi w natywną gałąź systemową w celu zapewnienia pojedynczego widoku obu tych elementów.

Wszystkie zapisy są zachowywane podczas uaktualniania pakietu i usuwane tylko wtedy, gdy aplikacja zostanie odinstalowana.

##### <a name="uninstallation"></a>Odinstalowywanie

Gdy użytkownik odinstaluje pakiet, wszystkie pliki i foldery znajdujące się w obszarze  `C:\Program Files\WindowsApps\package_name` są usuwane, a także wszystkie przekierowane zapisy do programu AppData lub rejestr, który został przechwycony w trakcie tego procesu.

Aby uzyskać szczegółowe informacje o tym, jak spakowana aplikacja obsługuje instalowanie, dostęp do plików, rejestr i odinstalowywanie, zobacz <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> .

Możesz uzyskać pełną listę rzeczy do zaewidencjonowania <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> .

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>Jak dodać interfejsy API WinRT do projektu pulpitu

W tej sekcji znajdziesz przewodnik dotyczący sposobu integrowania wyskakujących powiadomień w istniejącej aplikacji WPF. Chociaż jest to proste w perspektywie kodu, ułatwia to zilustrowanie całego procesu. Powiadomienia to jeden z wielu dostępnych interfejsów API WinRT dostępnych do użycia w aplikacji .NET. W takim przypadku interfejs API wymaga tożsamości pakietu. Ten proces jest bardziej prosty, jeśli interfejsy API nie wymagają tożsamości pakietu.

Przejdźmy do istniejącej przykładowej aplikacji WPF, która odczytuje pliki i pokazuje jej zawartość na ekranie. Celem jest wyświetlenie wyskakującego powiadomienia, gdy aplikacja zostanie uruchomiona.

![Zrzut ekranu przedstawiający przykładową aplikację, która jest uruchamiana](./media/windows-migration/sample-application.png)

Najpierw należy zaewidencjonować następujący link, niezależnie od tego, czy używany interfejs API systemu Windows 10 wymaga tożsamości pakietu:

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

Nasz przykład użyje <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> interfejsu API, który wymaga spakowanej tożsamości:

![Klasa powiadomień w dokumentacji firmy Microsoft](./media/windows-migration/notification-class-documentation.png)

Aby uzyskać dostęp do interfejsu API WinRT, Dodaj odwołanie do `Microsoft.Windows.SDK.Contracts`   pakietu NuGet, a ten pakiet wykona Magic w tle (zobacz szczegóły pod adresem <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> ).

Teraz przygotowano się do rozpoczęcia dodawania kodu.

Utwórz `ShowToastNotification` metodę, która będzie wywoływana podczas uruchamiania aplikacji. Po prostu kompiluje wyskakujące powiadomienie ze wzorca XML:

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

Mimo że projekt kompiluje się, występują błędy, ponieważ interfejs API powiadomień wymaga tożsamości pakietu i jego nie podano. Dodanie projektu pakietu Windows do rozwiązania spowoduje rozwiązanie tego problemu:

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie nowego projektu w programie Visual Studio](./media/windows-migration/add-packaging-project.png)

Wybierz minimalną wersję systemu Windows, która ma być obsługiwana, oraz żądaną wersję. Nie wszystkie interfejsy API WinRT są obsługiwane we wszystkich wersjach systemu Windows 10. Każda aktualizacja systemu Windows 10 dodaje nowe interfejsy API, które są dostępne tylko w tej wersji. Obsługa niskiego poziomu jest niedostępna.

![Wybieranie minimalnej wersji systemu Windows](./media/windows-migration/select-versions.png)

Następnym krokiem jest dodanie aplikacji WPF do projektu pakietu Windows, dodając odwołanie do projektu:

![Dodawanie aplikacji WPF do projektu pakietu Windows](./media/windows-migration/add-application.png)

![Menedżer odwołań](./media/windows-migration/reference-manager.png)

Projekt pakietów systemu Windows może spakować kilka aplikacji, więc należy określić, który z nich jest punktem wejścia:

![Ustawianie punktu wejścia](./media/windows-migration/set-entry-point.png)

Następnym krokiem jest ustawienie projektu WPF jako projektu startowego w konfiguracji rozwiązania. Możesz nacisnąć klawisz F5, aby skompilować i skompilować i wyświetlić wyniki.

![Przykładowa aplikacja uruchamiana i pokazująca wyniki](./media/windows-migration/sample-app-result.png)

Wygenerujemy pakiet, aby można było zainstalować aplikację. Kliknij prawym przyciskiem myszy pozycję **Zapisz**  >  **pakiety aplikacji**.

![Okno dialogowe Tworzenie pakietów aplikacji](./media/windows-migration/create-app-packages.png)

Wybierz opcję pobierania lokalnego, aby wdrożyć aplikację na komputerze:

![Wybieranie opcji pobierania lokalnego](./media/windows-migration/select-sideloading-option.png)

Wybierz architekturę aplikacji dla aplikacji:

![Wybieranie architektury aplikacji](./media/windows-migration/select-app-architecture.png)

Na koniec Utwórz pakiet, klikając pozycję **Utwórz**.

## <a name="xaml-islands"></a>Wyspy XAML

Wyspy XAML to zestaw składników, które umożliwiają deweloperom klasycznym z systemem Windows Korzystanie z kontrolek XAML platformy UWP w istniejących aplikacjach Win32, w tym Windows Forms i WPF.

![Struktura wysp XAML](./media/windows-migration/xaml-islands.png)

Możesz zrobić obraz swojej aplikacji Win32 przy użyciu standardowych kontrolek i spośród nich "Wyspa" platformy UWP interfejs użytkownika, który zawiera kontrolki z nowoczesnego świata. Koncepcja jest podobna, jakby mieć element iFrame wewnątrz strony sieci Web, która wyświetla zawartość z`different page.`

Oprócz dodawania funkcji z interfejsów API systemu Windows 10, możesz dodać fragmenty platformy UWP XAML wewnątrz aplikacji przy użyciu wysp XAML.

Aktualizacja systemu Windows 10 1903 wprowadza zestaw interfejsów API, które umożliwiają hostowanie zawartości XAML platformy UWP w systemie Win32. Tylko aplikacje działające w systemie Windows 10 1903 mogą korzystać z wysp XAML.

### <a name="the-road-to-xaml-islands"></a>Droga z wyspami XAML

Drogi do wysp XAML rozpoczęto w 2012, gdy firma Microsoft wprowadziła interfejsy API WinRT jako platformę do modernizacji aplikacji Win32 (Windows Forms, WPF i natywnych aplikacji Win32). Jednak nowe kontrolki interfejsu użytkownika w środowisku WinRT były dostępne dla nowych aplikacji, ale nie dla istniejących.

W 2015, wraz z systemem Windows 10, platformy UWP. PLATFORMY UWP umożliwia tworzenie aplikacji działających na urządzeniach z systemem Windows, takich jak XBox, Mobile i Desktop. Jeden rok później firma Microsoft ogłosiła mostek Desktop (dawniej znany jako Project Centennial). Mostek Desktop to zestaw narzędzi, które umożliwiają deweloperom przenoszenie istniejących aplikacji Win32 do Microsoft Store. Dodano więcej możliwości w 2017, dzięki czemu deweloperzy mogą ulepszyć swoje aplikacje Win32 przy użyciu niektórych nowych interfejsów API systemu Windows 10, takich jak kafelki dynamiczne i powiadomienia w centrum akcji. Jednak nadal nie są dostępne żadne nowe kontrolki interfejsu użytkownika.

W kompilacji 2018 firma Microsoft ogłosiła sposób, aby deweloperzy mogli korzystać z nowych kontrolek XAML systemu Windows 10 w ich bieżących aplikacjach Win32, bez w pełni migrowania ich aplikacji do platformy UWP. Było to oznakowane jako platformy UWP wyspy XAML.

### <a name="how-it-works"></a>Jak to działa

W aktualizacji systemu Windows 10 1903 wprowadzono kilka interfejsów API hostingu XAML. Dwa z nich są `WindowsXamlManager`   i  `DesktopWindowXamlSource` .

 `WindowsXamlManager`   Klasa obsługuje strukturę XAML platformy UWP. `InitializeForCurrentThread`Metoda ładuje strukturę XAML platformy UWP w bieżącym wątku aplikacji Win32.

 `DesktopWindowXamlSource`   Jest to wystąpienie zawartości wyspy XAML. Ma `Content` Właściwość, która jest odpowiedzialna za tworzenie i ustawianie. `DesktopWindowXamlSource`   Renderuje i pobiera dane wejściowe z elementu HWND. Musi wiedzieć, z którym innym elementem HWND będzie dołączać wyspy XAML, i użytkownik jest odpowiedzialny za ustalanie rozmiarów i pozycjonowanie HWND elementu nadrzędnego.

WPF lub Windows Forms deweloperzy zazwyczaj nie zajmują się tym samym kodem, więc może być trudno zrozumieć i obsłużyć wskaźniki HWND i bazowe okablowanie, aby komunikować się ze światem Win32 i platformy UWP.

#### <a name="the-xaml-islands-net-wrappers"></a>Otoki platformy .NET z wyspami XAML

Zestaw narzędzi Community dla systemu Windows ma ustawiony otoki platformy .NET dla wysp XAML dla WPF lub Windows Forms, które ułatwiają korzystanie z wysp XAML. Te otoki zarządzają elementami HWND, zarządzaniem fokusem, między innymi. Deweloperzy Windows Forms i WPF powinni używać tych otok.

Zestaw narzędzi społeczności systemu Windows oferuje dwa typy kontrolek: zawinięte kontrolki i kontrolki hostingu.

##### <a name="wrapped-controls"></a>Zawinięte kontrolki

Te zawinięte kontrolki zawijają niektóre formanty platformy UWP do kontrolek Windows Forms lub WPF, ukrywając koncepcje platformy UWP dla tych deweloperów. Te kontrolki są następujące:

* WebView i WebViewCompatible
* InkCanvas i InkToolbar
* MediaPlayerElement
* MapControl

Dodaj `Microsoft.Toolkit.Wpf.UI.Controls` pakiet do projektu, Dołącz odwołanie do przestrzeni nazw i zacznij korzystać z nich.

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a>Hostowanie formantów

Potęgi wysp XAML rozciągają się na większość kontrolek, formantów innych firm i formantów niestandardowych opracowanych dla platformy UWP, które można zintegrować w Windows Forms i WPF jako "wyspy" z w pełni funkcjonalnym interfejsem użytkownika. `WindowsXamlHost`Kontrolka dla WPF i Windows Forms umożliwia wykonanie tej czynności.

Na przykład, aby użyć `WindowsXamlHost` formantu w WPF, Dodaj odwołanie do `Microsoft.Toolkit.Wpf.UI.XamlHost` pakietu dostarczonego przez zestaw Windows Community Toolkit.

Po umieszczeniu `WindowsXamlHost` w kodzie interfejsu użytkownika Określ, który typ platformy UWP chcesz załadować. Można wybrać używanie zawiniętej kontrolki, takiej jak `Button` lub bardziej złożonej, składającej się z kilku różnych kontrolek, które są niestandardowymi kontrolkami platformy UWP.

Poniższy przykład pokazuje, jak dodać platformy UWP `Button` :

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

Istnieje jasne zalecenie dotyczące sposobu podejścia i lepszym rozwiązaniem jest posiadanie jednej i większej wyspy XAML zawierającej niestandardową kontrolkę, która nie ma kilku wysp z jedną kontrolką.

Jedną z podstawowych funkcji języka XAML jest powiązanie i działa między kodem Win32 a wyspami. W związku z tym można powiązać, na przykład, Win32 `Textbox` z platformy UWP `Textbox` . Ważną kwestią jest to, że te powiązania są powiązaniami jednokierunkowymi, od platformy UWP do Win32, więc jeśli zaktualizujesz `Textbox` wewnątrz wyspy XAML, pole tekstowe Win32 zostanie zaktualizowane, ale nie w inny sposób.

Aby zapoznać się z przewodnikiem dotyczącym korzystania z wysp XAML, zobacz:

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>Dodawanie niestandardowych kontrolek XAML platformy UWP

Kontrolka niestandardowa XAML to kontrolka (lub kontrolka użytkownika) utworzona przez użytkownika lub przez inne osoby (w tym kontrolki WinUI 2. x). Aby hostować niestandardową kontrolkę platformy UWP w aplikacji Windows Forms lub WPF, będziesz potrzebować:

- Aby użyć `WindowsXamlHost` formantu platformy UWP w aplikacji .NET Core 3. x.
- Aby utworzyć projekt aplikacji platformy UWP, który definiuje `XamlApplication` obiekt.

Twój projekt WPF lub Windows Forms musi mieć dostęp do wystąpienia `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` klasy dostarczonej przez zestaw narzędzi społeczności systemu Windows. Ten obiekt pełni rolę głównego dostawcy metadanych na potrzeby ładowania metadanych dla niestandardowych typów platformy UWP języka XAML w zestawach w bieżącym katalogu aplikacji. Zalecanym sposobem jest dodanie pustego projektu aplikacji (uniwersalnego systemu Windows) do tego samego rozwiązania, w którym znajduje się obiekt WPF lub Windows Forms projektu, i skorygowanie domyślnej klasy aplikacji w tym projekcie.

Kontrolka XAML niestandardowego platformy UWP może być uwzględniona w tej aplikacji platformy UWP lub w niezależnym projekcie biblioteki klas platformy UWP, do której odwołuje się w tym samym rozwiązaniu, co projekt WPF lub Windows Forms.

Szczegółowy opis procesu krok po kroku można sprawdzić pod adresem:

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Biblioteka interfejsu użytkownika systemu Windows (WinUI 2)

Oprócz formantów skrzynki odbiorczej systemu Windows 10, które są dostarczane z systemem operacyjnym, ten sam zespół XAML platformy UWP również dostarcza dodatkowe kontrolki w bibliotece interfejsu użytkownika systemu Windows (**WinUI 2**). WinUI 2 udostępnia oficjalne natywne formanty i funkcje interfejsu użytkownika firmy Microsoft dla aplikacji systemu Windows platformy UWP. te kontrolki mogą być używane wewnątrz Wysp XAML.

WinUI 2 to open source, a informacje można znaleźć pod adresem <https://github.com/microsoft/microsoft-ui-xaml> .

W poniższym artykule pokazano, jak hostować kontrolkę XAML platformy UWP z biblioteki WinUI 2:<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>Potrzebujesz wysp XAML

Wyspy XAML są przeznaczone dla istniejących aplikacji Win32, które chcą ulepszyć środowisko użytkownika dzięki wykorzystaniu nowych kontrolek i zachowań platformy UWP bez konieczności pełnego ponownego zapisu aplikacji. Możesz już [korzystać z interfejsów API systemu Windows 10](/windows/uwp/porting/desktop-to-uwp-enhance), ale aż do wysp XAML, tylko interfejsów API związanych z interfejsem użytkownika.

Jeśli tworzysz nową aplikację systemu Windows, prawdopodobnie jest to właściwe podejście do [aplikacji platformy UWP](/windows/uwp/get-started/universal-application-platform-guide)   .

### <a name="the-road-ahead-xaml-islands-winui-30"></a>Wyspy XAML o drodze: WinUI 3,0

Ponieważ system Windows 8, Platforma interfejsu użytkownika systemu Windows, w tym Struktura interfejsu użytkownika języka XAML, warstwa kompozycji wizualnej i przetwarzanie danych wejściowych, zostały dostarczone jako integralna część systemu Windows. Oznacza to, że aby skorzystać z najnowszych ulepszeń technologii interfejsu użytkownika, należy przeprowadzić uaktualnienie do najnowszej wersji interfejsu użytkownika, spowalniając innowacje podczas opracowywania aplikacji. Aby oddzielić te dwa cykle ewolucji i wspierać innowacje, firma Microsoft aktywnie pracuje nad projektem WinUI.

Począwszy od WinUI 2 w 2018, firma Microsoft uruchomiła nowe kontrolki interfejsu użytkownika XAML i funkcje jako oddzielne pakiety NuGet, które kompilują się na bazie zestawu SDK platformy UWP.

![Struktura WinUI 2,0](./media/windows-migration/winui2.png)

WinUI 3 jest w fazie aktywnego programowania i znacząco rozszerza zakres WinUI w taki sposób, aby obejmował pełną platformę interfejsu użytkownika, która zostanie całkowicie oddzielona od zestawu SDK platformy UWP:

![Struktura WinUI 3,0](./media/windows-migration/winui3.png)

Środowisko XAML będzie teraz opracowywane w usłudze GitHub i dostarczane poza pasmem jako pakiety [NuGet](/nuget/what-is-nuget)   .

Istniejące interfejsy API XAML platformy UWP, które są dostarczane jako część systemu operacyjnego, nie będą już otrzymywać nowych aktualizacji funkcji. Będą oni nadal otrzymywać aktualizacje zabezpieczeń i poprawki krytyczne zgodnie z cyklem pomocy technicznej systemu Windows 10.

Platforma uniwersalna systemu Windows zawiera więcej niż tylko strukturę języka XAML (na przykład modele aplikacji i zabezpieczeń, potoki multimediów, integracje z usługą Xbox i Windows 10 Shell, szeroką obsługę urządzeń) i będą nadal rozwijane. Wszystkie nowe funkcje XAML zostaną po prostu opracowane i dostarczane jako część WinUI.

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>WinUI 3 w aplikacji klasycznej i WinUIe wyspy XAML

Jak widać, WinUI 3 to ewolucja platformy UWP XAML, która działa w sposób naturalny w modelu aplikacji platformy UWP i wszystkie jej wymagania (MSIX spakowanego identyfikatora, piaskownicy, uaktywnić element corewindow itd.). Aby użyć tylko WinUI 3 w modelu aplikacji Win32, zawartość WinUI powinna być hostowana przez inną strukturę interfejsu użytkownika (Windows Forms, WPF itd.) przy użyciu **wysp WINUI XAML**. Jest to odpowiednia ścieżka, jeśli chcesz rozwijać aplikację i technologie mieszane. Jeśli jednak chcesz zastąpić cały stary interfejs użytkownika WinUI, aplikacja nie powinna ładować struktur interfejsu użytkownika tylko w celu hostowania WinUI.

WinUI 3 będzie rozwiązać ten krytyczną opinię Dodawanie **WinUI w aplikacjach klasycznych**. Dzięki temu aplikacje Win32 będą mogły używać WinUI 3 jako autonomicznej struktury interfejsu użytkownika. nie trzeba ładować Windows Forms ani WPF.

W ramach tej agregacji WinUI 3 umożliwi deweloperom łatwe mieszanie i dopasowanie odpowiedniej kombinacji:

* Model aplikacji: platformy UWP, Win32
* Platforma: .NET Core lub Native
* Język: .NET (C \# , Visual Basic), standard C++
* Pakowanie: MSIX, AppX dla Microsoft Store, nieopakowany
* Międzyoperacyjność: Użyj WinUI 3, aby rozłożyć istniejące aplikacje WPF, WinForms i MFC przy użyciu WinUIych wysp XAML.

Jeśli chcesz poznać więcej szczegółów, firma Microsoft udostępnia ten plan w programie <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> .

>[!div class="step-by-step"]
>[Poprzedni](migrate-modern-applications.md) 
> [Dalej](example-migration-core.md)
