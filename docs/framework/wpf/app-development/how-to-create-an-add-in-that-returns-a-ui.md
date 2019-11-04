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
ms.openlocfilehash: d799c91b9abdf7882a0fcd3f0b656eac553b188c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460144"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Jak utworzyć dodatek, który zwraca interfejs użytkownika
Ten przykład pokazuje, jak utworzyć dodatek, który zwraca Windows Presentation Foundation (WPF) do aplikacji autonomicznej WPF hosta.  
  
 Dodatek zwraca interfejs użytkownika, który jest formantem użytkownika WPF. Zawartość kontrolki użytkownika to pojedynczy przycisk, który po kliknięciu wyświetla okno komunikatu. Aplikacja autonomiczna WPF obsługuje dodatek i wyświetla kontrolkę użytkownika (zwracaną przez dodatek) jako zawartość głównego okna aplikacji.  
  
 **Wymagania wstępne**  
  
 W tym przykładzie wyróżniono rozszerzenia WPF do modelu dodatku .NET Framework, który umożliwia ten scenariusz, i przyjmuje następujące elementy:  
  
- Znajomość modelu dodatku .NET Framework, w tym potoku, dodatku i opracowywania hosta. Jeśli nie znasz tych pojęć, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Samouczek przedstawiający implementację potoku, dodatek i aplikację hosta zawiera [Przewodnik: Tworzenie aplikacji rozszerzalnej](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Znajomość rozszerzeń WPF do modelu dodatku .NET Framework, który można znaleźć tutaj: [Omówienie dodatków WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Przykład  
 Aby utworzyć dodatek, który zwraca interfejs użytkownika WPF, wymaga określonego kodu dla każdego segmentu potoku, dodatku i aplikacji hosta.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementowanie segmentu potoku kontraktu  
 Metoda musi być zdefiniowana przez umowę zwracającą interfejs użytkownika, a jej wartość zwracana musi być typu <xref:System.AddIn.Contract.INativeHandleContract>. Jest to zademonstrowane przez metodę `GetAddInUI` kontraktu `IWPFAddInContract` w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementowanie segmentu potoku widoku dodatku  
 Ponieważ dodatek implementuje interfejsów użytkownika, który zapewnia jako podklasy <xref:System.Windows.FrameworkElement>, metoda w widoku dodatku, która jest skorelowane do `IWPFAddInView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok dodatku kontraktu wdrożony jako interfejs.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementowanie segmentu potoku karty dodatku  
 Metoda Contract zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale dodatek zwraca <xref:System.Windows.FrameworkElement> (zgodnie z opisem w widoku dodatku). W związku z tym <xref:System.Windows.FrameworkElement> należy przekonwertować na <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granicy izolacji. Ta operacja jest wykonywana przez adapter dodatku, wywołując <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementowanie segmentu potoku widoku hosta  
 Ponieważ aplikacja hosta będzie wyświetlała <xref:System.Windows.FrameworkElement>, metoda w widoku hosta, która jest skorelowane do `IWPFAddInHostView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok hosta kontraktu wdrożony jako interfejs.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementowanie segmentu potoku karty po stronie hosta  
 Metoda Contract zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale aplikacja hosta oczekuje <xref:System.Windows.FrameworkElement> (określony przez widok hosta). W związku z tym <xref:System.AddIn.Contract.INativeHandleContract> musi być konwertowana na <xref:System.Windows.FrameworkElement> po przekroczeniu granicy izolacji. Ta operacja jest wykonywana przez adapter po stronie hosta przez wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementowanie dodatku  
 Po utworzeniu wbudowanej karty sieciowej i dodatku dodatek (`WPFAddIn1.AddIn`) musi zaimplementować metodę `IWPFAddInView.GetAddInUI` w celu zwrócenia obiektu <xref:System.Windows.FrameworkElement> (w tym przykładzie <xref:System.Windows.Controls.UserControl>). Implementacja <xref:System.Windows.Controls.UserControl>, `AddInUI` jest pokazana przez następujący kod.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Implementacja `IWPFAddInView.GetAddInUI` przez dodatek po prostu musi zwrócić nowe wystąpienie `AddInUI`, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Implementowanie aplikacji hosta  
 Po utworzeniu karty sieciowej i widoku hosta po stronie hosta aplikacja hosta może użyć modelu dodatku .NET Framework, aby otworzyć potok, uzyskać widok hosta dodatku i wywołać metodę `IWPFAddInHostView.GetAddInUI`. Te kroki przedstawiono w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Zobacz także

- [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Dodatki WPF — omówienie](wpf-add-ins-overview.md)
