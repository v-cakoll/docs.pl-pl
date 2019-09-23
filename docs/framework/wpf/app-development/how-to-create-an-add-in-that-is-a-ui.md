---
title: 'Instrukcje: Utwórz dodatek, który jest interfejsem użytkownika'
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
ms.openlocfilehash: b0e847061a30e93d36997ab603c52715e2730765
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182642"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Instrukcje: Utwórz dodatek, który jest interfejsem użytkownika
Ten przykład pokazuje, jak utworzyć dodatek, który jest Windows Presentation Foundation (WPF), który jest obsługiwany przez aplikację autonomiczną WPF.  
  
 Dodatek to interfejs użytkownika, który jest formantem użytkownika WPF. Zawartość kontrolki użytkownika to pojedynczy przycisk, który po kliknięciu wyświetla okno komunikatu. Aplikacja autonomiczna WPF obsługuje interfejs użytkownika dodatku jako zawartość głównego okna aplikacji.  
  
 **Wymagania wstępne  
  
 W tym przykładzie wyróżniono rozszerzenia WPF do modelu dodatku .NET Framework, który umożliwia ten scenariusz, i przyjmuje następujące elementy:  
  
- Znajomość modelu dodatku .NET Framework, w tym potoku, dodatku i opracowywania hosta. Jeśli nie znasz tych pojęć, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Aby zapoznać się z samouczkiem, który ilustruje implementację potoku, dodatek i aplikację hosta, zobacz [Przewodnik: Tworzenie aplikacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))rozszerzalnej.  
  
