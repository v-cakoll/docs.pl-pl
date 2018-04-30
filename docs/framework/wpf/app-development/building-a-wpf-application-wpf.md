---
title: Kompilowanie aplikacji WPF (WPF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
caps.latest.revision: 45
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 46572bf2cf8cc52dbd4ba8949dddcd0f88651152
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="building-a-wpf-application-wpf"></a>Kompilowanie aplikacji WPF (WPF)
Aplikacje systemu Windows Presentation Foundation (WPF) może być utworzone jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pliki wykonywalne (.exe), bibliotekach (dll) lub kombinację obu typów zestawów. W tym temacie przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji i opisano kluczowe kroki procesu kompilacji.  
  
  
<a name="Building_a_WPF_Application_using_Command_Line"></a>   
## <a name="building-a-wpf-application"></a>Kompilowanie aplikacji WPF  
 Aplikacja WPF mogą być kompilowane w następujący sposób:  
  
-   Wiersza polecenia. Aplikacja musi zawierać tylko kod (nie XAML) i pliku definicji aplikacji. Aby uzyskać więcej informacji, zobacz [budynku wiersza polecenia z csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [tworzenie z wiersza polecenia (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
-   Microsoft Build Engine (MSBuild). Oprócz kodu i plików XAML aplikacja musi zawierać plik projektu programu MSBuild. Aby uzyskać więcej informacji zobacz "MSBuild".  
  
-   Program Visual Studio. Program Visual Studio jest zintegrowane środowisko programistyczne kompiluje aplikacji WPF przy użyciu programu MSBuild, który zawiera wizualnego projektanta do tworzenia interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [programowanie aplikacji w programie Visual Studio](http://msdn.microsoft.com/library/97490c1b-a247-41fb-8f2c-bc4c201eff68) i [projektanta WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).  
  
<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>   
## <a name="wpf-build-pipeline"></a>Potok kompilacji WPF  
 Gdy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] skompilować projekt, kombinację specyficzny dla języka i [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]-są wywoływane określonych elementów docelowych. Proces wykonywania następujących elementów docelowych jest nazywany potoku kompilacji i klucza kroki są zilustrowane w poniższym rysunku.  
  
 ![Proces kompilacji WPF](../../../../docs/framework/wpf/app-development/media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")  
  
<a name="Pre_Build_Initializations"></a>   
### <a name="pre-build-initializations"></a>Inicjowanie wstępnej kompilacji  
 Przed rozpoczęciem budowania, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] Określa lokalizację ważne narzędzia i biblioteki, w tym następujące:  
  
-   .NET Framework.  
  
-   [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Katalogów.  
  
-   Lokalizacja [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] odwołuje się do zestawów.  
  
-   Właściwość ścieżki wyszukiwania zestawów.  
  
 Pierwszą lokalizację gdzie [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] wyszukuje zestawów jest katalogiem zestawu odwołania (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). W tym kroku procesu kompilacji inicjuje różnych właściwości i grup elementów i wykonuje pracę Oczyszczanie wymagane.  
  
<a name="Resolving_references"></a>   
### <a name="resolving-references"></a>Rozpoznawanie odwołania  
 Proces kompilacji lokalizuje i wiąże zestawy wymagane do utworzenia projektu aplikacji. Istotą takiej logiki jest zawarta w `ResolveAssemblyReference` zadań. Wszystkie zestawy zadeklarowany jako `Reference` w pliku projektu są dostarczane do danego zadania oraz informacje na temat ścieżek wyszukiwania i metadanych dla zestawów już zainstalowane w systemie. Zadanie odwołuje się do zestawów i używa zainstalowanego zestawu metadanych do odfiltrowania tych podstawowych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawy, które należy pokazuj się w manifestach danych wyjściowych. Można to zrobić, aby uniknąć nadmiarowych w manifestów ClickOnce. Na przykład, ponieważ PresentationFramework.dll jest uznawana za przedstawiciela aplikacji wbudowanych oraz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , a ponadto wszystkie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawy istnieje w tej samej lokalizacji, na każdym komputerze, który ma programu .NET Framework zainstalowany, nie istnieje potrzeba aby uwzględnić wszystkie informacje dotyczące wszystkich zestawów odwołań .NET Framework w manifestach.  
  
<a name="Markup_Compilation___Pass_1"></a>   
### <a name="markup-compilationpass-1"></a>Kompilację znaczników — przebieg 1  
 W tym kroku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki są analizowane i skompilowany, dzięki czemu środowiska uruchomieniowego nie poświęcić czas analizowania [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] i sprawdzanie poprawności wartości właściwości. Skompilowana klasa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest stokenizowana sprzed tak, aby w czasie wykonywania, załadowanie go powinno być znacznie szybsze niż ładowanie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.  
  
 W tym kroku następujące działania została wykonana każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku `Page` elementu kompilacji:  
  
1.  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Pliku jest analizowana przez kompilator znaczników.  
  
2.  Reprezentacja skompilowana jest tworzony w tym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i skopiowany do folderu obj\Release.  
  
3.  Reprezentacja CodeDOM klasę częściową jest utworzony i skopiowany do folderu obj\Release.  
  
 Ponadto plik specyficzny dla języka kodu zostanie wygenerowany dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Na przykład dla strony Page1.xaml w projektach Visual Basic, generowane jest Page1.g.vb; na stronie Page1.xaml w projekcie C# Page1.g.cs jest generowany. Wskazuje ".g" w nazwie pliku, plik jest generowany kod, który ma deklarację klasy częściowej dla elementu najwyższego poziomu w pliku znaczników (takich jak `Page` lub `Window`). Klasa jest zadeklarowany za pomocą `partial` modyfikator w języku C# (`Extends` w języku Visual Basic) aby wskazać, istnieje inny deklaracji klasy w innym miejscu, zazwyczaj w kodu powiązanego pliku Page1.xaml.cs.  
  
 Klasy częściowe rozciąga się od odpowiedniej klasy podstawowej (takich jak <xref:System.Windows.Controls.Page> strony) i implementuje <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> interfejsu. <xref:System.Windows.Markup.IComponentConnector> Interfejs ma metodę, aby zainicjować składnika i połącz nazwy i zdarzeń w przypadku elementów w jego zawartości. W rezultacie plik wygenerowany kod ma implementacji metody, takie jak następujące:  
  
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
  
 Domyślnie kompilację znaczników jest uruchamiane w tym samym <xref:System.AppDomain> jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] aparatu. Zapewnia to znaczący wzrost wydajności. To zachowanie może być przełączane `AlwaysCompileMarkupFilesInSeparateDomain` właściwości. To ustawienie zaletą zwalnianie wszystkich zestawów odwołań przez zwalnianie szczegółowych <xref:System.AppDomain>.  
  
<a name="Pass_2_of_Markup_Compilation"></a>   
### <a name="markup-compilationpass-2"></a>Kompilację znaczników — przebieg 2  
 Nie wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony są kompilowane w przebiegu 1 kompilację znaczników. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, które zostały zdefiniowane lokalnie typu odwołania (odwołania do typów zdefiniowanych w kodzie w tym samym projekcie) są wyłączone z kompilacji w tej chwili. Jest to spowodowane te typy zdefiniowane lokalnie istnieje tylko w lokalizacji źródłowej i nie został skompilowany. Aby to ustalić, analizator korzysta z algorytmów heurystycznych, które są związane z elementów takich jak `x:Name` w pliku znaczników. Takie wystąpienie zostanie wykryte, że kompilacji pliku znaczników zostanie odłożona do momentu zostały skompilowane pliki kodu, po którym, drugi kompilację znaczników przekazać procesów tych plików.  
  
<a name="File_Classification"></a>   
### <a name="file-classification"></a>Klasyfikacji plików  
 Pliki wyjściowe naraża procesu kompilacji do różnych grup zasobów oparte na zestawie aplikacji, które będzie można umieścić w. W typowej aplikacji niezlokalizowanej, wszystkie pliki danych są oznaczone jako `Resource` umieszczonych w zestawie głównym (plik wykonywalny lub biblioteka). Gdy `UICulture` jest ustawiony w projekcie, wszystkich skompilowanych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki i zasoby wyraźnie oznaczona jako specyficzne dla języka są umieszczane w zestawu satelickiego zasobów. Ponadto wszystkie zasoby niezależny od języka, są umieszczane w zestawie głównym. W tym kroku procesu kompilacji, która jest wybierana.  
  
 `ApplicationDefinition`, `Page`, I `Resource` akcje kompilacji w pliku projektu można rozszerzyć za pomocą `Localizable` metadanych (dopuszczalne wartości to `true` i `false`), który określa, czy plik jest specyficzny dla języka lub niezależny od języka.  
  
<a name="Core_Compilation"></a>   
### <a name="core-compilation"></a>Podstawowe kompilacji  
 Krok kompilacji core obejmuje kompilacji plików kodu. Jest to zorkiestrowana przez logikę w plikach cele specyficzny dla języka Microsoft.CSharp.targets i Microsoft.VisualBasic.targets. Jeśli heurystyki w ustaleniu, który jednym przebiegu kompilatora znaczników jest wystarczająca, a następnie wygenerowaniu główny zestaw. Jednak jeśli co najmniej jeden [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki w projekcie odwołują się do lokalnie zdefiniowanych typów, a następnie plik tymczasowy dll jest generowany, zestawy końcowego aplikacji mogą zostać utworzone po zakończeniu drugi przebieg kompilację znaczników.  
  
<a name="Manifest_generation"></a>   
### <a name="manifest-generation"></a>Generowanie manifestu  
 Po zakończeniu procesu kompilacji, po wszystkich aplikacji i zestawy, pliki zawartości są gotowe [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] manifesty dla aplikacja są generowane.  
  
 Plik manifestu wdrożenia w tym artykule opisano model wdrażania: Bieżąca wersja zachowania aktualizacji i tożsamości wydawcy oraz podpisu cyfrowego. Tego manifestu ma zostać utworzone przez administratorów, którzy obsługują wdrożenia. Rozszerzenie pliku jest .xbap (dla [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) i .application zainstalowanych aplikacji. Pierwsza jest zależna `HostInBrowser` właściwości projektu i w związku z tym manifest identyfikuje aplikację jako obsługiwane w przeglądarce.  
  
 Manifest aplikacji (. plik exe.manifest) opisano zestawów aplikacji i zależnych bibliotek i list uprawnień wymaganych przez aplikację. Ten plik ma być utworzony przez dewelopera aplikacji. Aby uruchomić [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] aplikacji, użytkownik otwiera plik manifestu wdrożenia aplikacji.  
  
 Te pliki manifestu zawsze są tworzone dla [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Dla zainstalowanych aplikacji, są nie tworzone chyba że `GenerateManifests` właściwość jest określona w pliku projektu o wartości `true`.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] dwa dodatkowe uprawnienia tylko te uprawnienia przypisane do typowych aplikacji stref internetowych: <xref:System.Security.Permissions.WebBrowserPermission> i <xref:System.Security.Permissions.MediaPermission>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] System kompilacji deklaruje tych uprawnień w manifeście aplikacji.  
  
<a name="Incremental_Build_Support"></a>   
## <a name="incremental-build-support"></a>Obsługa wzrostowe  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] System kompilacji obsługuje kompilacje przyrostowe. Jest dość inteligentnie wykrywanie zmian w znaczników lub kodu i kompiluje tylko artefakty zmiany. Mechanizm wzrostowe używa następujących plików:  
  
-   $(*AssemblyName*) _MarkupCompiler.Cache plik, aby zachować bieżący stan kompilatora.  
  
-   $(*AssemblyName*) _MarkupCompiler.lref plik do pamięci podręcznej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki z odwołaniami do typy zdefiniowane lokalnie.  
  
 Oto zestaw zasad regulujących wzrostowe:  
  
-   Plik jest najmniejsza jednostka, w którym system kompilacji wykrywa zmiany. Dzięki dla pliku kodu system kompilacji nie może sprawdzić, czy typu została zmieniona lub kod został dodany. To samo dla plików projektu.  
  
-   Mechanizm wzrostowe muszą być świadome który [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony definiuje klasę lub korzysta z innych klas.  
  
-   Jeśli `Reference` wpisy zmienić, a następnie ponowne skompilowanie wszystkich stron.  
  
-   W przypadku zmiany pliku kodu, skompiluj ponownie wszystkich stron z odwołania do typu zdefiniowane lokalnie.  
  
-   Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zmiany:  
  
    -   Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zadeklarowany jako `Page` w projekcie: Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma odwołania do typu zdefiniowane lokalnie, skompiluj ponownie, który [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony z odwołaniami do lokalnego; Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ma lokalne odwołania, skompiluj ponownie wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron z lokalnego odwołania.  
  
    -   Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zadeklarowany jako `ApplicationDefinition` w projekcie: ponowne skompilowanie wszystkich [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron (Przyczyna: każda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawiera odwołanie do <xref:System.Windows.Application> typu, który mógł ulec zmianie).  
  
-   Jeśli plik projektu deklaruje pliku kodu jako definicji aplikacji zamiast [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku:  
  
    -   Sprawdź, czy `ApplicationClassName` zmieniono wartość w pliku projektu (jest to nowy typ aplikacji?). Jeśli tak, skompiluj ponownie całej aplikacji.  
  
    -   W przeciwnym razie ponownie skompilować wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron z lokalnego odwołania.  
  
-   W przypadku zmiany pliku projektu: zastosowanie wszystkich powyższych reguł i zobacz, co wymaga ponownego skompilowania. Zmienia się na następujących wyzwalacza właściwości pełną ponownej kompilacji: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace`, i `HostInBrowser`.  
  
 Możliwe są następujące scenariusze ponownej kompilacji:  
  
-   Cała aplikacja jest ponownie kompilowana.  
  
-   Tylko te [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, które zostały zdefiniowane lokalnie odwołania do typu jest ponownie kompilowana.  
  
-   Nic nie jest ponownie kompilowana (Jeśli w projekcie nie zaszły żadne zmiany).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [Odwołanie do WPF MSBuild](/visualstudio/msbuild/wpf-msbuild-reference)  
 [Pakowanie URI w WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Zasoby aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
