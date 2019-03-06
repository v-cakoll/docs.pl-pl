---
title: Struktura wejścia ze zdolnością do współpracy Windows Forms i WPF
ms.date: 03/30/2017
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
ms.openlocfilehash: 50097ef86fb6bc5341d7ea16ccee441b89823401
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352428"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Struktura wejścia ze zdolnością do współpracy Windows Forms i WPF
Współdziałanie między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] wymaga, że obie technologie mają odpowiednie skróty przetwarzania danych wejściowych. W tym temacie opisano sposób implementacji tych technologii, klawiatury i przetwarzania, aby umożliwić bezproblemowe współdziałanie w aplikacjach hybrydowych komunikatów.  
  
 Ten temat zawiera następujące podsekcje:  
  
-   Niemodalne formularze i okna dialogowe  
  
-   Windowsformshost — klawiatura i przetwarzanie komunikatów  
  
-   Elementhost — klawiatura i przetwarzanie komunikatów  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Niemodalne formularze i okna dialogowe  
 Wywołanie <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> metody w <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, aby otworzyć niemodalne okno formularza lub okna dialogowego z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.  
  
 Wywołania <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metody <xref:System.Windows.Forms.Integration.ElementHost> control, aby otworzyć niemodalne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]— na podstawie aplikacji.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>Windowsformshost — klawiatura i przetwarzanie komunikatów  
 W przypadku hostowania za [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-aplikacji opartej na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klawiatury i przetwarzania składa się z następujących komunikatów:  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Klasy uzyskuje wiadomości z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pętli komunikatów, który jest implementowany przez <xref:System.Windows.Interop.ComponentDispatcher> klasy.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Klasy tworzy zastępczy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętli komunikatów, aby upewnić się, że zwykłych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] przetwarzania klawiatury.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Klasy implementuje <xref:System.Windows.Interop.IKeyboardInputSink> interfejsu do zapewnienia koordynacji zarządzania fokus przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Kontrolki rejestrują się i rozpocząć ich pętli komunikatów.  
  
 W poniższych sekcjach opisano te części procesu bardziej szczegółowo.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Pobieranie wiadomości z pętli komunikatów dla WPF  
 <xref:System.Windows.Interop.ComponentDispatcher> Klasa implementuje Menedżera pętli komunikatów dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.ComponentDispatcher> Klasa udostępnia punkty zaczepienia umożliwiające klientów zewnętrznych, by przefiltrować komunikaty zanim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przetwarza je.  
  
 Obsługuje współdziałanie implementacji <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> zdarzenie, które umożliwia [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] służy do przetwarzania komunikatów przed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Pętli komunikatów dla zastępczy Windows Forms  
 Domyślnie <xref:System.Windows.Forms.Application?displayProperty=nameWithType> klasa zawiera pętli komunikatów głównej dla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji. Podczas współdziałanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] komunikat pętli nie przetwarza komunikatów. W związku z tym można odtworzyć tę logikę. Obsługa <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> zdarzeń wykonuje następujące czynności:  
  
1.  Filtry wiadomości przy użyciu <xref:System.Windows.Forms.IMessageFilter> interfejsu.  
  
2.  Wywołania <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metody.  
  
3.  Tłumaczy i wysyła komunikat, jeśli jest to wymagane.  
  