- Znajomość rozszerzeń WPF do modelu dodatku .NET Framework. Zobacz [Omówienie dodatków WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Przykład  
 Aby utworzyć dodatek, który jest interfejsem użytkownika WPF, wymaga określonego kodu dla każdego segmentu potoku, dodatku i aplikacji hosta.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementowanie segmentu potoku kontraktu

Gdy dodatek jest interfejsem użytkownika, kontrakt dla dodatku musi być zaimplementowany <xref:System.AddIn.Contract.INativeHandleContract>. W przykładzie `IWPFAddInContract` implementuje <xref:System.AddIn.Contract.INativeHandleContract>, jak pokazano w poniższym kodzie.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementowanie segmentu potoku widoku dodatku

Ponieważ dodatek jest zaimplementowany jako podklasa <xref:System.Windows.FrameworkElement> typu, widok dodatku musi być również podklasą. <xref:System.Windows.FrameworkElement> Poniższy kod przedstawia widok dodatku kontraktu wdrożony jako `WPFAddInView` Klasa.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
W tym miejscu widok dodatku pochodzi od <xref:System.Windows.Controls.UserControl>. W związku z tym interfejs użytkownika dodatku powinien również pochodzić od <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementowanie segmentu potoku karty dodatku

Gdy kontrakt to <xref:System.AddIn.Contract.INativeHandleContract>, dodatek <xref:System.Windows.FrameworkElement> to (zgodnie z definicją segmentu potoku widoku). W związku z <xref:System.Windows.FrameworkElement> tym, należy przekonwertować <xref:System.AddIn.Contract.INativeHandleContract> na wartość przed przekroczeniem granicy izolacji. Ta operacja jest wykonywana przez adapter dodatku, wywołując <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

W modelu dodatku, w którym dodatek zwraca interfejs użytkownika (zobacz [Tworzenie dodatku, który zwraca interfejs użytkownika](how-to-create-an-add-in-that-returns-a-ui.md)), adapter dodatku został przekonwertowany <xref:System.Windows.FrameworkElement> na obiekt <xref:System.AddIn.Contract.INativeHandleContract> przez wywoływanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>musi być również wywoływana w tym modelu, chociaż należy zaimplementować metodę, z której należy napisać kod w celu wywołania go. Można to zrobić, zastępując <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> i implementując kod, który wywołuje <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> , gdy wywoływany <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> kod oczekuje na <xref:System.AddIn.Contract.INativeHandleContract>. W takim przypadku obiekt wywołujący będzie adapterem po stronie hosta, który jest pokryty w kolejnej podsekcji.  
  
> [!NOTE]
> Należy również przesłonić <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> ten model, aby włączyć funkcję tabulacji między interfejsem użytkownika aplikacji hosta i interfejsem użytkownika dodatku. Aby uzyskać więcej informacji, zobacz "ograniczenia dodatku WPF" w temacie [Omówienie dodatków WPF](wpf-add-ins-overview.md).  
  
Ponieważ karta dodatku implementuje interfejs, który pochodzi z <xref:System.AddIn.Contract.INativeHandleContract>, należy również zaimplementować <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, chociaż jest on ignorowany, gdy <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> jest zastępowany.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementowanie segmentu potoku widoku hosta

W tym modelu aplikacja hosta zwykle oczekuje, że widok hosta będzie <xref:System.Windows.FrameworkElement> podklasą. Karta po stronie hosta musi <xref:System.AddIn.Contract.INativeHandleContract> zostać przeprowadzona konwersja do a <xref:System.Windows.FrameworkElement> po <xref:System.AddIn.Contract.INativeHandleContract> przekroczeniu granicy izolacji. Ponieważ metoda nie jest wywoływana przez aplikację hosta w celu uzyskania <xref:System.Windows.FrameworkElement>, widok hosta musi "zwrócić <xref:System.Windows.FrameworkElement> ", zawierający go. W związku z tym widok hosta musi pochodzić od podklasy <xref:System.Windows.FrameworkElement> , która może zawierać inne interfejsów użytkownika, na przykład. <xref:System.Windows.Controls.UserControl> Poniższy kod przedstawia widok hosta kontraktu wdrożony jako `WPFAddInHostView` Klasa.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementowanie segmentu potoku karty po stronie hosta

Gdy kontrakt jest <xref:System.AddIn.Contract.INativeHandleContract>aplikacją, aplikacja hosta oczekuje <xref:System.Windows.Controls.UserControl> (jak określono w widoku hosta). W <xref:System.AddIn.Contract.INativeHandleContract> związku z tym, należy przekonwertować <xref:System.Windows.FrameworkElement> na wartość po przekroczeniu granicy izolacji przed ustawieniem jako zawartość widoku hosta (który pochodzi z <xref:System.Windows.Controls.UserControl>).  
  
Ta operacja jest wykonywana przez kartę po stronie hosta, jak pokazano w poniższym kodzie.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Jak widać, adapter po stronie hosta uzyskuje <xref:System.AddIn.Contract.INativeHandleContract> przez wywołanie <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> metody karty dodatku ( <xref:System.AddIn.Contract.INativeHandleContract> jest to punkt, w którym przecina granicę izolacji).  
  
Następnie karta po stronie hosta konwertuje <xref:System.AddIn.Contract.INativeHandleContract> do a <xref:System.Windows.FrameworkElement> przez wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Na <xref:System.Windows.FrameworkElement> koniec jest ustawiony jako zawartość widoku hosta.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementowanie dodatku

Po zastosowaniu dostosowanej karty i widoku dodatku można zaimplementować ten dodatek, pobierając go z widoku dodatku, jak pokazano w poniższym kodzie.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

Z tego przykładu można zobaczyć jedną ciekawą korzyść tego modelu: deweloperzy dodatków muszą tylko zaimplementować dodatek (ponieważ jest również interfejsem użytkownika), a nie zarówno klasę dodatku, jak i interfejs użytkownika dodatku.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implementowanie aplikacji hosta

Po utworzeniu karty sieciowej i widoku hosta po stronie hosta aplikacja hosta może użyć modelu dodatku .NET Framework, aby otworzyć potok i uzyskać widok hosta dodatku. Te kroki przedstawiono w poniższym kodzie.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

Aplikacja hosta używa typowego kodu modelu dodatku .NET Framework w celu aktywowania dodatku, który niejawnie zwraca widok hosta do aplikacji hosta. Następnie aplikacja hosta wyświetla widok hosta (który jest <xref:System.Windows.Controls.UserControl>) <xref:System.Windows.Controls.Grid>z.  
  
 Kod służący do przetwarzania interakcji z interfejsem użytkownika dodatku działa w domenie aplikacji dodatku. Te interakcje obejmują następujące elementy:  
  
- <xref:System.Windows.Controls.Button> Obsługa<xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.  
  
- <xref:System.Windows.MessageBox>Wyświetlanie.  
  
 To działanie jest całkowicie odizolowane od aplikacji hosta.  
  
## <a name="see-also"></a>Zobacz także

- [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Dodatki WPF — omówienie](wpf-add-ins-overview.md)
