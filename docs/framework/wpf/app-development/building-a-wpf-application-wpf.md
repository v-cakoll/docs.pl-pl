---
title: Kompilowanie aplikacji WPF (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: 8d24314290e4f385362a3369836e4d18a23cc868
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663105"
---
# <a name="building-a-wpf-application-wpf"></a>Kompilowanie aplikacji WPF (WPF)

Aplikacje Windows Presentation Foundation (WPF) może być kompilowany jako .NET Framework pliki wykonywalne (.exe), biblioteki (.dll) lub kombinacji obu typów zestawów. W tym temacie przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji i opisano kluczowe kroki w procesie kompilacji.

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>Kompilowanie aplikacji WPF

Aplikacja WPF można kompilować w następujący sposób:

- Wiersza polecenia. Aplikacja musi zawierać tylko kod (nie XAML) i plik definicji aplikacji. Aby uzyskać więcej informacji, zobacz [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [tworzenie z wiersza polecenia (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

- Microsoft Build Engine (MSBuild). Oprócz kodu i pliki XAML aplikacja musi zawierać plik projektu programu MSBuild. Aby uzyskać więcej informacji zobacz "MSBuild".

- Program Visual Studio. Visual Studio to zintegrowane środowisko deweloperskie kompiluje aplikacje WPF za pomocą narzędzia MSBuild, która zawiera projektanta wizualnego do tworzenia interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [pisanie kodu i zarządzanie nim przy użyciu programu Visual Studio](/visualstudio/ide/index-writing-code) i [projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>Potok kompilacji WPF

Gdy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projekt jest kompilowany, kombinacja specyficzny dla języka i [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]-określonych elementów docelowych są wywoływane. Proces wykonywania następujących elementów docelowych nosi nazwę potoku kompilacji, i przedstawiono podstawowe etapy według poniższej ilustracji.

![Proces kompilacji WPF](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>Inicjalizacje sprzed kompilacji

Przed kompilacją, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] Określa lokalizację ważne narzędzia i biblioteki, w tym następujące:

- .NET Framework.

- [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Katalogów.

- Lokalizacja [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawów odwołań.

- Właściwość dla ścieżki wyszukiwania zestawów.

Pierwszą lokalizację gdzie [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] wyszukuje zestawy to katalog zestawów odwołania (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). W tym kroku procesu kompilacji inicjuje różnych właściwości i grup elementów i wykonuje wszelkie prace wymagane oczyszczania.

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>Rozpoznawanie odwołania

Proces kompilacji lokalizuje i wiąże zestawów wymaganych do utworzenia projektu aplikacji. Tę logikę znajduje się w `ResolveAssemblyReference` zadania. Wszystkie zestawy zadeklarowane jako `Reference` w pliku projektu są dostarczane do zadania, wraz z informacji na temat ścieżek wyszukiwania i metadane zestawów, które już są zainstalowane w systemie. Zadanie odwołuje się do zestawów i korzysta z metadanych zestawu zainstalowanych umożliwiające filtrowanie tych podstawowych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawów, które muszą wykazują się w manifestach danych wyjściowych. Jest to realizowane w celu uniknięcia nadmiarowe informacje w manifesty ClickOnce. Na przykład, ponieważ PresentationFramework.dll jest uznawana za przedstawiciela aplikacji oparta na i [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i ponadto od wszystkich [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawy istnieje w tej samej lokalizacji na każdym komputerze, który ma programu .NET Framework zainstalowany, nie ma potrzeby obejmujący wszystkie informacje dotyczące wszystkich zestawów odwołań w .NET Framework w manifestach.

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>Kompilacja znaczników — przebieg 1

W tym kroku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki są analizowane i kompilowane tak, aby środowisko uruchomieniowe spędzać czas analizy [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] i sprawdzanie poprawności wartości właściwości. Skompilowana klasa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest stokenizowana wstępnie tak, aby w czasie wykonywania, załadowanie go powinno być znacznie szybciej niż Trwa ładowanie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.

W tym kroku następujące działania wykonane każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku `Page` kompilacji elementu:

1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Przez kompilator znaczników jest analizowany plik.

2. Reprezentację skompilowanego jest tworzony w tym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i skopiowany do folderu obj\Release.

3. CodeDOM reprezentacja klasę częściową jest utworzony i skopiowany do folderu obj\Release.

Ponadto, generowany jest plik kodu języka specyficznego dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Na przykład dla strony Page1.xaml w projektach Visual Basic, generowane jest Page1.g.vb; na stronie Page1.xaml w projektach C# Page1.g.cs jest generowany. ".G" w nazwie pliku wskazuje na to, jest on generowany kod, który zawiera deklarację klasy częściowej najwyższego poziomu elementu pliku znaczników (takie jak `Page` lub `Window`). Klasa jest zadeklarowana za pomocą `partial` modyfikator w języku C# (`Extends` w języku Visual Basic) do wskazania, istnieje inny deklaracji klasy, gdzie indziej, zazwyczaj w związanym z kodem pliku Page1.xaml.cs.

Klasy częściowej rozciąga się od odpowiedniej klasy podstawowej (takie jak <xref:System.Windows.Controls.Page> strony) i implementuje <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> interfejsu. <xref:System.Windows.Markup.IComponentConnector> Interfejsu posiada metody do zainicjowania składnika i połącz nazwy i zdarzeń na elementy w jego zawartości. W związku z tym plik wygenerowanego kodu zawiera implementację metody, jak pokazano poniżej:

```csharp
public void InitializeComponent() {
    if (_contentLoaded) {
        return;
    }
    _contentLoaded = true;
    System.Uri resourceLocater =
        new System.Uri(
            "window1.xaml",
            System.UriKind.RelativeOrAbsolute);
    System.Windows.Application.LoadComponent(this, resourceLocater);
}
```

```vb
Public Sub InitializeComponent() _

    If _contentLoaded Then
        Return
    End If

    _contentLoaded = True
    Dim resourceLocater As System.Uri = _
        New System.Uri("mainwindow.xaml", System.UriKind.Relative)

    System.Windows.Application.LoadComponent(Me, resourceLocater)

End Sub
```

Domyślnie znaczników kompilacji jest uruchamiany w tym samym <xref:System.AppDomain> jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] aparatu. Dzięki temu znaczący wzrost wydajności. To zachowanie może być przełączane z `AlwaysCompileMarkupFilesInSeparateDomain` właściwości. To ma tę zaletę zwolnienie wszystkich zestawów odwołań poprzez zwolnienie do oddzielnych <xref:System.AppDomain>.

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>Kompilacja znaczników — przebieg 2

Nie wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony są kompilowane w przebiegu 1 kompilacji znaczników. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, które lokalnie zdefiniowane typu odwołania (odwołania do typów zdefiniowanych w kodzie, w tym samym projekcie) są wyłączone z kompilacji w tej chwili. Jest to spowodowane te typy zdefiniowane lokalnie istnieje tylko w lokalizacji źródłowej i nie został skompilowany. Aby ustalić tę liczbę, analizator używa algorytmu heurystycznego, które są związane z elementów takich jak `x:Name` w pliku znaczników. Takie wystąpienie zostanie wykryte, że kompilacji pliku znaczników zostanie odłożona do momentu pliki kodu zostały skompilowane, po którym, druga kompilacja znaczników przekazać procesy te pliki.

<a name="File_Classification"></a>

### <a name="file-classification"></a>Klasyfikacja plików

Pliki wyjściowe umieszcza procesu kompilacji w różnych grupach zasobów oparty na zestaw aplikacji, która zostanie umieszczona w. W Typowa aplikacja niezlokalizowanej, wszystkie pliki danych są oznaczone jako `Resource` są umieszczane w głównym zestawie (plik wykonywalny lub biblioteka). Gdy `UICulture` jest ustawiony w projekcie, wszystkich skompilowanych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki i zasoby specjalnie oznaczony jako specyficzny dla języka są umieszczane w satelickim zestawem zasobów. Ponadto wszystkie zasoby niezależny od języka są umieszczane w głównym zestawie. W tym kroku procesu kompilacji, która jest wybierana.

`ApplicationDefinition`, `Page`, I `Resource` akcji kompilacji w pliku projektu można rozszerzyć za pomocą `Localizable` metadanych (dopuszczalne są wartości z `true` i `false`), która określa, czy plik jest specyficzny dla języka lub niezależny od języka.

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>Podstawowe kompilacji

Krok kompilacji core obejmuje kompilacji plików kodu. Jest to zorganizowanych według logiki w plikach specyficzny dla języka, obiekty docelowe Microsoft.CSharp.targets i Microsoft.VisualBasic.targets. Jeśli Algorytm heurystyczny zdecydowano, że jednym przebiegu kompilator znaczników jest wystarczająca, a następnie wygenerowaniu zestawu głównego. Jednakże jeśli jeden lub więcej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki w projekcie odwołują się do lokalnie zdefiniowanych typów, a następnie plik tymczasowy plik .dll jest generowany, więc mogą zostać utworzone zestawy gotowych aplikacji, po zakończeniu przebiegu drugi kompilacji znaczników.

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>Generowanie manifestu

Pod koniec procesu kompilacji, po wykonaniu tych czynności wszystkich zestawów aplikacji i plików zawartości [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] są generowane manifesty aplikacji.

Pliku manifestu wdrożenia w tym artykule opisano model wdrażania: bieżącą wersję, zachowanie aktualizacji i tożsamość wydawcy wraz z podpisu cyfrowego. Tego manifestu ma zostać utworzone przez administratorów, którzy przetwarzają wdrożenia. Rozszerzenie pliku jest XBAP (dla [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) i .application zainstalowanych aplikacji. Pierwsza jest zależna od `HostInBrowser` właściwość projektu i w rezultacie manifest identyfikuje aplikację jako hostowana w przeglądarce.

Manifest aplikacji (. exe.manifest pliku) opisano zestawów aplikacji i zależne biblioteki i listy uprawnień wymaganych przez aplikację. Ten plik ma zostać utworzona przez dewelopera aplikacji. Aby uruchomić [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] aplikacji, użytkownik otwiera plik manifestu wdrażania aplikacji.

Te pliki manifestu są zawsze tworzone dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Zainstalowanych aplikacji, mogą nie są tworzone chyba że `GenerateManifests` właściwość jest określona w pliku projektu z wartością `true`.

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Uzyskaj dwa dodatkowe uprawnienia, oprócz tych uprawnień przypisanych do typowych aplikacjach strefy Internet: <xref:System.Security.Permissions.WebBrowserPermission> i <xref:System.Security.Permissions.MediaPermission>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] System kompilacji deklaruje te uprawnienia w manifeście aplikacji.

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>Kompilacja przyrostowa pomocy technicznej

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] System kompilacji obsługuje kompilacje przyrostowe. Jest dość inteligentnie wykrywanie zmian wprowadzonych do znaczników lub innego kodu, a następnie kompiluje tylko te artefakty, które dotyczy zmiana. Mechanizm kompilacja przyrostowa używa następujących plików:

- $(*AssemblyName*) _MarkupCompiler.Cache plik, aby zachować bieżący stan kompilatora.

- $(*AssemblyName*) _MarkupCompiler.lref plik do pamięci podręcznej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików za pomocą odwołania do typów zdefiniowane lokalnie.

Oto zbiór zasad regulujących kompilacja przyrostowa:

- Plik jest najmniejsza jednostka, w którym system kompilacji wykryje zmianę. Tak dla pliku z kodem, system kompilacji nie wiadomo, czy typ został zmieniony, czy kod został dodany. To samo dla plików projektu.

- Mechanizm kompilacja przyrostowa muszą być świadome, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony definiuje klasę lub korzysta z innych klas.

- Jeśli `Reference` wpisy zmienić, a następnie ponownie skompilować wszystkich stron.

- Jeśli zmieni się plik kodu, należy ponownie skompilować wszystkich stron z odwołań do typu zdefiniowane lokalnie.

- Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zmiany plików:

  - Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zadeklarowany jako `Page` w projekcie: Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie istnieją lokalnie zdefiniowanego typu odwołania, ponownie skompilować, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oraz wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron przy użyciu lokalnego odwołania; Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ma lokalne odwołania, należy ponownie skompilować wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron przy użyciu lokalnego odwołania.

  - Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zadeklarowany jako `ApplicationDefinition` w projekcie: Skompiluj ponownie wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron (Przyczyna: każda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odwołuje się do <xref:System.Windows.Application> typ, który mógł ulec zmianie).

- Jeśli plik projektu deklaruje pliku z kodem jako definicji aplikacji zamiast [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku:

  - Sprawdź, czy `ApplicationClassName` zmianie wartości w pliku projektu (jest to nowy typ aplikacji?). Jeśli tak, należy ponownie skompilować całej aplikacji.

  - W przeciwnym razie ponownie skompilować wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron przy użyciu lokalnego odwołania.

- Jeśli zmiany w pliku projektu: stosowanie wszystkich powyższych zasad i zobacz, co musi być ponownie kompilowane. Zmienia się na następujących wyzwalacza właściwości zakończenie ponownej kompilacji: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace`, i `HostInBrowser`.

Możliwe są następujące scenariusze ponownej kompilacji:

- Cała aplikacja jest ponownie kompilowana.

- Tylko te [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, które lokalnie zdefiniowane odwołań do typu są ponownie kompilowane.

- Nic nie jest ponownie kompilowany, (Jeśli w projekcie nic się nie zmieniło).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
- [Odwołanie do WPF MSBuild](/visualstudio/msbuild/wpf-msbuild-reference)
- [Pakowanie URI w WPF](pack-uris-in-wpf.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md)
