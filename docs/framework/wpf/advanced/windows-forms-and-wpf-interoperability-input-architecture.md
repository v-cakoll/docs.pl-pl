---
title: "Struktura wejścia ze zdolnością do współpracy Windows Forms i WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a246a3297d212eabc31bf2ac9d000aeb56329d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Struktura wejścia ze zdolnością do współpracy Windows Forms i WPF
Współdziałanie między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] musi mieć obu tych technologii przetwarzania wejściowych odpowiedniej klawiatury. W tym temacie opisano, jak te technologie zaimplementować klawiatury i przetwarzania umożliwia sprawne współdziałanie w aplikacjach hybrydowego komunikatów.  
  
 Ten temat zawiera następujące podsekcje:  
  
-   Niemodalne formularzach i oknach dialogowych  
  
-   Klawiatura WindowsFormsHost i przetwarzanie komunikatów  
  
-   ElementHost klawiatury i przetwarzanie komunikatów  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Niemodalne formularzach i oknach dialogowych  
 Wywołanie <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, aby otworzyć niemodalne okno formularza lub okna dialogowego z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-aplikacji.  
  
 Wywołanie <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metody w <xref:System.Windows.Forms.Integration.ElementHost> sterowania, aby otworzyć niemodalny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w obszarze [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]— aplikacji.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>Klawiatura WindowsFormsHost i przetwarzanie komunikatów  
 Obsługiwany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-aplikacji opartej na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klawiatury i przetwarzania składa się z następujących komunikatów:  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Klas uzyskuje komunikaty z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pętli komunikatów, który jest implementowany przez <xref:System.Windows.Interop.ComponentDispatcher> klasy.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Klasy tworzy surogatu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętli komunikatów, aby upewnić się, że zwykłych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] przetwarzania klawiatury.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Klasa implementuje <xref:System.Windows.Interop.IKeyboardInputSink> interfejs do koordynowania fokus zarządzania za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Formanty rejestrować i uruchomić ich pętli komunikatów.  
  
 W poniższych sekcjach opisano te części procesu bardziej szczegółowo.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Pobieranie wiadomości z pętli komunikatów WPF  
 <xref:System.Windows.Interop.ComponentDispatcher> Klasa implementuje Menedżera pętli komunikatów dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.ComponentDispatcher> Klasa udostępnia punkty zaczepienia, aby umożliwić klientom zewnętrznych do filtrowania wiadomości przed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przetwarza je.  
  
 Uchwyty współdziałanie implementacji <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> zdarzeń, dzięki czemu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] służy do przetwarzania komunikatów przed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Pętli komunikatów formularzy systemu Windows Surogat  
 Domyślnie <xref:System.Windows.Forms.Application?displayProperty=nameWithType> klasa zawiera pętli komunikatów głównej dla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji. Podczas współdziałanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] komunikat pętli nie może przetwarzać komunikatów. W związku z tym można odtworzyć ten logiki. Program obsługi dla <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> zdarzeń wykonuje następujące czynności:  
  
1.  Filtry wiadomości przy użyciu <xref:System.Windows.Forms.IMessageFilter> interfejsu.  
  
2.  Wywołania <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metody.  
  
3.  Wykonuje translację i wysyła komunikat, jeśli jest to wymagane.  
  
4.  Przekazaniem do hostowania formantu, jeśli żadne inne formanty przetworzyć komunikatu.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implementacja IKeyboardInputSink  
 Pętli komunikatów Surogat obsługuje zarządzanie klawiatury. W związku z tym <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> jest jedyną metodą <xref:System.Windows.Interop.IKeyboardInputSink> elementu członkowskiego, który wymaga implementacja <xref:System.Windows.Forms.Integration.WindowsFormsHost> klasy.  
  
 Domyślnie <xref:System.Windows.Interop.HwndHost> klasy zwraca `false` dla jego <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> implementacji. Zapobiega to klawisza TAB z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Implementacja <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> metoda wykonuje następujące czynności:  
  
1.  Znajduje pierwsze lub ostatnie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który jest zawarty w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli i które można ustawić fokusu. Wybór kontroli zależy od informacji przechodzenie.  
  
2.  Ustawia fokus do formantu i zwraca `true`.  
  
