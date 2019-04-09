---
title: 'Instrukcje: Tworzenie dodatku, który zwraca interfejs użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: faed11bb02037ea42b31402d431e1bcdd8b70339
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115755"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Instrukcje: Tworzenie dodatku, który zwraca interfejs użytkownika
Ten przykład przedstawia sposób tworzenia dodatku, zwracające Windows Presentation Foundation (WPF) do hosta WPF autonomiczną aplikacją.  
  
 Dodatek zwraca interfejs użytkownika, który jest formanty użytkownika WPF. Zawartość kontrolki użytkownika nie ma jednego przycisku, po kliknięciu wyświetla okno komunikatu. Oddzielną aplikację WPF obsługuje dodatku i wyświetla kontrolkę użytkownika (zwrócone przez dodatek) jako zawartość okna głównego aplikacji.  
  
 **Wymagania wstępne**  
  
 W tym przykładzie wyróżnia rozszerzenia WPF model dodatku .NET Framework, które umożliwiają w tym scenariuszu i przyjęto założenie, że:  
  
-   Znajomość środowiska .NET Framework — w modelu, w tym potoku dodatku i rozwoju hosta. Jeśli nie jesteś zaznajomiony z tych pojęć, zobacz [dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Aby uzyskać samouczek, który przedstawia implementację potoku dodatku i aplikacji hosta, zobacz [instruktażu: Tworzenie aplikacji rozszerzalnej](../../add-ins/walkthrough-create-extensible-app.md).  
  
-   Wiedzę na temat rozszerzeń WPF, .NET Framework — w modelu, który można znaleźć tutaj: [Przegląd dodatki WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Przykład  
 Aby utworzyć dodatek, który zwraca interfejs użytkownika WPF wymaga określonego kodu dla każdy z segmentów potoku dodatku i aplikacji hosta.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementowanie segmentów potoku kontraktu  
 Metoda musi być określona przez umowę do zwracania interfejsu użytkownika, a jego wartość zwracana musi być typu <xref:System.AddIn.Contract.INativeHandleContract>. Wskazuje na `GetAddInUI` metody `IWPFAddInContract` Umowę w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementowanie segmentów potoku dodatku widoku  
 Ponieważ dodatek implementuje [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] zapewnia jako podklasy <xref:System.Windows.FrameworkElement>, metody, w widoku dodatku, odpowiadająca `IWPFAddInView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok dodatku kontrakt implementowany jako interfejs.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementowanie segmentów potoku dodać strony karty  
 Metoda kontraktu zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale dodatek zwraca <xref:System.Windows.FrameworkElement> (jak określono w widoku dodatku). W związku z tym <xref:System.Windows.FrameworkElement> muszą zostać skonwertowane do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji. Ta praca jest wykonywana przez siebie w Dodaj kartę przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementowanie segmentów potoku widok hosta  
 Ponieważ aplikacja hosta będzie wyświetlana <xref:System.Windows.FrameworkElement>, metody, w widoku hosta, które skorelowany `IWPFAddInHostView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok hosta umowy implementowany jako interfejs.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementowanie segmentów potoku adaptery po stronie hosta  
 Metoda kontraktu zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale oczekuje, że aplikacja hosta <xref:System.Windows.FrameworkElement> (jak określono w widoku hosta). W związku z tym <xref:System.AddIn.Contract.INativeHandleContract> muszą zostać skonwertowane do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji. Ta praca jest wykonywana przez adapter po stronie hosta, wywołując <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Wdrażanie dodatku programu  
 Za pomocą karty add w side i widoku dodatku utworzeniu dodatku (`WPFAddIn1.AddIn`) musi implementować `IWPFAddInView.GetAddInUI` metodę, aby zwrócić <xref:System.Windows.FrameworkElement> obiektu ( <xref:System.Windows.Controls.UserControl> w tym przykładzie). Implementacja <xref:System.Windows.Controls.UserControl>, `AddInUI`, jest wyświetlany przez następujący kod.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Implementacja `IWPFAddInView.GetAddInUI` przez dodatek po prostu musi zwrócić nowe wystąpienie klasy `AddInUI`, jak pokazano w następującym kodem.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Wdrażanie aplikacji hosta  
 Adaptery po stronie hosta i widok hosta utworzony, aplikacji hosta umożliwia model dodatku .NET Framework Otwórz potok, uzyskać widok hosta dodatków i wywołania `IWPFAddInHostView.GetAddInUI` metody. Te kroki są wyświetlane w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Zobacz także

- [Dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Przegląd Dodatki WPF](wpf-add-ins-overview.md)
