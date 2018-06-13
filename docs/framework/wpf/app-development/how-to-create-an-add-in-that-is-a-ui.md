---
title: Jak utworzyć dodatek, który jest interfejsem użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 4bd03c2f879ecab83306bb68552c044a33f2e6e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549594"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Jak utworzyć dodatek, który jest interfejsem użytkownika
W tym przykładzie przedstawiono sposób tworzenia dodatku, który jest Windows Presentation Foundation (WPF), która jest hostowana przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja autonomiczna.  
  
 Dodatek jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czyli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kontrolki użytkownika. Zawartość kontrolki użytkownika jest pojedynczy przycisku, po kliknięciu wyświetla okno komunikatu. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Aplikacji autonomicznych hostów dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jako zawartość okna głównego aplikacji.  
  
 **Wymagania wstępne**  
  
 W tym przykładzie wyróżniono [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerzeń [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, Włącz w tym scenariuszu, która przyjmuje następujące:  
  
-   Znajomość [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku modelu, w tym potoku dodatku i rozwoju hosta. Jeśli znasz tych pojęć, zobacz [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md). Samouczek przedstawiający implementacji potoku, dodatek i aplikacji hosta, zobacz [wskazówki: tworzenie aplikacji rozszerzalnej](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).  
  
-   Znajomość [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerzenia do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, który można znaleźć tutaj: [omówienie Add-Ins WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## <a name="example"></a>Przykład  
 Aby utworzyć dodatku, który jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wymaga określonego kodu dla każdego segmentu potoku dodatku i aplikacji hosta.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementowanie kontraktu segmentów potoku  
 Gdy dodatek jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], muszą implementować kontrakt dodatku <xref:System.AddIn.Contract.INativeHandleContract>. W tym przykładzie `IWPFAddInContract` implementuje <xref:System.AddIn.Contract.INativeHandleContract>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementowanie segmentów potoku dodatku widoku  
 Ponieważ dodatek jest zaimplementowany jako podklasą <xref:System.Windows.FrameworkElement> typu widoku dodatku musi również podklasy <xref:System.Windows.FrameworkElement>. Poniższy kod przedstawia widok dodatku kontraktu zaimplementowane jako `WPFAddInView` klasy.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 W tym miejscu Dodaj w widoku jest pochodną <xref:System.Windows.Controls.UserControl>. W rezultacie dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] również powinien pochodzić od <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementowanie segmentów potoku Dodaj strony karty  
 Gdy kontrakt jest <xref:System.AddIn.Contract.INativeHandleContract>, dodatek jest <xref:System.Windows.FrameworkElement> (określone przez segment potoku dodatku widoku). W związku z tym <xref:System.Windows.FrameworkElement> muszą zostać skonwertowane do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji. To zadanie jest wykonywane przez karty Dodaj w stronie przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 W modelu dodatku, gdzie dodatek zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (zobacz [tworzenia dodatku zwracanych interfejsu użytkownika](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)), przekonwertować adapter dodatku <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> również musi zostać wywołany w tym modelu, chociaż należy zaimplementować metodę, z którego można napisać kod w celu wywołania go. Aby to zrobić, zastępowanie <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> i wdrażanie kod, który wywołuje <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> Jeśli kod, który wywołuje <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> oczekuje <xref:System.AddIn.Contract.INativeHandleContract>. W takim przypadku obiekt wywołujący będzie karty po stronie hosta, które zostało opisane w kolejnych podsekcji.  
  
> [!NOTE]
>  Należy również zastąpić <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> w tym modelu do Włączanie przełączania między aplikacji hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Aby uzyskać więcej informacji, zobacz temat "WPF dodatku ograniczenia" w [omówienie Add-Ins WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Ponieważ karty Dodaj w stronie implementuje interfejs pochodzący z <xref:System.AddIn.Contract.INativeHandleContract>, musisz również wdrożyć <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, mimo że to jest ignorowany podczas <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> zostanie zastąpiona.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementowanie segmentów potoku widoku hosta  
 W tym modelu aplikacji hosta zwykle oczekuje jako widoku hosta <xref:System.Windows.FrameworkElement> podklasy. Adaptery po stronie hosta muszą być konwertowane <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> po <xref:System.AddIn.Contract.INativeHandleContract> przecina granicę izolacji. Ponieważ metoda nie jest wywoływana przez aplikacji hosta w celu uzyskania <xref:System.Windows.FrameworkElement>, widoku hosta musi "return" <xref:System.Windows.FrameworkElement> przez zawierającego go. W rezultacie widoku hosta musi pochodzić od podklasą <xref:System.Windows.FrameworkElement> może zawierać inne [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], takich jak <xref:System.Windows.Controls.UserControl>. Poniższy kod przedstawia kontraktu zaimplementowane jako widoku hosta `WPFAddInHostView` klasy.  
  
  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementowanie segmentów potoku karty po stronie hosta  
 Gdy kontrakt jest <xref:System.AddIn.Contract.INativeHandleContract>, aplikacja hosta oczekuje <xref:System.Windows.Controls.UserControl> (jak określono w widoku hosta). W rezultacie <xref:System.AddIn.Contract.INativeHandleContract> muszą zostać skonwertowane do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji, zanim zostanie ustawiona jako zawartość widoku hosta (pochodzący od <xref:System.Windows.Controls.UserControl>).  
  
 To zadanie jest wykonywane przez karty po stronie hosta, jak pokazano w poniższym kodzie.  
  
  
  
 Jak widać, uzyskuje karty po stronie hosta <xref:System.AddIn.Contract.INativeHandleContract> wywołując karty Dodaj w stronie <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> — metoda (to jest punkt gdzie <xref:System.AddIn.Contract.INativeHandleContract> przecina granicę izolacji).  
  
 Adaptery po stronie hosta następnie konwertuje <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Na koniec <xref:System.Windows.FrameworkElement> jest ustawiony jako zawartość widoku hosta.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementowanie dodatku  
 Dodaj w stronie karty i Dodaj w widoku w miejscu dodatek może być zaimplementowany przez wynikających z widoku dodatku, jak pokazano w poniższym kodzie.  
  
  
  
  
  
 W tym przykładzie widać jeden interesujące zaletą tego modelu: dodatek deweloperzy tylko muszą implementować (ponieważ jest ono [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] również), zamiast zarówno klasy dodatku i dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>Wdrażanie aplikacji hosta  
 Adaptery po stronie hosta i widoku hosta utworzony, można użyć aplikacji hosta [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, aby otworzyć potoku i uzyskać widok hosta dodatku. Te kroki przedstawiono w poniższym kodzie.  
  
  
  
 Aplikacja hosta używa typowej [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kodu dodatku modelu dodatku, która niejawnie zwraca widoku hosta do aplikacji hosta. W widoku hosta następnie wyświetlane w aplikacji hosta (czyli <xref:System.Windows.Controls.UserControl>) z <xref:System.Windows.Controls.Grid>.  
  
 Kod dla przetwarzania interakcji z dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] działa w dodatku w domenie aplikacji. Interakcje te obejmują:  
  
-   Obsługa <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
-   Wyświetlanie <xref:System.Windows.MessageBox>.  
  
 To działanie jest całkowicie odizolowane od aplikacji hosta.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md)  
 [Dodatki WPF — omówienie](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
