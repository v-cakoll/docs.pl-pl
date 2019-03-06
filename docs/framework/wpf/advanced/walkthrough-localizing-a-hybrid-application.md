---
title: 'Przewodnik: Lokalizacja aplikacji hybrydowej'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 116a847d4f7b0591e823416cf5744e68d689c6ee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378083"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Przewodnik: Lokalizacja aplikacji hybrydowej

W tym instruktażu pokazano, jak zlokalizować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]— na podstawie aplikacji hybrydowych.

Zadania zilustrowane w tym przewodniku obejmują:

-   Tworzenie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projektu hosta.

-   Dodawanie możliwych do zlokalizowania zawartości.

-   Włączanie lokalizacji.

-   Przypisywanie identyfikatorów zasobów.

-   Przy użyciu locbaml — narzędzie do tworzenia zestawu satelickiego.

Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [lokalizowanie przykładowej aplikacji hybrydowych](https://go.microsoft.com/fwlink/?LinkID=160015).

Po zakończeniu masz hybrydowej zlokalizowanych aplikacji.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Tworząc projekt hosta Windows Forms

Pierwszym krokiem jest utworzenie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji projektu i dodawanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu z zawartością, która będzie lokalizowany.

### <a name="to-create-the-host-project"></a>Aby utworzyć projekt hosta

1.  Tworzenie **aplikacja WPF** projektu o nazwie `LocalizingWpfInWf`.  (**Pliku** > **nowe** > **projektu** > **Visual C#** lub **języka Visual Basic**   >  **Classic Desktop** > **aplikacji WPF**).

2.  Dodaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> element o nazwie `SimpleControl` do projektu.

3.  Użyj <xref:System.Windows.Forms.Integration.ElementHost> formantu, aby umieścić `SimpleControl` elementu w formularzu. Aby uzyskać więcej informacji, zobacz [instruktażu: Hosting złożonego formantu 3D WPF w formularzach Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Dodawanie możliwych do zlokalizowania zawartości

Następnie dodasz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolka etykiety i ustaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości elementu do zlokalizowania ciągu.

### <a name="to-add-localizable-content"></a>Aby dodać możliwych do zlokalizowania zawartości

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **SimpleControl.xaml** aby otworzyć go w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2.  Ustaw zawartość <xref:System.Windows.Controls.Button> kontrolować, używając następującego kodu.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Form1** aby go otworzyć w programie Windows Forms Designer.

4.  Otwórz **przybornika** i kliknij dwukrotnie **etykiety** można dodać kontrolkę typu etykieta do formularza. Ustaw wartość jego <xref:System.Windows.Forms.Control.Text%2A> właściwość `"Hello"`.

5.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

     Zarówno `SimpleControl` elementu i formant etykiety wyświetlić tekst **"Hello"**.

## <a name="enabling-localization"></a>Włączanie lokalizacji

Windows Forms Designer udostępnia ustawienia umożliwiające włączanie lokalizacji w zestawie satelickim.

### <a name="to-enable-localization"></a>Można włączyć lokalizacji

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Form1.cs** aby go otworzyć w programie Windows Forms Designer.

2.  W **właściwości** okna, ustaw wartość w postaci **Lokalizowalny** właściwość `true`.

3.  W **właściwości** okna, ustaw wartość **języka** właściwości **hiszpański (Hiszpania)**.

4.  W programie Windows Forms Designer wybierz formant etykiety.

5.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwość `"Hola"`.

     Plik zasobów o nazwie Form1.es ES.resx zostanie dodany do projektu.

6.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.cs** i kliknij przycisk **Wyświetl kod** aby go otworzyć w edytorze kodu.

7.  Skopiuj następujący kod do `Form1` konstruktora, poprzedzającym wywołanie `InitializeComponent`.

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **LocalizingWpfInWf** i kliknij przycisk **Zwolnij projekt**.

     Nazwa projektu jest oznaczona etykietą **(niedostępna)**.

9. Kliknij prawym przyciskiem myszy **LocalizingWpfInWf**i kliknij przycisk **Edytuj LocalizingWpfInWf.csproj**.

     Plik projektu zostanie otwarty w edytorze kodu.

10. Skopiuj następujący wiersz do pierwszego `PropertyGroup` w pliku projektu.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Zapisz plik projektu i zamknij go.

12. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **LocalizingWpfInWf** i kliknij przycisk **Załaduj ponownie projekt**.

## <a name="assigning-resource-identifiers"></a>Przypisywanie identyfikatory zasobów

Możliwych do zlokalizowania zawartości można mapować do zestawów zasobów przy użyciu identyfikatorów zasobów. Po określeniu aplikacji MsBuild.exe automatycznie przypisuje identyfikatory zasobów `updateuid` opcji.

### <a name="to-assign-resource-identifiers"></a>Aby przypisać identyfikatory zasobów

1.  Z Menu Start otwórz wiersz polecenia programisty dla programu Visual Studio.

2.  Użyj następującego polecenia, aby przypisać identyfikatory zasobów do zlokalizowania zawartości.

    ```
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **SimpleControl.xaml** aby go otworzyć w edytorze kodu. Zostanie wyświetlony `msbuild` polecenia został dodany `Uid` atrybutu do wszystkich elementów. To ułatwia lokalizacji poprzez przypisywanie identyfikatorów zasobów.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4.  Naciśnij klawisz **F6** do skompilowania rozwiązania.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Przy użyciu locbaml — w celu utworzenia zestawu satelickiego

Zlokalizowane zawartość jest przechowywana w tylko do zasobów *zestawie satelickim*. Narzędzie wiersza polecenia LocBaml.exe do utworzenia zlokalizowanej zestawu dla Twojego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.

### <a name="to-produce-a-satellite-assembly"></a>Aby wygenerować zestawu satelickiego

1.  Skopiuj LocBaml.exe folder obj\Debug tego projektu. Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](how-to-localize-an-application.md).

2.  W oknie wiersza polecenia użyj następującego polecenia, aby wyodrębnić ciągów zasobów do pliku tymczasowego.

    ```
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3.  Otwórz plik temp.csv za pomocą programu Visual Studio lub innego edytora tekstu. Zastąp ciąg `"Hello"` z tłumaczeniem hiszpańskim `"Hola"`.

4.  Zapisz plik temp.csv.

5.  Użyj następującego polecenia, aby wygenerować plik zlokalizowanych zasobów.

    ```
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     Plik LocalizingWpfInWf.g.es ES.resources jest tworzony w folderze obj\Debug.

6.  Użyj następującego polecenia do tworzenia zestawu satelickiego zlokalizowane.

    ```
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     Plik LocalizingWpfInWf.resources.dll jest tworzony w folderze obj\Debug.

7.  Skopiuj plik LocalizingWpfInWf.resources.dll do folderu bin\Debug\es ES projektu. Zastąp istniejący plik.

8.  Uruchom LocalizingWpfInWf.exe, który znajduje się w folderze bin\Debug Twojego projektu. Nie ponownie skompiluj aplikację lub zestawie satelickim zostaną zastąpione.

     Aplikacja zawiera zlokalizowane ciągi zamiast ciągi w języku polskim.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Lokalizowanie aplikacji](how-to-localize-an-application.md)
- [Przewodnik: Lokalizowanie interfejsów Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
