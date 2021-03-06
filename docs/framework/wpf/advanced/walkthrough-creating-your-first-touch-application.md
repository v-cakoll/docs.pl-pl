---
title: 'Przewodnik: tworzenie pierwszej aplikacji dotykowej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: a915b8e238550eb3d9c1bcbe72d0d05a83a8312c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605807"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>Przewodnik: tworzenie pierwszej aplikacji dotykowej
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia aplikacjom odpowiadanie na touch. Na przykład możesz wchodzić w interakcje z aplikacją przy użyciu jednej lub więcej palców urządzenia dotykowe, takiego jak ekranu dotykowego, w tym przewodniku tworzy aplikację, która umożliwia użytkownikowi przenoszenie, zmienianie rozmiaru lub Obracanie pojedynczego obiektu za pomocą dotyku.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
- Program Visual Studio.  
  
- Urządzenie, które akceptuje dotykowym, takich jak ekranu dotykowego, który obsługuje Windows Touch.  
  
 Ponadto powinien mieć podstawową wiedzę na temat sposobu tworzenia aplikacji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zwłaszcza jak subskrybować i obsługiwać zdarzenia. Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="creating-the-application"></a>Tworzenie aplikacji  
  
#### <a name="to-create-the-application"></a>Aby utworzyć aplikację  
  
1. Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `BasicManipulation`. Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
2. Zastąp zawartość pliku MainWindow.xaml następujące XAML.  
  
     Ten kod znaczników tworzy prostą aplikację, która zawiera czerwonego <xref:System.Windows.Shapes.Rectangle> na <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.UIElement.IsManipulationEnabled%2A> Właściwość <xref:System.Windows.Shapes.Rectangle> jest ustawiona na wartość true, dzięki czemu będzie ona otrzymywać do manipulowania zdarzenia. Aplikacja subskrybuje <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, i <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzenia. Te zdarzenia zawiera logikę do przenoszenia <xref:System.Windows.Shapes.Rectangle> po użytkownik modyfikuje je.  
  
     [!code-xaml[BasicManipulation#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3. Jeśli używasz języka Visual Basic w pierwszym wierszu pliku MainWindow.xaml, Zastąp `x:Class="BasicManipulation.MainWindow"` z `x:Class="MainWindow"`.  
  
4. W `MainWindow` klasy, Dodaj następujący kod <xref:System.Windows.UIElement.ManipulationStarting> programu obsługi zdarzeń.  
  
     <xref:System.Windows.UIElement.ManipulationStarting> Wystąpi zdarzenie po [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykryje, że touch danych wejściowych, który rozpoczyna się do manipulowania obiektu. Kod określa, że pozycja operowanie atrybutami powinny być względem <xref:System.Windows.Window> , ustawiając <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> właściwości.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]

5. W `MainWindow` klasy, Dodaj następujący kod <xref:System.Windows.Input.ManipulationDelta> programu obsługi zdarzeń.

     <xref:System.Windows.Input.ManipulationDelta> Zdarzenie występuje, gdy odrywania danych wejściowych zmienia pozycję i może wystąpić wiele razy podczas manipulowania. Zdarzenia może również wystąpić po palcem jest wywoływane. Na przykład, jeśli użytkownik przeciąga palcem na ekranie <xref:System.Windows.Input.ManipulationDelta> zdarzeń powtarza się wielokrotnie jako przenosi finger. Gdy użytkownik zgłasza palcem na ekranie <xref:System.Windows.Input.ManipulationDelta> zdarzeń będzie się powtarzał do symulacji bezwładności.

     Stosuje się kod <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> do <xref:System.Windows.UIElement.RenderTransform%2A> z <xref:System.Windows.Shapes.Rectangle> przenieść je, gdy użytkownik przesuwa odrywania danych wejściowych. Sprawdza również czy <xref:System.Windows.Shapes.Rectangle> znajduje się poza granicami <xref:System.Windows.Window> podczas bezwładności, gdy wystąpi zdarzenie. Jeśli tak, aplikacja wywołuje <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> metodę, aby zakończyć operowanie atrybutami.

     [!code-csharp[BasicManipulation#ManipulationDelta](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]

6. W `MainWindow` klasy, Dodaj następujący kod <xref:System.Windows.UIElement.ManipulationInertiaStarting> programu obsługi zdarzeń.

     <xref:System.Windows.UIElement.ManipulationInertiaStarting> Zdarzenie występuje, gdy użytkownik zgłasza wszystkich palców od ekranu. Kod ustawia prędkości początkowej oraz prędkości dla przepływu, rozszerzenia i obracania prostokąta.

     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]

7. Skompiluj i uruchom projekt.

     Powinien zostać wyświetlony czerwony kwadrat są wyświetlane w oknie.

## <a name="testing-the-application"></a>Testowanie aplikacji
 Aby przetestować aplikację, wypróbuj następujące operacje. Należy pamiętać, że można zrobić więcej niż jedną z następujących czynności w tym samym czasie.

- Aby przenieść <xref:System.Windows.Shapes.Rectangle>, umieść palcem w <xref:System.Windows.Shapes.Rectangle> i przesuń palcem na ekranie.

- Aby zmienić rozmiar <xref:System.Windows.Shapes.Rectangle>, umieść dwóch palców w <xref:System.Windows.Shapes.Rectangle> i przenieść palców, razem lub oddalone od siebie nawzajem.

- Aby obrócić <xref:System.Windows.Shapes.Rectangle>, umieść dwóch palców w <xref:System.Windows.Shapes.Rectangle> i Obróć palców wokół siebie nawzajem.

 Aby spowodować bezwładności, szybko podnieść palców od ekranu podczas wykonywania poprzednich manipulacji. <xref:System.Windows.Shapes.Rectangle> Będą nadal przenieść, zmienić rozmiar lub Obróć przez kilka sekund, zanim przestanie.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>