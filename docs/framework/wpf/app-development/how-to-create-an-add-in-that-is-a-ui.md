---
title: 'Instrukcje: Utwórz dodatek, który jest interfejsem użytkownika'
ms.date: 03/30/2017
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: f81812b766242311ac29c43de68906d65ae52b32
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366390"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Instrukcje: Utwórz dodatek, który jest interfejsem użytkownika
Ten przykład przedstawia sposób tworzenia dodatku, który jest Windows Presentation Foundation (WPF), która jest hostowana przez oddzielną aplikację WPF.  
  
 Dodatek jest interfejs użytkownika, który jest formanty użytkownika WPF. Zawartość kontrolki użytkownika nie ma jednego przycisku, po kliknięciu wyświetla okno komunikatu. Aplikacja autonomiczna WPF obsługuje dodatków interfejsu użytkownika jako zawartość okna głównego aplikacji.  
  
 **Wymagania wstępne**  
  
 W tym przykładzie wyróżnia rozszerzenia WPF model dodatku .NET Framework, które umożliwiają w tym scenariuszu i przyjęto założenie, że:  
  
-   Znajomość środowiska .NET Framework — w modelu, w tym potoku dodatku i rozwoju hosta. Jeśli nie jesteś zaznajomiony z tych pojęć, zobacz [dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Aby uzyskać samouczek, który przedstawia implementację potoku dodatku i aplikacji hosta, zobacz [instruktażu: Tworzenie aplikacji rozszerzalnej](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
-   Wiedza na temat rozszerzenia WPF model dodatku .NET Framework. Zobacz [Przegląd dodatki WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Przykład  
 Aby utworzyć dodatek, który jest interfejsem użytkownika WPF wymaga określonego kodu dla każdy z segmentów potoku dodatku i aplikacji hosta.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementowanie segmentów potoku kontraktu  
 Gdy dodatek jest interfejsem użytkownika, należy zaimplementować kontrakt dla dodatku <xref:System.AddIn.Contract.INativeHandleContract>. W tym przykładzie `IWPFAddInContract` implementuje <xref:System.AddIn.Contract.INativeHandleContract>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementowanie segmentów potoku dodatku widoku  
 Ponieważ dodatek jest implementowany jako podklasą <xref:System.Windows.FrameworkElement> typu widoku dodatku musi również podklasy <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok dodatku kontraktu, zaimplementowane jako `WPFAddInView` klasy.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 W tym miejscu widoku dodatku jest tworzony na podstawie <xref:System.Windows.Controls.UserControl>. W związku z tym, Dodaj w interfejsie użytkownika powinien również pochodzić od <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementowanie segmentów potoku dodać strony karty  
 Podczas gdy kontrakt jest <xref:System.AddIn.Contract.INativeHandleContract>, dodatek jest <xref:System.Windows.FrameworkElement> (zgodnie z określonym segmentów potoku dodatku widoku). W związku z tym <xref:System.Windows.FrameworkElement> muszą zostać skonwertowane do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji. Ta praca jest wykonywana przez siebie w Dodaj kartę przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 W modelu dodatków gdzie dodatek zwraca interfejs użytkownika (zobacz [Tworzenie dodatku, zwraca interfejs użytkownika](how-to-create-an-add-in-that-returns-a-ui.md)), przekonwertować karty dodatku <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> również musi zostać wywołany w tym modelu, chociaż należy zaimplementować metodę, z którego można zapisywać jej wywołania kodu. Możesz to zrobić przez zastąpienie <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> i wdrażanie kodu, który wywołuje <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> Jeśli kod, który wywołuje <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> oczekuje <xref:System.AddIn.Contract.INativeHandleContract>. W tym przypadku obiekt wywołujący będzie adapter po stronie hosta, co zostało omówione w kolejnej podsekcji.  
  
> [!NOTE]
>  Musisz także Przesłoń <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> w tym modelu Włączanie przełączania między aplikacją hosta interfejsu użytkownika i interfejsu użytkownika dodatku. Aby uzyskać więcej informacji, zobacz temat "WPF dodatku ograniczenia" w [Przegląd dodatki WPF](wpf-add-ins-overview.md).  
  
 Ponieważ karta add w side implementuje interfejs, który pochodzi od klasy <xref:System.AddIn.Contract.INativeHandleContract>, trzeba będzie również zaimplementować <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, mimo że to jest ignorowany podczas <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> zostanie zastąpiona.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementowanie segmentów potoku widok hosta  
 W tym modelu aplikacja hosta zazwyczaj oczekuje, że widok hosta jako <xref:System.Windows.FrameworkElement> podklasę. Adaptery po stronie hosta muszą być konwertowane <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> po <xref:System.AddIn.Contract.INativeHandleContract> przecina granicę izolacji. Ponieważ metoda nie jest wywoływana przez hosta aplikacji w celu uzyskania <xref:System.Windows.FrameworkElement>, widoku hosta musi "return" <xref:System.Windows.FrameworkElement> przez umieszczenie go. W związku z tym, w widoku hosta muszą pochodzić od podklasą <xref:System.Windows.FrameworkElement> może zawierać inne [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], takich jak <xref:System.Windows.Controls.UserControl>. Poniższy kod przedstawia widok hosta umowy, zaimplementowane jako `WPFAddInHostView` klasy.  
  
  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementowanie segmentów potoku adaptery po stronie hosta  
 Podczas gdy kontrakt jest <xref:System.AddIn.Contract.INativeHandleContract>, oczekuje, że aplikacja hosta <xref:System.Windows.Controls.UserControl> (jak określono w widoku hosta). W związku z tym <xref:System.AddIn.Contract.INativeHandleContract> muszą zostać skonwertowane do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji, zanim zostanie ustawiona jako zawartość widoku hosta (która jest pochodną <xref:System.Windows.Controls.UserControl>).  
  
 Ta praca odbywa się przez adapter po stronie hosta, jak pokazano w poniższym kodzie.  
  
  
  
 Jak widać, adapter po stronie hosta uzyskuje <xref:System.AddIn.Contract.INativeHandleContract> przez wywołanie metody karty add w side <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> — metoda (jest to punkt gdzie <xref:System.AddIn.Contract.INativeHandleContract> przecina granicę izolacji).  
  
 Adaptery po stronie hosta następnie konwertuje <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Na koniec <xref:System.Windows.FrameworkElement> jest ustawiony jako zawartość widoku hosta.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Wdrażanie dodatku programu  
 Karta Dodaj w side i wyświetlanie dodatku w miejscu dodatek może być implementowana przez pochodząca z widoku dodatku, jak pokazano w poniższym kodzie.  
  
  
  
  
  
 W tym przykładzie widać, co ciekawe zaletą tego modelu: deweloperzy w dodatku wystarczy do zaimplementowania dodatku (ponieważ jest to również interfejs użytkownika), a nie klasy dodatku i dodatków interfejsu użytkownika.  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>Wdrażanie aplikacji hosta  
 Adaptery po stronie hosta i widok hosta utworzony, można użyć aplikacji hosta [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu w dodatku, otwórz potok i uzyskać widok hosta dodatków. Te kroki są wyświetlane w poniższym kodzie.  
  
  
  
 Aplikacja hosta używa typowy kod model dodatku .NET Framework do aktywowania dodatku, niejawnie zwracające widoku hosta aplikacji hosta. Aplikacja hosta następnie wyświetla widok hosta (czyli <xref:System.Windows.Controls.UserControl>) z <xref:System.Windows.Controls.Grid>.  
  
 Kod dla przetwarzania interakcji z interfejsem użytkownika dodatku działa w dodatku w domenie aplikacji. Interakcje te obejmują:  
  
-   Obsługa <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
-   Wyświetlanie <xref:System.Windows.MessageBox>.  
  
 To działanie jest całkowicie odizolowana od aplikacji hosta.  
  
## <a name="see-also"></a>Zobacz także
- [Dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Dodatki WPF — omówienie](wpf-add-ins-overview.md)
