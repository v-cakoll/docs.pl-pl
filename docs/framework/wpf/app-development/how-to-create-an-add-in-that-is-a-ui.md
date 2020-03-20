---
title: Jak utworzyć dodatek, który jest interfejsem użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 339231031b9e57b9f00a2aeb6fbbde8ad66c1ad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141032"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Jak utworzyć dodatek, który jest interfejsem użytkownika
W tym przykładzie pokazano, jak utworzyć dodatek, który jest Windows Presentation Foundation (WPF), który jest obsługiwany przez aplikację autonomiczną WPF.  
  
 Dodatek jest interfejs użytkownika, który jest formantem użytkownika WPF. Zawartość formantu użytkownika jest pojedynczym przyciskiem, który po kliknięciu wyświetla okno komunikatu. Aplikacja autonomiczna WPF hostuje interfejs użytkownika dodatku jako zawartość głównego okna aplikacji.  
  
 **Wymagania wstępne**  
  
 W tym przykładzie wyróżniono rozszerzenia WPF do modelu dodatku .NET Framework, który włącza ten scenariusz i zakłada, że:  
  
- Znajomość modelu dodatku .NET Framework, w tym potoku, dodatku i rozwoju hosta. Jeśli nie znasz tych pojęć, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Aby zapoznać się z samouczkiem przedstawiającym implementację potoku, dodatku i aplikacji hosta, zobacz [Przewodnik: Tworzenie aplikacji rozszerzalnej](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Znajomość rozszerzeń WPF do modelu dodatku .NET Framework. Zobacz [Przegląd dodatków WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Przykład  
 Aby utworzyć dodatek, który jest interfejs użytkownika WPF wymaga określonego kodu dla każdego segmentu potoku, dodatek i aplikacji hosta.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Wdrażanie segmentu rurociągu kontraktowego

Gdy dodatek jest interfejsem użytkownika, kontrakt dla dodatku <xref:System.AddIn.Contract.INativeHandleContract>musi implementować . W przykładzie `IWPFAddInContract` implementuje <xref:System.AddIn.Contract.INativeHandleContract>, jak pokazano w poniższym kodzie.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementowanie segmentu potoku widoku dodatku

Ponieważ dodatek jest implementowany jako podklasa <xref:System.Windows.FrameworkElement> typu, widok dodatku musi <xref:System.Windows.FrameworkElement>również podklasa . Poniższy kod przedstawia add-in widzenia umowy, `WPFAddInView` zaimplementowane jako klasy.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
W tym miejscu widok dodatku <xref:System.Windows.Controls.UserControl>pochodzi od . W związku z tym interfejs użytkownika dodatku <xref:System.Windows.Controls.UserControl>powinien również pochodzić z .  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementowanie segmentu potoku adaptera dodatku

Podczas gdy kontrakt <xref:System.AddIn.Contract.INativeHandleContract>jest , dodatek <xref:System.Windows.FrameworkElement> jest (określony przez segment potoku widoku dodatku). W związku <xref:System.Windows.FrameworkElement> z tym musi <xref:System.AddIn.Contract.INativeHandleContract> być przekształcony w przed przekroczeniem granicy izolacji. Ta praca jest wykonywana przez kartę dodatku <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>przez wywołanie, jak pokazano w poniższym kodzie.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

W modelu dodatku, w którym dodatek zwraca interfejs użytkownika (zobacz [Tworzenie dodatku, który zwraca interfejs użytkownika),](how-to-create-an-add-in-that-returns-a-ui.md)karta dodatku <xref:System.Windows.FrameworkElement> przekonwertowana na wywołanie <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>musi być również wywoływana w tym modelu, chociaż należy zaimplementować metodę, z której można napisać kod, aby go wywołać. Można to zrobić, <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> zastępując i implementując <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> kod, który wywołuje, jeśli kod, który wywołuje <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> oczekuje <xref:System.AddIn.Contract.INativeHandleContract>. W takim przypadku wywołujący będzie karta po stronie hosta, która jest omówiona w kolejnej podsekcji.  
  
> [!NOTE]
> Należy również zastąpić <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> w tym modelu, aby włączyć tabulacji między interfejsu użytkownika aplikacji hosta i dodatku interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz "Ograniczenia dodatku WPF" w [przeglądzie dodatków WPF](wpf-add-ins-overview.md).  
  
Ponieważ karta dodatkowa implementuje interfejs, który pochodzi <xref:System.AddIn.Contract.INativeHandleContract>od , należy <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>również zaimplementować <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> , chociaż jest to ignorowane, gdy jest zastępowany.  
  
<a name="HostViewPipeline"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementowanie segmentu potoku widoku hosta

W tym modelu aplikacja hosta zazwyczaj oczekuje widoku <xref:System.Windows.FrameworkElement> hosta do podklasy. Karta po stronie hosta <xref:System.AddIn.Contract.INativeHandleContract> musi <xref:System.Windows.FrameworkElement> przekonwertować na a po <xref:System.AddIn.Contract.INativeHandleContract> przekroczeniu granicy izolacji. Ponieważ metoda nie jest wywoływana przez aplikację <xref:System.Windows.FrameworkElement>hosta, aby uzyskać, <xref:System.Windows.FrameworkElement> widok hosta musi "zwrócić" przez zawierające go. W związku z tym widok hosta musi <xref:System.Windows.FrameworkElement> pochodzić z podklasy, która może zawierać inne interfejsy użytkownika, takie jak <xref:System.Windows.Controls.UserControl>. Poniższy kod pokazuje widok hosta umowy, `WPFAddInHostView` zaimplementowane jako klasa.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementowanie segmentu potoku karty po stronie hosta

Podczas gdy umowa <xref:System.AddIn.Contract.INativeHandleContract>jest , aplikacja <xref:System.Windows.Controls.UserControl> hosta oczekuje (zgodnie z określonymi przez widok hosta). W związku <xref:System.AddIn.Contract.INativeHandleContract> z tym musi <xref:System.Windows.FrameworkElement> być przekonwertowany na po przekroczeniu granicy izolacji, <xref:System.Windows.Controls.UserControl>przed ustawieniem jako zawartość widoku hosta (który pochodzi od ).  
  
Ta praca jest wykonywana przez kartę po stronie hosta, jak pokazano w poniższym kodzie.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Jak widać, karta po stronie hosta <xref:System.AddIn.Contract.INativeHandleContract> uzyskuje, wywołując <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> metodę karty dodatku (jest to punkt, w którym <xref:System.AddIn.Contract.INativeHandleContract> przekracza granicę izolacji).  
  
Następnie karta po stronie hosta konwertuje na <xref:System.AddIn.Contract.INativeHandleContract> a, <xref:System.Windows.FrameworkElement> wywołując . <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> Na koniec <xref:System.Windows.FrameworkElement> jest ustawiona jako zawartość widoku hosta.  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Implementowanie dodatku

W miejscu karty dodatku i widoku dodatku dodatek można zaimplementować, wywodząc się z widoku dodatku, jak pokazano w poniższym kodzie.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

W tym przykładzie można zobaczyć jedną interesującą zaletę tego modelu: deweloperzy dodatków wystarczy zaimplementować dodatek (ponieważ jest to również interfejs użytkownika), a nie zarówno klasy dodatku i dodatku interfejsu użytkownika.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implementowanie aplikacji hosta

Po utworzeniu karty po stronie hosta i widoku hosta aplikacja hosta może użyć modelu dodatku .NET Framework, aby otworzyć potok i uzyskać widok hosta dodatku. Te kroki są pokazane w poniższym kodzie.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

Aplikacja hosta używa typowego kodu modelu dodatku .NET Framework, aby uaktywnić dodatek, który niejawnie zwraca widok hosta do aplikacji hosta. Następnie aplikacja hosta wyświetla widok hosta <xref:System.Windows.Controls.UserControl>(który <xref:System.Windows.Controls.Grid>jest a) z pliku .  
  
 Kod do przetwarzania interakcji z interfejsem użytkownika dodatku jest uruchamiany w domenie aplikacji dodatku. Interakcje te obejmują następujące czynności:  
  
- <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obsługa zdarzenia.  
  
- Wyświetlanie <xref:System.Windows.MessageBox>pliku .  
  
 To działanie jest całkowicie odizolowane od aplikacji hosta.  
  
## <a name="see-also"></a>Zobacz też

- [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Dodatki WPF — omówienie](wpf-add-ins-overview.md)
