---
title: Jak utworzyć dodatek, który zwraca interfejs użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: 24b30d61553796840a44a869eacb33232a0b78d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Jak utworzyć dodatek, który zwraca interfejs użytkownika
W tym przykładzie przedstawiono sposób tworzenia dodatek zwraca Windows Presentation Foundation (WPF) na host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja autonomiczna.  
  
 Dodatek zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czyli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kontrolki użytkownika. Zawartość kontrolki użytkownika jest pojedynczy przycisku, po kliknięciu wyświetla okno komunikatu. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Aplikacja autonomiczna obsługuje dodatek i wyświetla kontrolki użytkownika (zwracanym przez dodatek) jako zawartość okna głównego aplikacji.  
  
 **Wymagania wstępne**  
  
 W tym przykładzie wyróżniono [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerzeń [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, Włącz w tym scenariuszu, która przyjmuje następujące:  
  
-   Znajomość [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku modelu, w tym potoku dodatku i rozwoju hosta. Jeśli znasz tych pojęć, zobacz [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md). Samouczek przedstawiający implementacji potoku, dodatek i aplikacji hosta, zobacz [wskazówki: tworzenie aplikacji rozszerzalnej](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).  
  
-   Znajomość [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerzenia do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, który można znaleźć tutaj: [omówienie Add-Ins WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## <a name="example"></a>Przykład  
 Aby utworzyć dodatku, który zwraca [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wymaga określonego kodu dla każdego segmentu potoku dodatku i aplikacji hosta.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementowanie kontraktu segmentów potoku  
 Metoda musi być zdefiniowany przez kontraktu dla zwracania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], a jego wartości zwracanej musi być typu <xref:System.AddIn.Contract.INativeHandleContract>. Wskazuje na `GetAddInUI` metody `IWPFAddInContract` kontraktu w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementowanie segmentów potoku dodatku widoku  
 Ponieważ dodatek implementuje [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] zapewnia jako podklasy <xref:System.Windows.FrameworkElement>, metoda odpowiadająca widoku Dodaj `IWPFAddInView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok dodatku kontraktu implementowany jako interfejs.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementowanie segmentów potoku Dodaj strony karty  
 Zwraca metodę kontraktu <xref:System.AddIn.Contract.INativeHandleContract>, ale dodatek zwraca <xref:System.Windows.FrameworkElement> (jak określono w widoku dodatku). W rezultacie <xref:System.Windows.FrameworkElement> muszą zostać skonwertowane do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji. To zadanie jest wykonywane przez karty Dodaj w stronie przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementowanie segmentów potoku widoku hosta  
 Ponieważ aplikacja hosta będzie wyświetlana <xref:System.Windows.FrameworkElement>, metoda w widoku hosta, które są powiązane z `IWPFAddInHostView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok hosta kontraktu implementowany jako interfejs.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementowanie segmentów potoku karty po stronie hosta  
 Zwraca metodę kontraktu <xref:System.AddIn.Contract.INativeHandleContract>, ale oczekuje aplikacji hosta <xref:System.Windows.FrameworkElement> (jak określono w widoku hosta). W rezultacie <xref:System.AddIn.Contract.INativeHandleContract> muszą zostać skonwertowane do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji. To zadanie jest wykonywane przez adaptery po stronie hosta przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementowanie dodatku  
 Dodaj w stronie karty i dodatku Widok utworzony, dodatek (`WPFAddIn1.AddIn`) musi implementować `IWPFAddInView.GetAddInUI` metodę, aby zwrócić <xref:System.Windows.FrameworkElement> obiektu ( <xref:System.Windows.Controls.UserControl> w tym przykładzie). Implementacja <xref:System.Windows.Controls.UserControl>, `AddInUI`, przedstawiono w następującym kodem.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Implementacja `IWPFAddInView.GetAddInUI` przez dodatek musi zwrócić nowe wystąpienie klasy `AddInUI`, jak pokazano w następującym kodem.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Wdrażanie aplikacji hosta  
 Adaptery po stronie hosta i widoku hosta utworzony, można użyć aplikacji hosta [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, aby otworzyć potoku, uzyskać widoku hosta dodatku, i wywołanie `IWPFAddInHostView.GetAddInUI` metody. Te kroki przedstawiono w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md)  
 [Dodatki WPF — omówienie](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
