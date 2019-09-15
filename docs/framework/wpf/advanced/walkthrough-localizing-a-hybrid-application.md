---
title: 'Przewodnik: lokalizowanie aplikacji hybrydowej'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b98bf7b3f0aa4e7698a5c0ca7c8ae16051ce6300
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991774"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Przewodnik: lokalizowanie aplikacji hybrydowej

W tym instruktażu pokazano, jak lokalizować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy w aplikacjihybrydowejopartejnabazie.[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hosta.

- Dodawanie lokalizowalnej zawartości.

- Włączanie lokalizacji.

- Przypisywanie identyfikatorów zasobów.

- Używanie narzędzia LocBaml do tworzenia zestawu satelickiego.

Aby uzyskać pełną listę kodu zadań przedstawionych w tym przewodniku, zobacz [lokalizowanie przykładowej aplikacji hybrydowej](https://go.microsoft.com/fwlink/?LinkID=160015).

Po zakończeniu będziesz mieć zlokalizowaną aplikację hybrydową.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Tworzenie projektu hosta Windows Forms

Pierwszym krokiem jest utworzenie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projektu aplikacji i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dodanie elementu z zawartością, która zostanie zlokalizowana.

### <a name="to-create-the-host-project"></a>Aby utworzyć projekt hosta

1. Utwórz projekt **aplikacji WPF** o nazwie `LocalizingWpfInWf`.  (**Plik** > **Nowy** **projekt Visual C#**  Visual Basic**klasyczna** **Aplikacja WPF**Desktop) > . >  >  > 

2. Dodaj element o nazwie`SimpleControl` do projektu. <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

3. Użyj kontrolki, <xref:System.Windows.Forms.Integration.ElementHost> aby `SimpleControl` umieścić element w formularzu. Aby uzyskać więcej informacji, [zobacz Przewodnik: Hostowanie złożonej kontrolki WPF 3D w Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Dodawanie lokalizowalnej zawartości

Następnie dodasz kontrolkę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]etykietai ustawisz zawartość elementu na Lokalizowalny ciąg. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]

### <a name="to-add-localizable-content"></a>Aby dodać lokalizowalną zawartość

1. W **Eksplorator rozwiązań**kliknij dwukrotnie [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]plik **SimpleControl. XAML** , aby otworzyć go w.

2. Ustaw zawartość <xref:System.Windows.Controls.Button> formantu przy użyciu następującego kodu.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. W **Eksplorator rozwiązań**kliknij dwukrotnie przycisk **Form1** , aby otworzyć go w Projektant formularzy systemu Windows.

4. Otwórz **Przybornik** i kliknij dwukrotnie **etykietę** , aby dodać kontrolkę etykieta do formularza. Ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości na `"Hello"`.

5. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.

     Zarówno element, jak i kontrolka etykieta wyświetlają tekst **"Hello".** `SimpleControl`

## <a name="enabling-localization"></a>Włączanie lokalizacji

Projektant formularzy systemu Windows zawiera ustawienia umożliwiające włączenie lokalizacji w zestawie satelickim.

### <a name="to-enable-localization"></a>Aby włączyć lokalizację

1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **Form1.cs** , aby otworzyć ją w Projektant formularzy systemu Windows.

2. W oknie **Właściwości** ustaw wartość właściwości **Lokalizowalny** formularza na `true`.

3. W oknie **Właściwości** ustaw wartość właściwości **Language** na **hiszpański (Hiszpania)** .

4. W Projektant formularzy systemu Windows wybierz kontrolkę etykieta.

5. W oknie **Właściwości** ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości na `"Hola"`.

     Nowy plik zasobów o nazwie Form1.es-ES. resx zostanie dodany do projektu.

6. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1.cs** , a następnie kliknij pozycję **Wyświetl kod** , aby otworzyć ją w edytorze kodu.

7. Skopiuj następujący kod do `Form1` konstruktora, poprzedzając `InitializeComponent`wywołanie metody.

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **LocalizingWpfInWf** , a następnie kliknij pozycję **Zwolnij projekt**.

     Nazwa projektu ma etykietę **(niedostępna)** .

9. Kliknij prawym przyciskiem myszy pozycję **LocalizingWpfInWf**, a następnie kliknij pozycję **Edytuj LocalizingWpfInWf. csproj**.

     Plik projektu zostanie otwarty w edytorze kodu.

10. Skopiuj poniższy wiersz do pierwszego `PropertyGroup` w pliku projektu.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Zapisz plik projektu i zamknij go.

12. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **LocalizingWpfInWf** , a następnie kliknij pozycję **Załaduj ponownie projekt**.

## <a name="assigning-resource-identifiers"></a>Przypisywanie identyfikatorów zasobów

Można zmapować lokalizowalną zawartość na zestawy zasobów przy użyciu identyfikatorów zasobów. Aplikacja MsBuild. exe automatycznie przypisuje identyfikatory zasobów podczas określania `updateuid` opcji.

### <a name="to-assign-resource-identifiers"></a>Aby przypisać identyfikatory zasobów

1. Z menu Start Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio.

2. Użyj następującego polecenia, aby przypisać identyfikatory zasobów do lokalizowalnej zawartości.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. W **Eksplorator rozwiązań**kliknij dwukrotnie plik **SimpleControl. XAML** , aby otworzyć go w edytorze kodu. Zobaczysz, że `msbuild` polecenie `Uid` dodało atrybut do wszystkich elementów. Ułatwia to lokalizowanie identyfikatorów zasobów.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Naciśnij klawisz **F6** , aby skompilować rozwiązanie.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Tworzenie zestawu satelickiego za pomocą LocBaml

Zlokalizowana zawartość jest przechowywana w *zestawie satelickim*obsługującym tylko zasoby. Użyj narzędzia wiersza polecenia LocBaml. exe, aby utworzyć zlokalizowany zestaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.

### <a name="to-produce-a-satellite-assembly"></a>Aby utworzyć zestaw satelicki

1. Skopiuj plik LocBaml. exe do folderu obj\Debug projektu. Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](how-to-localize-an-application.md).

2. W oknie wiersza polecenia Użyj następującego polecenia, aby wyodrębnić ciągi zasobów do pliku tymczasowego.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Otwórz plik temp. CSV z programem Visual Studio lub innym edytorem tekstu. Zastąp ciąg `"Hello"` wyrażeniem hiszpańskim `"Hola"`.

4. Zapisz plik temp. csv.

5. Użyj następującego polecenia, aby wygenerować zlokalizowany plik zasobów.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     Plik LocalizingWpfInWf.g.es-ES. Resources jest tworzony w folderze obj\Debug.

6. Użyj następującego polecenia, aby skompilować zlokalizowany zestaw satelicki.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     Plik LocalizingWpfInWf. resources. dll jest tworzony w folderze obj\Debug.

7. Skopiuj plik LocalizingWpfInWf. resources. dll do folderu bin\Debug\es-ES projektu. Zastąp istniejący plik.

8. Uruchom program LocalizingWpfInWf. exe, który znajduje się w folderze bin\Debug projektu. Nie Kompiluj ponownie aplikacji lub zestaw satelicki zostanie nadpisany.

     Aplikacja pokazuje zlokalizowane ciągi zamiast ciągów w języku angielskim.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Lokalizowanie aplikacji](how-to-localize-an-application.md)
- [Przewodnik: Lokalizowanie Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
