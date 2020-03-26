---
title: 'Wskazówki: lokalizacja aplikacji hybrydowej'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111117"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Wskazówki: lokalizacja aplikacji hybrydowej

W tym przewodniku pokazano, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zlokalizować elementy w aplikacji hybrydowej opartej na formularzach systemu Windows.

Zadania zilustrowane w tym przewodniku obejmują:

- Tworzenie projektu hosta formularzy systemu Windows.

- Dodawanie zawartości zlokalizowanej.

- Włączanie lokalizacji.

- Przypisywanie identyfikatorów zasobów.

- Za pomocą narzędzia LocBaml do produkcji zestawu satelickiego.

Aby uzyskać pełną listę kod zadań zilustrowanych w tym instruktażu, zobacz [Lokalizowanie przykładu aplikacji hybrydowej](https://go.microsoft.com/fwlink/?LinkID=160015).

Po zakończeniu będziesz mieć zlokalizowaną aplikację hybrydową.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Tworzenie projektu hosta formularzy systemu Windows

Pierwszym krokiem jest utworzenie projektu aplikacji Formularze systemu Windows i dodanie elementu z zawartością, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] która będzie się ulaszować.

### <a name="to-create-the-host-project"></a>Aby utworzyć projekt hosta

1. Utwórz projekt aplikacji `LocalizingWpfInWf` **WPF** o nazwie .  (Plik**File** > **Nowy** > **projekt Visual** > **C#** lub **Visual Basic** > **Classic Desktop** > **WPF Aplikacji**).

2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> Dodaj element `SimpleControl` wywoływany do projektu.

3. Użyj <xref:System.Windows.Forms.Integration.ElementHost> formantu, `SimpleControl` aby umieścić element w formularzu. Aby uzyskać więcej informacji, zobacz [Przewodnik: Hostowanie kontrolki złożonej 3D WPF w formularzach systemu Windows](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Dodawanie zawartości zlokalizowanej

Następnie należy dodać formant etykiety windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] forms i ustawić zawartość elementu na ciąg lokalizowalny.

### <a name="to-add-localizable-content"></a>Aby dodać zawartość konfigurowalną

1. W **Eksploratorze rozwiązań**kliknij dwukrotnie **simplecontrol.xaml,** aby otworzyć go w Projektancie WPF.

2. Ustaw zawartość formantu przy <xref:System.Windows.Controls.Button> użyciu następującego kodu.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. W **Eksploratorze rozwiązań**kliknij dwukrotnie **pozycję Form1,** aby otworzyć go w Projektancie formularzy systemu Windows.

4. Otwórz **przybornik** i kliknij dwukrotnie **pozycję Etykieta,** aby dodać formant etykiety do formularza. Ustaw wartość jego <xref:System.Windows.Forms.Control.Text%2A> właściwości `"Hello"`na .

5. Naciśnij **klawisz F5,** aby utworzyć i uruchomić aplikację.

     Zarówno `SimpleControl` element, jak i formant etykiety wyświetlają tekst **"Hello"**.

## <a name="enabling-localization"></a>Włączanie lokalizacji

Projektant formularzy systemu Windows udostępnia ustawienia umożliwiające lokalizację w zestawie satelicie.

### <a name="to-enable-localization"></a>Aby włączyć lokalizację

1. W **Eksploratorze rozwiązań**kliknij dwukrotnie **Form1.cs,** aby otworzyć go w Projektancie formularzy systemu Windows.

2. W oknie **Właściwości** ustaw wartość właściwości **Localizable** formularza na `true`.

3. W oknie **Właściwości** ustaw wartość właściwości **Language** na **hiszpański (Hiszpania)**.

4. W projektancie formularzy systemu Windows wybierz kontrolkę etykiety.

5. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Forms.Control.Text%2A> na `"Hola"`.

     Nowy plik zasobów o nazwie Form1.es-ES.resx zostanie dodany do projektu.

6. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **Form1.cs** i kliknij polecenie **Wyświetl kod,** aby otworzyć go w Edytorze kodów.

7. Skopiuj `Form1` następujący kod do konstruktora, poprzedzając wywołanie do `InitializeComponent`.

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję LocalizingWpfInWf** i kliknij polecenie **Zwolnij projekt**.

     Nazwa projektu jest oznaczona etykietą **(niedostępna).**

9. Kliknij prawym przyciskiem myszy **pozycję LocalizingWpfInWf**, a następnie kliknij polecenie **Edytuj lokalizowanieWpfInWf.csproj**.

     Plik projektu zostanie otwarty w Edytorze kodu.

10. Skopiuj następujący `PropertyGroup` wiersz do pierwszego w pliku projektu.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Zapisz plik projektu i zamknij go.

12. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję LocalizingWpfInWf** i kliknij polecenie **Załaduj ponownie projekt**.

## <a name="assigning-resource-identifiers"></a>Przypisywanie identyfikatorów zasobów

Zawartość konfigurowalną można mapować na zestawy zasobów przy użyciu identyfikatorów zasobów. Aplikacja MsBuild.exe automatycznie przypisuje identyfikatory zasobów po `updateuid` określeniu tej opcji.

### <a name="to-assign-resource-identifiers"></a>Aby przypisać identyfikatory zasobów

1. W menu Start otwórz wiersz polecenia dewelopera dla programu Visual Studio.

2. Użyj następującego polecenia, aby przypisać identyfikatory zasobów do zawartości możliwej do zlokalizowania.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. W **Eksploratorze rozwiązań**kliknij dwukrotnie **simplecontrol.xaml,** aby otworzyć go w Edytorze kodu. Zobaczysz, że `msbuild` polecenie `Uid` dodało atrybut do wszystkich elementów. Ułatwia to lokalizację poprzez przypisanie identyfikatorów zasobów.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Naciśnij **klawisz F6,** aby zbudować rozwiązanie.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Tworzenie zestawu satelitarnego za pomocą LocBaml

Zlokalizowana zawartość jest przechowywana w *zestawie satelicie*tylko za zasoby. Użyj narzędzia wiersza polecenia LocBaml.exe, aby utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zlokalizowany zestaw dla zawartości.

### <a name="to-produce-a-satellite-assembly"></a>Aby wyprodukować zespół satelity

1. Skopiuj program LocBaml.exe do folderu obj\Debug projektu. Aby uzyskać więcej informacji, zobacz [Lokalizowanie aplikacji](how-to-localize-an-application.md).

2. W oknie Wiersz polecenia użyj następującego polecenia, aby wyodrębnić ciągi zasobów do pliku tymczasowego.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Otwórz plik temp.csv za pomocą programu Visual Studio lub innego edytora tekstu. Zastąp ciąg `"Hello"` jego `"Hola"`tłumaczeniem na język hiszpański, .

4. Zapisz plik temp.csv.

5. Użyj następującego polecenia, aby wygenerować zlokalizowany plik zasobów.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     Plik LocalizingWpfInWf.g.es-ES.resources jest tworzony w folderze obj\Debug.

6. Użyj następującego polecenia, aby zbudować zlokalizowany zestaw satelickiego.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     Plik LocalizingWpfInWf.resources.dll jest tworzony w folderze obj\Debug.

7. Skopiuj plik LocalizingWpfInWf.resources.dll do folderu bin\Debug\es projektu. Zastąp istniejący plik.

8. Uruchom localizingWpfInWf.exe, który znajduje się w folderze bin\Debug projektu projektu. Nie należy przebudowywać aplikacji lub zestaw satelicie zostanie zastąpiony.

     Aplikacja pokazuje zlokalizowane ciągi zamiast ciągów w języku angielskim.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Lokalizowanie aplikacji](how-to-localize-an-application.md)
- [Przewodnik: Lokalizowanie formularzy systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