3.  Jeśli formant nie może odebrać fokus, zwraca `false`.  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost rejestracji  
 Gdy uchwyt okna, aby <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant jest utworzony, <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli wywołuje metody statycznej wewnętrznej rejestruje jego obecność dla pętli komunikatów.  
  
 Podczas rejestracji <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant sprawdza pętli komunikatów. Jeśli nie uruchomiono pętlę komunikatów, <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> program obsługi zdarzeń jest utworzony. Pętla wiadomości jest uznawany za uruchomione podczas <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> program obsługi zdarzeń jest dołączony.  
  
 Gdy zostanie zniszczony uchwytu okna, <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli usuwa z rejestracji.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost klawiatury i przetwarzanie komunikatów  
 Obsługiwany przez [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klawiatury i przetwarzania składa się z następujących komunikatów:  
  
-   <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>, i <xref:System.Windows.Interop.IKeyboardInputSite> implementacji interfejsu.  
  
-   Klucze klawisza TAB i strzałki.  
  
-   Polecenie klucze i klucze — okno dialogowe.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Przetwarzanie akceleratora.  
  
 W poniższych sekcjach opisano te części bardziej szczegółowo.  
  
### <a name="interface-implementations"></a>Implementacje interfejsu  
 W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], komunikaty klawiatury są kierowane do uchwytu okna dla formantu, który ma fokus. W <xref:System.Windows.Forms.Integration.ElementHost> kontroli, komunikaty te są kierowane do elementu hostowanej. Aby to osiągnąć, <xref:System.Windows.Forms.Integration.ElementHost> kontrola zapewnia <xref:System.Windows.Interop.HwndSource> wystąpienia. Jeśli <xref:System.Windows.Forms.Integration.ElementHost> formant ma fokus, <xref:System.Windows.Interop.HwndSource> wystąpienia kieruje większości przy użyciu klawiatury, aby mogą być przetwarzane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> klasy.  
  
 <xref:System.Windows.Interop.HwndSource> Klasa implementuje <xref:System.Windows.Interop.IKeyboardInputSink> i <xref:System.Windows.Interop.IKeyboardInputSite> interfejsów.  
  
 Współdziałanie klawiatury zależy od implementacji <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> metodę dojścia klawisza TAB i strzałki klucza danych wejściowych, który przenosi fokus poza hostowanej elementów.  
  
### <a name="tabbing-and-arrow-keys"></a>Tabbing i klawiszy strzałek  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Logiki zaznaczenie jest mapowany na <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> i <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> metody służące do implementacji kartę i Strzałka klucza nawigacji. Zastępowanie <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> metoda wykonuje się to mapowanie.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Polecenie klucze i klucze — okno dialogowe  
 Aby zapewnić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pierwsza okazja do przetworzenia polecenia klucze i klucze okna dialogowego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] polecenia wstępnego przetwarzania jest podłączony do <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> — metoda. Zastępowanie <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> metody łączy dwie technologie.  
  
 Z <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> metody hostowanej elementów może obsługiwać dowolny komunikat klucza, takich jak WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN lub WM_SYSKEYUP, w tym klucze polecenia, takie jak klucze kartę, wprowadź ESC i strzałki. Komunikat klucza nie jest obsługiwana, jest wysyłana [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hierarchii nadrzędnej obsługi.  
  
### <a name="accelerator-processing"></a>Przetwarzanie klawiszy skrótów  
 Poprawnie, przetworzyć akceleratorów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] akceleratora przetwarzania musi być podłączony do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> klasy. Ponadto wszystkie komunikaty WM_CHAR muszą być prawidłowo kierowane do hostowanych elementów.  
  
 Ponieważ domyślne <xref:System.Windows.Interop.HwndSource> implementacja <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> metoda zwraca `false`, WM_CHAR wiadomości są przetwarzane przy użyciu z następującą logiką:  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> Metoda zostanie przesłonięta, aby upewnić się, że wszystkie komunikaty WM_CHAR są przekazywane do hostowanej elementów.  
  
-   Jeśli zostanie naciśnięty klawisz ALT, wiadomość jest WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Nie przetwarzaj wstępnie tego komunikatu za pośrednictwem <xref:System.Windows.Forms.Control.IsInputChar%2A> metody. W związku z tym <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> metoda zostanie przesłonięta w zapytaniu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> dla zarejestrowanego akceleratora. Jeśli zostanie znaleziony zarejestrowanych akceleratora, <xref:System.Windows.Input.AccessKeyManager> przetwarza je.  
  
-   Jeśli nie zostanie naciśnięty klawisz ALT, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> klasy przetwarza nieobsługiwany danych wejściowych. Jeśli dane wejściowe to akcelerator <xref:System.Windows.Input.AccessKeyManager> przetwarza je. <xref:System.Windows.Input.InputManager.PostProcessInput> Zdarzenie jest obsługiwane dla komunikatów WM_CHAR, które nie zostały przetworzone.  
  
 Gdy użytkownik naciśnie klawisz ALT, akceleratora podpowiedzi wizualne są wyświetlane na cały formularz. Do obsługi tego zachowania, wszystkie <xref:System.Windows.Forms.Integration.ElementHost> formantów w formularzu active odbierać komunikaty WM_SYSKEYDOWN, niezależnie od tego, które formant ma fokus.  
  
 Komunikaty są wysyłane tylko z <xref:System.Windows.Forms.Integration.ElementHost> formantów w formularzu aktywne.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