4.  Przekazuje komunikat do hostowania kontrolki, jeśli brak innych kontrolek przetworzyć komunikatu.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implementacja IKeyboardInputSink  
 Zastępczy pętli komunikatów obsługuje zarządzanie klawiatury. W związku z tym <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> metody jest jedyną <xref:System.Windows.Interop.IKeyboardInputSink> elementu członkowskiego, który wymaga implementacji w <xref:System.Windows.Forms.Integration.WindowsFormsHost> klasy.  
  
 Domyślnie <xref:System.Windows.Interop.HwndHost> klasy zwraca `false` dla jego <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> implementacji. Zapobiega to klawiszem TAB z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolę [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Implementacji <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> metoda wykonuje następujące czynności:  
  
1.  Wyszukuje pierwszy lub ostatni [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który jest zawarty w <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli i który może odebrać fokus. Wybór kontroli zależy od informacji przechodzenia.  
  
2.  Ustawia fokus do formantu i zwraca `true`.  
  
3.  Jeśli formant nie może odebrać fokus, zwraca `false`.  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost rejestracji  
 Jeśli okna obsługi do <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant zostanie utworzony, <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolki wywołuje wewnętrznego statyczna metoda, która rejestruje jego obecność dla pętli komunikatów.  
  
 Podczas rejestracji <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli sprawdza pętli komunikatów. Jeśli nie uruchomiono pętli komunikatów, <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> program obsługi zdarzeń jest tworzone. Pętla komunikatów jest uważany za uruchomione podczas <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> programu obsługi zdarzeń jest dołączony.  
  
 Kiedy niszczony jest uchwyt okna, <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli usuwa z rejestracji.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>Elementhost — klawiatura i przetwarzanie komunikatów  
 W przypadku hostowania za [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klawiatury i przetwarzania składa się z następujących komunikatów:  
  
-   <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>, i <xref:System.Windows.Interop.IKeyboardInputSite> implementacji interfejsu.  
  
-   Klawisze strzałki i klawiszem TAB.  
  
-   Polecenie klucze i klucze okno dialogowe.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Przetwarzanie akceleratora.  
  
 W poniższych sekcjach opisano te części bardziej szczegółowo.  
  
### <a name="interface-implementations"></a>Implementacje interfejsu  
 W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], komunikaty klawiatury są kierowane do uchwyt okna formantu, który jest ustawiony fokus. W <xref:System.Windows.Forms.Integration.ElementHost> kontrolki, te komunikaty są kierowane do element hostowany. Aby to osiągnąć, <xref:System.Windows.Forms.Integration.ElementHost> control oferuje <xref:System.Windows.Interop.HwndSource> wystąpienia. Jeśli <xref:System.Windows.Forms.Integration.ElementHost> kontrolka ma fokus, <xref:System.Windows.Interop.HwndSource> wystąpienia kieruje większość klawiatury, aby mogą być przetwarzane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> klasy.  
  
 <xref:System.Windows.Interop.HwndSource> Klasy implementuje <xref:System.Windows.Interop.IKeyboardInputSink> i <xref:System.Windows.Interop.IKeyboardInputSite> interfejsów.  
  
 Współdziałanie klawiatury opiera się na implementowaniu <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> metodą klawisza TAB dojścia i strzałki klucza dane wejściowe, które powoduje przeniesienie fokusu poza hostowanej elementów.  
  
### <a name="tabbing-and-arrow-keys"></a>Tabbing i klawisze strzałek  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Logikę wyboru jest mapowany na <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> i <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> metody służące do implementacji kartę i Strzałka klucza nawigacji. Zastępowanie <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> metody w ramach tego mapowania.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Polecenie klucze i klucze okno dialogowe  
 Aby zapewnić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pierwsza okazja do przetwarzania polecenia klucze i klucze okna dialogowego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] poleceń przetwarzania wstępnego jest podłączony do <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> metody. Zastępowanie <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> metoda łączy dwie technologie.  
  
 Za pomocą <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> metody hostowanej elementów może obsługiwać żadnych kluczy wiadomości, takich jak przetłumaczyła, WM_KEYUP, WM_SYSKEYDOWN lub WM_SYSKEYUP, w tym kluczy polecenia, takie jak klucze TAB, ENTER, ESC i strzałki. Jeśli komunikat klucza nie jest obsługiwane, są wysyłane [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hierarchii nadrzędny obsługi.  
  
### <a name="accelerator-processing"></a>Przetwarzanie klawiszy skrótów  
 Poprawnie przetworzyć akceleratorów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] akceleratora przetwarzania musi być podłączony do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> klasy. Ponadto wszystkie komunikaty WM_CHAR muszą być prawidłowo kierowane do hostowanych elementów.  
  
 Ponieważ wartość domyślna <xref:System.Windows.Interop.HwndSource> implementacji <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> metoda zwraca `false`, WM_CHAR komunikaty są przetwarzane przy użyciu logiki poniższym:  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> Metoda zostanie przesłonięta, aby upewnić się, że wszystkie komunikaty WM_CHAR są przekazywane do hostowanej elementów.  
  
-   W przypadku naciśnięcia klawisza ALT, komunikat jest WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Nie przetwarzaj wstępnie tego komunikatu za pośrednictwem <xref:System.Windows.Forms.Control.IsInputChar%2A> metody. W związku z tym <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> metoda zostanie przesłonięta zapytania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> dla zarejestrowanego akceleratora. Jeśli zostanie znaleziony zarejestrowanych akceleratora, <xref:System.Windows.Input.AccessKeyManager> przetwarza je.  
  
-   Jeśli nie jest wciśnięty klawisz ALT, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> klasy przetwarza nieobsługiwany dane wejściowe. Jeśli dane wejściowe to akcelerator <xref:System.Windows.Input.AccessKeyManager> przetwarza je. <xref:System.Windows.Input.InputManager.PostProcessInput> Zdarzenie jest obsługiwane dla WM_CHAR wiadomości, które nie zostały przetworzone.  
  
 Gdy użytkownik naciśnie klawisz ALT, akcelerator podpowiedzi wizualne są wyświetlane na cały formularz. Do obsługi tego zachowania wszystkich <xref:System.Windows.Forms.Integration.ElementHost> kontrolek w formularzu aktywne komunikaty WM_SYSKEYDOWN, niezależnie od tego, które kontrolki jest ustawiony fokus.  
  
 Komunikaty są wysyłane tylko do <xref:System.Windows.Forms.Integration.ElementHost> formantów w formularzu active.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
