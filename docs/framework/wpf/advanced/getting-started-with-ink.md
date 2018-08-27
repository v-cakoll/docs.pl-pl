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
ms.openlocfilehash: 600d8528125606c6e1af5b031e2fc31aabb79206
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925047"
---
# <a name="get-started-with-ink-in-wpf"></a>Rozpoczynanie pracy z usługą pisma odręcznego na platformie WPF

Windows Presentation Foundation (WPF) zawiera funkcję pisma odręcznego, ułatwiająca włączenie cyfrowy atrament w swojej aplikacji.

## <a name="prerequisites"></a>Wymagania wstępne

Można użyć poniższych przykładów, najpierw [zainstalować program Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Pomaga również wiedzieć, jak napisać podstawowych aplikacji WPF. Aby uzyskać pomoc, wprowadzenie do WPF, zobacz [Instruktaż: Mój pierwszy aplikacji klasycznej WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Przewodnik Szybki Start

Ta sekcja ułatwia pisanie prostą aplikację WPF, która gromadzi pisma odręcznego.

### <a name="got-ink"></a>Masz pisma odręcznego?

Aby utworzyć aplikację WPF, która obsługuje pisma odręcznego:

1. Otwórz program Visual Studio.

2. Utwórz nową **aplikacja WPF**.

   W **nowy projekt** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** lub **języka Visual Basic**  >   **Windows Desktop** kategorii. Następnie wybierz **aplikacja WPF (.NET Framework)** szablonu aplikacji. Wprowadź nazwę, a następnie wybierz **OK**.

   Program Visual Studio tworzy projekt, a *MainWindow.xaml* zostanie otwarty w projektancie.

3. Typ `<InkCanvas/>` między `<Grid>` tagów.

   ![Projektant XAML z tagiem InkCanvas](media/getting-started-with-ink/inkcanvas-xaml.png)

4. Naciśnij klawisz **F5** do uruchomienia aplikacji w debugerze.

5. Za pomocą pióra lub mysz, zapis **Witaj, świecie** w oknie.

Napisanych pisma odręcznego wielokrotność aplikację "hello world" przy użyciu tylko 12 naciśnięć klawiszy!

### <a name="spice-up-your-app"></a>Popraw aplikacji w górę

Przyjrzyjmy się korzystać z niektórych funkcji WPF. Zastąp wszystkie między otwierającym i zamykającym \<okna > Znaczniki następującym kodem:

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

Ta XAML tworzy pędzla gradientu tła powierzchni pisma odręcznego.

![Gradient kolorów na pisma odręcznego narażonego na ataki w aplikacji WPF](media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Dodawanie kodu za XAML

Gdy XAML sprawia, że można łatwo projektować interfejs użytkownika, dowolnej aplikacji w rzeczywistych warunkach musi dodać kod do obsługi zdarzeń. Poniżej przedstawiono prosty przykład, który powiększa pisma odręcznego w odpowiedzi kliknij prawym przyciskiem myszy z myszy.

1. Ustaw `MouseRightButtonUp` obsługi w swojej XAML:

   [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. W **Eksploratora rozwiązań**, rozwiń węzeł MainWindow.xaml i Otwórz plik związany z kodem (MainWindow.xaml.cs lub MainWindow.xaml.vb). Dodaj następujący kod procedury obsługi zdarzeń:

   [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Uruchom aplikację. Dodaj część pisma odręcznego, a następnie kliknij prawym przyciskiem myszy, za pomocą myszy lub wykonać odpowiednik naciśnięcie i przytrzymanie za pomocą pióra.

   Wyświetlanie powiększa za każdym razem, który kliknięto prawym przyciskiem myszy.

### <a name="use-procedural-code-instead-of-xaml"></a>Zamiast kod proceduralny XAML

Można uzyskać dostęp do wszystkich funkcji środowiska WPF z kodu proceduralnego. Wykonaj następujące kroki, aby utworzyć aplikację "Hello pisma odręcznego World" dla WPF, który nie używa żadnych XAML w ogóle.

1. Utwórz nowy projekt aplikacji konsoli w programie Visual Studio.

   W **nowy projekt** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** lub **języka Visual Basic**  >   **Windows Desktop** kategorii. Następnie wybierz **Aplikacja konsoli (.NET Framework)** szablonu aplikacji. Wprowadź nazwę, a następnie wybierz **OK**.

1. Wklej następujący kod do pliku Program.cs lub Program.vb:

   [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Dodaj odwołania do zestawów PresentationCore PresentationFramework i WindowsBase, klikając prawym przyciskiem myszy **odwołania** w **Eksploratora rozwiązań** i wybierając pozycję **Dodaj odwołanie**.

   ![Menadżer odwołań PresentationCore i PresentationFramework](media/getting-started-with-ink/references.png)

1. Kompiluj aplikację, naciskając klawisz **F5**.

## <a name="see-also"></a>Zobacz też

- [Cyfrowy atrament](../../../../docs/framework/wpf/advanced/digital-ink.md)
- [Zbieranie atramentu](../../../../docs/framework/wpf/advanced/collecting-ink.md)
- [Rozpoznawanie pisma odręcznego](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)
- [Przechowywanie pisma odręcznego](../../../../docs/framework/wpf/advanced/storing-ink.md)
