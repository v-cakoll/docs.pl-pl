---
title: Kompilowanie aplikacji WPF (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: a5254de07029e53dd6b72bd2c096c38525a661b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958706"
---
# <a name="building-a-wpf-application-wpf"></a>Kompilowanie aplikacji WPF (WPF)

Aplikacje Windows Presentation Foundation (WPF) mogą być kompilowane jako .NET Framework pliki wykonywalne (. exe), biblioteki (. dll) lub kombinację obu typów zestawów. W tym temacie przedstawiono sposób kompilowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji i opisano kluczowe kroki w procesie kompilacji.

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>Kompilowanie aplikacji WPF

Aplikację WPF można skompilować w następujący sposób:

- Wiersz polecenia. Aplikacja musi zawierać tylko kod (bez XAML) i plik definicji aplikacji. Aby uzyskać więcej informacji, zobacz [wiersza polecenia kompilowanego za pomocą pliku CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilowanie z poziomu wiersza polecenia (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

- Microsoft Build Engine (MSBuild). Oprócz kodu i plików XAML, aplikacja musi zawierać plik projektu programu MSBuild. Aby uzyskać więcej informacji, zobacz "MSBuild".

- Program Visual Studio. Program Visual Studio to zintegrowane środowisko programistyczne, które kompiluje aplikacje WPF z programem MSBuild i zawiera wizualny Projektant do tworzenia interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [pisanie kodu i zarządzanie nim za pomocą programu Visual Studio](/visualstudio/ide/index-writing-code) i [projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>Potok kompilacji WPF

Po skompilowaniu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]projektujestwywoływana kombinacja obiektów docelowych specyficznych dla języka i określonych. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Proces wykonywania tych celów jest nazywany Potokiem kompilacji, a kluczowe kroki przedstawiono na poniższej ilustracji.

![Proces kompilacji WPF](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>Inicjalizacje przed kompilacją

Przed skompilowaniem program MSBuild określa lokalizację ważnych narzędzi i bibliotek, w tym następujące elementy:

- .NET Framework.

- [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Katalogi.

- Lokalizacja [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawów referencyjnych.

- Właściwość ścieżek wyszukiwania zestawu.

Pierwszą lokalizacją, w której program MSBuild wyszukuje zestawy, jest katalogiem zestawu\\odwołania (%PROGRAMFILES%\Reference Assemblies\Microsoft\Framework\v3.0). W tym kroku proces kompilacji inicjuje również różne właściwości i grupy elementów oraz wykonuje wymagane czynności czyszczące.

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>Rozpoznawanie odwołań

Proces kompilacji lokalizuje i wiąże zestawy wymagane do skompilowania projektu aplikacji. Ta logika jest zawarta w `ResolveAssemblyReference` zadaniu. Wszystkie zestawy zadeklarowane `Reference` jako w pliku projektu są dostarczane do zadania wraz z informacjami na temat ścieżek wyszukiwania i metadanych w zestawach zainstalowanych już w systemie. Zadanie wyszukuje zestawy i korzysta z metadanych zainstalowanego zestawu, aby odfiltrować te zestawy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podstawowe, które nie muszą być wyświetlane w manifestach wyjściowych. Jest to gotowe do uniknięcia nadmiarowych informacji w manifestach ClickOnce. Na przykład, ponieważ platformie docelowej. dll może być uważany za reprezentatywną dla aplikacji, która jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wbudowana i dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i a ponadto, ponieważ wszystkie zestawy istnieją w tej samej lokalizacji na każdej maszynie, która ma .NET Framework zainstalowany, nie ma potrzeby uwzględniania wszystkich informacji na wszystkich zestawach odwołań .NET Framework w manifestach.

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>Kompilacja znaczników — Pass 1

W tym kroku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki są analizowane i kompilowane, dzięki czemu środowisko uruchomieniowe nie poświęca czasu na analizowanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] i sprawdzanie poprawności wartości właściwości. Skompilowany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest wstępnie z tokenem, więc w czasie wykonywania ładowanie go powinno być znacznie szybsze niż [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ładowanie pliku.

W tym kroku zostaną wykonane następujące działania dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku, który `Page` jest elementem kompilacji:

1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Plik jest analizowany przez kompilator znaczników.

2. Skompilowana reprezentacja jest tworzona dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tego programu i kopiowana do folderu obj\Release.

3. Reprezentacja CodeDOM nowej klasy częściowej jest tworzona i kopiowana do folderu obj\Release.

Ponadto dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku jest generowany plik kodu specyficzny dla języka. Na przykład dla strony Strona1. XAML w projekcie Visual Basic jest generowany element Strona1. g. vb; dla strony Strona1. XAML w C# projekcie jest generowany page1.g.cs. ". G" w nazwie pliku wskazuje, że plik jest generowany kod, który ma deklarację klasy częściowej dla elementu najwyższego poziomu pliku znaczników (na przykład `Page` lub `Window`). Klasa jest zadeklarowana z `partial` modyfikatorem w C# (`Extends` w Visual Basic), aby wskazać, że istnieje inna Deklaracja dla klasy, zwykle w pliku związanym z kodem page1.XAML.cs.

Klasa częściowa rozciąga się od odpowiedniej klasy bazowej (na przykład <xref:System.Windows.Controls.Page> dla strony) i <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> implementuje interfejs. <xref:System.Windows.Markup.IComponentConnector> Interfejs ma metody inicjowania składnika oraz łączenia nazw i zdarzeń w elementach zawartości. W związku z tym wygenerowany plik kodu ma implementację metody podobną do następującej:

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

Domyślnie kompilacja znaczników jest uruchamiana w taki sam <xref:System.AppDomain> sposób, jak aparat MSBuild. Zapewnia to znaczący wzrost wydajności. Takie zachowanie może być przełączane za `AlwaysCompileMarkupFilesInSeparateDomain` pomocą właściwości. Zaletą jest zwolnienie wszystkich zestawów referencyjnych przez zwolnienie oddzielenia <xref:System.AppDomain>.

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>Kompilacja znaczników — Pass 2

Nie wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony są kompilowane podczas kompilacji znaczników 1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pliki, które mają lokalnie zdefiniowane odwołania typu (odwołania do typów zdefiniowanych w kodzie w innym projekcie) są wykluczone z kompilacji w tej chwili. Wynika to z faktu, że te typy zdefiniowane lokalnie istnieją tylko w źródle i nie zostały jeszcze skompilowane. Aby to ustalić, Analizator używa algorytmów heurystycznych, które obejmują Wyszukiwanie elementów takich jak `x:Name` w pliku znaczników. Gdy takie wystąpienie zostanie znalezione, kompilacja pliku znaczników jest odkładana do momentu skompilowania plików kodu, a następnie drugi przebieg kompilacji znaczników przetwarza te pliki.

<a name="File_Classification"></a>

### <a name="file-classification"></a>Klasyfikacja pliku

Proces kompilacji umieszcza pliki wyjściowe w różnych grupach zasobów na podstawie zestawu aplikacji, w którym zostaną umieszczone. W typowej aplikacji nielokalnej wszystkie pliki danych oznaczone jako `Resource` są umieszczane w zestawie głównym (plik wykonywalny lub biblioteka). Gdy `UICulture` jest ustawiony w projekcie, wszystkie skompilowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki i te, które zostały oznaczone jako specyficzne dla języka, są umieszczane w zestawie zasobów satelity. Ponadto wszystkie zasoby niezależne od języka są umieszczane w zestawie głównym. W tym kroku procesu kompilacji to oznaczenie zostało wykonane.

`true` `false`Akcje, i`Page` kompilacji`Resource` w pliku`Localizable` projektu można rozszerzyć za pomocą metadanych (akceptowalne wartości to i), które określają, czy plik jest specyficzny dla języka, czy `ApplicationDefinition` niezależny od języka.

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>Kompilacja podstawowa

Podstawowy krok kompilowania obejmuje kompilację plików kodu. Jest on zorganizowany przez logikę w plikach docelowych określonych dla języka Microsoft. CSharp. targets i Microsoft. VisualBasic. targets. Jeśli algorytmy heurystyczne ustaliły, że jeden przebieg kompilatora znaczników jest wystarczający, generowany jest zestaw główny. Jeśli jednak co najmniej jeden [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik w projekcie zawiera odwołania do typów zdefiniowanych lokalnie, zostanie wygenerowany tymczasowy plik dll, aby można było utworzyć końcowe zestawy aplikacji po zakończeniu drugiego przebiegu kompilacji znaczników.

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>Generowanie manifestu

Na końcu procesu kompilacji, gdy wszystkie zestawy aplikacji i pliki zawartości są gotowe, są generowane manifesty ClickOnce dla aplikacji.

Plik manifestu wdrożenia opisuje model wdrażania: bieżącą wersję, zachowanie aktualizacji i tożsamość wydawcy wraz z podpisem cyfrowym. Ten manifest jest przeznaczony dla administratorów, którzy obsługują wdrażanie. Rozszerzenie pliku to. XBAP (dla [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) i aplikacja dla zainstalowanych aplikacji. Dawniej jest określany przez `HostInBrowser` właściwość projektu i w wyniku tego manifest identyfikuje aplikację jako obsługiwaną przez przeglądarkę.

Manifest aplikacji (plik. exe. manifest) opisuje zestawy aplikacji i biblioteki zależne oraz listę uprawnień wymaganych przez aplikację. Ten plik jest przeznaczony dla deweloperów aplikacji. Aby można było uruchomić aplikację ClickOnce, użytkownik otwiera plik manifestu wdrażania aplikacji.

Te pliki manifestu są zawsze tworzone dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]programu. W przypadku zainstalowanych aplikacji nie są one tworzone, chyba `GenerateManifests` że właściwość zostanie określona w pliku projektu z wartością `true`.

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Uzyskaj dwa dodatkowe uprawnienia ponad i powyżej tych uprawnień przypisanych do typowych aplikacji internetowych: <xref:System.Security.Permissions.WebBrowserPermission> i <xref:System.Security.Permissions.MediaPermission>. System [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kompilacji deklaruje te uprawnienia w manifeście aplikacji.

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>Obsługa kompilacji przyrostowej

System [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kompilacji zapewnia obsługę kompilacji przyrostowych. Jest to dość inteligentne informacje o wykrywaniu zmian wprowadzonych w znacznikach lub kodzie, a także kompiluje tylko te artefakty, na które wpłynie zmiana. Mechanizm kompilacji przyrostowej używa następujących plików:

- Plik $ (*AssemblyName*) _MarkupCompiler. cache do obsługi bieżącego stanu kompilatora.

- Plik $ (*AssemblyName*) _MarkupCompiler. Lref do buforowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików z odwołaniami do typów zdefiniowanych lokalnie.

Poniżej znajduje się zestaw reguł dotyczących kompilacji przyrostowej:

- Ten plik jest najmniejszą jednostką, w której system kompilacji wykryje zmianę. Dlatego w przypadku pliku kodu system kompilacji nie może stwierdzić, czy typ został zmieniony lub czy kod został dodany. Te same blokady dla plików projektu.

- Mechanizm kompilacji przyrostowej musi być firma Cognizant, że [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strona definiuje klasę lub używa innych klas.

- W `Reference` przypadku zmiany wpisów należy ponownie skompilować wszystkie strony.

- W przypadku zmiany pliku kodu należy ponownie skompilować wszystkie strony z odwołaniami do typu zdefiniowane lokalnie.

- W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przypadku zmiany pliku:

  - Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zadeklarowana `Page` jako w projekcie: Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma odwołań do typu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokalnego, należy ją ponownie skompilować oraz wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony z odwołaniami lokalnymi; Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ma on wartość lokalną odwołuje się do programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , RECOMPILE wszystkie strony z odwołaniami lokalnymi.

  - Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zadeklarowana `ApplicationDefinition` jako w projekcie: ponownie Kompiluj wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony <xref:System.Windows.Application> (Przyczyna: Każdy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ma odwołanie do typu, który mógł ulec zmianie).

- Jeśli plik projektu deklaruje plik kodu jako definicję aplikacji zamiast [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku:

  - Sprawdź, `ApplicationClassName` czy wartość w pliku projektu została zmieniona (czy istnieje nowy typ aplikacji?). W takim przypadku należy ponownie skompilować całą aplikację.

  - W przeciwnym razie Skompiluj ponownie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wszystkie strony z odwołaniami lokalnymi.

- Jeśli plik projektu ulegnie zmianie: Zastosuj wszystkie poprzednie reguły i zobacz, co należy ponownie skompilować. Zmiany w następujących właściwościach wyzwalają pełną ponowną kompilację `IntermediateOutputPath`: `RootNamespace` `AssemblyName`,, `HostInBrowser`, i.

Możliwe są następujące scenariusze ponownej kompilacji:

- Cała aplikacja zostanie ponownie skompilowana.

- Ponownie kompilowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są tylko te pliki, które mają lokalnie zdefiniowane odwołania do typu.

- Nic nie jest ponownie kompilowane (Jeśli nic w projekcie nie zostało zmienione).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
- [Odwołanie do WPF MSBuild](/visualstudio/msbuild/wpf-msbuild-reference)
- [Pakowanie URI w WPF](pack-uris-in-wpf.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md)
