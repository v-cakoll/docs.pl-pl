---
title: 'Instrukcje: Utwórz dodatek, który zwraca interfejs użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: 1886703e089ed538f68a7221906d815a8ae72076
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182671"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Instrukcje: Utwórz dodatek, który zwraca interfejs użytkownika
Ten przykład pokazuje, jak utworzyć dodatek, który zwraca Windows Presentation Foundation (WPF) do aplikacji autonomicznej WPF hosta.  
  
 Dodatek zwraca interfejs użytkownika, który jest formantem użytkownika WPF. Zawartość kontrolki użytkownika to pojedynczy przycisk, który po kliknięciu wyświetla okno komunikatu. Aplikacja autonomiczna WPF obsługuje dodatek i wyświetla kontrolkę użytkownika (zwracaną przez dodatek) jako zawartość głównego okna aplikacji.  
  
 **Wymagania wstępne  
  
 W tym przykładzie wyróżniono rozszerzenia WPF do modelu dodatku .NET Framework, który umożliwia ten scenariusz, i przyjmuje następujące elementy:  
  
- Znajomość modelu dodatku .NET Framework, w tym potoku, dodatku i opracowywania hosta. Jeśli nie znasz tych pojęć, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Aby zapoznać się z samouczkiem, który ilustruje implementację potoku, dodatek i aplikację hosta, zobacz [Przewodnik: Tworzenie aplikacji](../../add-ins/walkthrough-create-extensible-app.md)rozszerzalnej.  
  
- Znajomość rozszerzeń WPF do modelu dodatku .NET Framework, który można znaleźć tutaj: [Omówienie dodatków WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Przykład  
 Aby utworzyć dodatek, który zwraca interfejs użytkownika WPF, wymaga określonego kodu dla każdego segmentu potoku, dodatku i aplikacji hosta.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementowanie segmentu potoku kontraktu  
 Metoda musi być zdefiniowana przez umowę zwracającą interfejs użytkownika, a jej zwracana wartość musi być typu <xref:System.AddIn.Contract.INativeHandleContract>. Jest to zademonstrowane przez `GetAddInUI` metodę `IWPFAddInContract` kontraktu w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementowanie segmentu potoku widoku dodatku  
 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] Ponieważ dodatek implementuje interfejs <xref:System.Windows.FrameworkElement>, zapewnia jako podklasy, metoda w widoku dodatku, który jest skorelowany do `IWPFAddInView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok dodatku kontraktu wdrożony jako interfejs.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementowanie segmentu potoku karty dodatku  
 Metoda Contract zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale dodatek <xref:System.Windows.FrameworkElement> zwraca (zgodnie z opisem w widoku dodatku). W związku z tym <xref:System.Windows.FrameworkElement> , należy przekonwertować <xref:System.AddIn.Contract.INativeHandleContract> na wartość przed przekroczeniem granicy izolacji. Ta operacja jest wykonywana przez adapter dodatku, wywołując <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementowanie segmentu potoku widoku hosta  
 Ponieważ aplikacja hosta będzie wyświetlać <xref:System.Windows.FrameworkElement>, metoda w widoku hosta, która jest skorelowana z `IWPFAddInHostView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok hosta kontraktu wdrożony jako interfejs.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementowanie segmentu potoku karty po stronie hosta  
 Metoda Contract zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale aplikacja hosta oczekuje <xref:System.Windows.FrameworkElement> (jak określono w widoku hosta). W <xref:System.AddIn.Contract.INativeHandleContract> związku z tym, należy przekonwertować na wartość <xref:System.Windows.FrameworkElement> po przekroczeniu granicy izolacji. Ta operacja jest wykonywana przez adapter po stronie hosta przez wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementowanie dodatku  
 Po utworzeniu`WPFAddIn1.AddIn`wbudowanej karty sieciowej i dodatku dodatek () musi `IWPFAddInView.GetAddInUI` zaimplementować metodę, aby <xref:System.Windows.Controls.UserControl> zwrócić <xref:System.Windows.FrameworkElement> obiekt (w tym przykładzie). Implementacja elementu <xref:System.Windows.Controls.UserControl>, `AddInUI`jest pokazana przez następujący kod.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Implementacja `IWPFAddInView.GetAddInUI` przez dodatek po prostu musi zwrócić nowe `AddInUI`wystąpienie, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Implementowanie aplikacji hosta  
 Po utworzeniu karty i widoku hosta po stronie hosta aplikacja hosta może użyć modelu dodatku .NET Framework, aby otworzyć potok, uzyskać widok hosta dodatku i wywołać `IWPFAddInHostView.GetAddInUI` metodę. Te kroki przedstawiono w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Zobacz także

- [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Dodatki WPF — omówienie](wpf-add-ins-overview.md)
