---
title: Tworzenie InkCanvas w aplikacji WPF w programie Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: ebbf25037921e7802b2bfcb6ffa562d16a849ffa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920248"
---
# <a name="get-started-with-ink-in-wpf"></a>Wprowadzenie do pisma odręcznego w WPF

Windows Presentation Foundation (WPF) zawiera funkcję atramentu, która ułatwia włączenie cyfrowego atramentu do aplikacji.

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z poniższych przykładów, należy najpierw zainstalować [program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Pomaga również dowiedzieć się, jak napisać podstawowe aplikacje WPF. Aby uzyskać pomoc dotyczącą rozpoczynania pracy z programem WPF, zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Szybki start

Ta sekcja ułatwia pisanie prostej aplikacji WPF, która zbiera pismo odręczne.

### <a name="got-ink"></a>Masz atrament?

Aby utworzyć aplikację WPF, która obsługuje pismo odręczne:

1. Otwórz program Visual Studio.

2. Utwórz nową **aplikację WPF**.

   W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowana** > **Wizualizacja C#**  lub **Visual Basic** > kategorii **pulpitu systemu Windows** . Następnie wybierz szablon aplikacji **Aplikacja WPF (.NET Framework)** . Wprowadź nazwę, a następnie wybierz przycisk **OK**.

   Program Visual Studio tworzy projekt, a *MainWindow. XAML* zostanie otwarty w projektancie.

3. Wpisz `<InkCanvas/>` między tagami `<Grid>`.

   ![Projektant XAML z tagiem InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. Naciśnij klawisz **F5** , aby uruchomić aplikację w debugerze.

5. Za pomocą pióra lub myszy Napisz **Hello World** w oknie.

Napisano odpowiednik atramentu aplikacji "Hello World" tylko przez 12 naciśnięć klawiszy.

### <a name="spice-up-your-app"></a>Przyprawa do aplikacji

Skorzystajmy z niektórych funkcji WPF. Zastąp wszystko między tagiem otwierającym i zamykającym \<> tagów z następującą adiustacją:

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

Ten kod XAML tworzy tło pędzla gradientu na powierzchni odręcznej.

![Kolory gradientowe na powierzchni odręcznej w aplikacji WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Dodaj kod za kodem XAML

Chociaż XAML ułatwia projektowanie interfejsu użytkownika, dowolna aplikacja rzeczywista musi dodać kod do obsługi zdarzeń. Oto prosty przykład, który powiększa się w odniesieniu do atramentu w odpowiedzi na kliknięcie prawym przyciskiem myszy.

1. Ustaw procedurę obsługi `MouseRightButtonUp` w kodzie XAML:

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. W **Eksplorator rozwiązań**rozwiń węzeł MainWindow. XAML i Otwórz plik związany z kodem (MainWindow.XAML.cs lub MainWindow. XAML. vb). Dodaj następujący kod procedury obsługi zdarzeń:

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Uruchom aplikację. Dodaj pismo odręczne, a następnie kliknij prawym przyciskiem myszy myszą lub naciśnij odpowiednik pióra.

   Widok zostanie powiększony za każdym razem, gdy klikniesz prawym przyciskiem myszy.

### <a name="use-procedural-code-instead-of-xaml"></a>Użyj kodu proceduralnego zamiast języka XAML

Dostęp do wszystkich funkcji WPF można uzyskać z kodu proceduralnego. Wykonaj następujące kroki, aby utworzyć aplikację "Hello Ink World" dla platformy WPF, która nie korzysta ze wszystkich języków XAML.

1. Utwórz nowy projekt aplikacji konsolowej w programie Visual Studio.

   W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowana** > **Wizualizacja C#**  lub **Visual Basic** > kategorii **pulpitu systemu Windows** . Następnie wybierz szablon aplikacji **Aplikacja konsolowa (.NET Framework)** . Wprowadź nazwę, a następnie wybierz przycisk **OK**.

1. Wklej następujący kod do pliku Program.cs lub program. vb:

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Dodaj odwołania do zestawów 'Presentationcore, platformie docelowej i 'Windowsbase, klikając prawym przyciskiem myszy pozycję **odwołania** w **Eksplorator rozwiązań** i wybierając pozycję **Dodaj odwołanie**.

   ![Menedżer odwołań przedstawiający 'Presentationcore i platformie docelowej](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. Skompiluj aplikację, naciskając klawisz **F5**.

## <a name="see-also"></a>Zobacz także

- [Cyfrowy atrament](digital-ink.md)
- [Zbieranie atramentu](collecting-ink.md)
- [Rozpoznawanie pisma odręcznego](handwriting-recognition.md)
- [Przechowywanie pisma odręcznego](storing-ink.md)
