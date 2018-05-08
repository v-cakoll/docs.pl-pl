---
title: 'Wskazówki: tworzenie Twojej pierwszej aplikacji dotykowej'
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
ms.openlocfilehash: 94a97c30179f7a8231426e31b8cacc364629ffc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-your-first-touch-application"></a>Wskazówki: tworzenie Twojej pierwszej aplikacji dotykowej
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia aplikacjom uwzględniał touch. Na przykład pozwala na interakcję z aplikacją za pomocą jednego lub więcej palców na urządzeniu dotykowe, takie jak ekran dotykowy tego przewodnika tworzy aplikację, która umożliwia użytkownikowi przenoszenie, zmienianie rozmiaru lub Obracanie pojedynczego obiektu przy użyciu touch.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7.  
  
-   Urządzenie, które akceptuje dotykowym, takie jak ekran dotykowy, który obsługuje Touch z systemem Windows.  
  
 Ponadto powinien mieć podstawową wiedzę na temat sposobu tworzenia aplikacji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], szczególnie jak subskrybować i obsługi zdarzenia. Aby uzyskać więcej informacji, zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="creating-the-application"></a>Tworzenie aplikacji  
  
#### <a name="to-create-the-application"></a>Aby utworzyć aplikację  
  
1.  Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `BasicManipulation`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Zamień zawartość MainWindow.xaml następujące XAML.  
  
     Ten kod znaczników tworzy prostą aplikację, która zawiera czerwony <xref:System.Windows.Shapes.Rectangle> na <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.UIElement.IsManipulationEnabled%2A> Właściwość <xref:System.Windows.Shapes.Rectangle> ma wartość true, dzięki czemu będą otrzymywać zdarzeń manipulowanie. Subskrybuje aplikacji <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, i <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzenia. Zdarzenia te zawierają logiki przenoszenia <xref:System.Windows.Shapes.Rectangle> gdy użytkownik modyfikuje go.  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Jeśli korzystasz z języka Visual Basic w pierwszym wierszu MainWindow.xaml, Zastąp `x:Class="BasicManipulation.MainWindow"` z `x:Class="MainWindow"`.  
  
4.  W `MainWindow` klasy, należy dodać następujące <xref:System.Windows.UIElement.ManipulationStarting> obsługi zdarzeń.  
  
     <xref:System.Windows.UIElement.ManipulationStarting> Zdarzenie po [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykryje, że touch rozpoczyna danych wejściowych do manipulowania obiektu. Kod określa, czy pozycja operowanie powinny być względem <xref:System.Windows.Window> przez ustawienie <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> właściwości.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  W `MainWindow` klasy, należy dodać następujące <xref:System.Windows.Input.ManipulationDelta> obsługi zdarzeń.  
  
     <xref:System.Windows.Input.ManipulationDelta> Zdarzeń występuje po naciśnięciu wejściowy zmienia pozycję i może wystąpić wiele razy podczas manipulowania. Zdarzenie może również wystąpić po palcem jest wywoływane. Na przykład, jeśli użytkownik przeciąga palcem ekranie <xref:System.Windows.Input.ManipulationDelta> zdarzenie wielokrotnie jako przenosi palca. Gdy użytkownik wywołuje palca na ekranie <xref:System.Windows.Input.ManipulationDelta> zdarzeń będzie się powtarzał do symulowania bezwładności.  
  
     Kod ma zastosowanie <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> do <xref:System.Windows.UIElement.RenderTransform%2A> z <xref:System.Windows.Shapes.Rectangle> przenieść go, gdy użytkownik przechodzi przez dotknięcie danych wejściowych. Sprawdza również czy <xref:System.Windows.Shapes.Rectangle> znajduje się poza granicami <xref:System.Windows.Window> po wystąpieniu zdarzenia podczas bezwładności. Jeśli tak, aplikacja wywołuje <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> metodę, aby zakończyć operowanie.  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  W `MainWindow` klasy, należy dodać następujące <xref:System.Windows.UIElement.ManipulationInertiaStarting> obsługi zdarzeń.  
  
     <xref:System.Windows.UIElement.ManipulationInertiaStarting> Zdarzenie wystąpi, gdy użytkownik wywołuje wszystkich palców na ekranie. Kod ustawia prędkość początkowa i prędkości dla ruchu, rozszerzenia i obrotu prostokąta.  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  Tworzenie i uruchamianie projektu.  
  
     Powinny pojawić się czerwonego kwadratu są wyświetlane w oknie.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Aby przetestować aplikację, wypróbuj następujące operacje. Należy pamiętać, że można wykonać więcej niż jedną z nich w tym samym czasie.  
  
-   Aby przenieść <xref:System.Windows.Shapes.Rectangle>, umieść palcem <xref:System.Windows.Shapes.Rectangle> i przesuń palcem po ekranie.  
  
-   Aby zmienić rozmiar <xref:System.Windows.Shapes.Rectangle>, umieść dwoma palcami <xref:System.Windows.Shapes.Rectangle> i Przenieś palcami razem lub je od siebie nawzajem.  
  
-   Obracanie <xref:System.Windows.Shapes.Rectangle>, umieść dwoma palcami <xref:System.Windows.Shapes.Rectangle> i obracania palcami wokół siebie nawzajem.  
  
 Aby spowodować bezwładności, szybko podnieść palcami na ekranie wykonywać operacje poprzedniej. <xref:System.Windows.Shapes.Rectangle> Będzie przenosić, Zmień rozmiar lub obracać przez kilka sekund, zanim przestanie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
