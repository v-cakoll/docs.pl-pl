---
title: Architektura danych wejściowych Windows Forms i WPF
titleSuffix: ''
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
ms.openlocfilehash: f79971ba13691ccc36420e39696b7b8a46e5ce0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745046"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Struktura wejścia ze zdolnością do współpracy Windows Forms i WPF
Współdziałanie między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] wymaga, aby obie technologie miały odpowiednie przetwarzanie danych wejściowych z klawiatury. W tym temacie opisano, w jaki sposób te technologie implementują przetwarzanie za pomocą klawiatury i komunikatów, aby umożliwić bezproblemowe współdziałanie w aplikacjach hybrydowych.  
  
 Ten temat zawiera następujące podsekcje:  
  
- Formularze niemodalne i okna dialogowe  
  
- Przetwarzanie komunikatów i klawiatury WindowsFormsHost  
  
- Przetwarzanie komunikatów i klawiatury ElementHost  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Formularze niemodalne i okna dialogowe  
 Wywołaj metodę <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost>, aby otworzyć niemodalny formularz lub okno dialogowe z aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Wywołaj metodę <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> w kontrolce <xref:System.Windows.Forms.Integration.ElementHost>, aby otworzyć niemodalną stronę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w aplikacji opartej na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>Przetwarzanie komunikatów i klawiatury WindowsFormsHost  
 W przypadku obsługi aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] z klawiatury i przetwarzania komunikatów składa się z następujących elementów:  
  
- Klasa <xref:System.Windows.Forms.Integration.WindowsFormsHost> uzyskuje komunikaty z pętli komunikatów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], która jest implementowana przez klasę <xref:System.Windows.Interop.ComponentDispatcher>.  
  
- Klasa <xref:System.Windows.Forms.Integration.WindowsFormsHost> tworzy wieloczęściową pętlę komunikatu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], aby upewnić się, że nastąpi normalne przetwarzanie klawiatury [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
- Klasa <xref:System.Windows.Forms.Integration.WindowsFormsHost> implementuje interfejs <xref:System.Windows.Interop.IKeyboardInputSink>, aby koordynować zarządzanie fokusem przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroluje siebie i uruchamiają pętle komunikatów.  
  
 W poniższych sekcjach opisano te części procesu bardziej szczegółowo.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Pobieranie komunikatów z pętli komunikatów WPF  
 Klasa <xref:System.Windows.Interop.ComponentDispatcher> implementuje Menedżera pętli komunikatów dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Klasa <xref:System.Windows.Interop.ComponentDispatcher> udostępnia punkty zaczepienia umożliwiające klientom zewnętrznym filtrowanie komunikatów przed ich przetworzeniem przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Implementacja międzyoperacyjna obsługuje zdarzenie <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>, co umożliwia kontrolowanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] do przetwarzania komunikatów przed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkami.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Wieloskładnikowa pętla komunikatu Windows Forms  
 Domyślnie Klasa <xref:System.Windows.Forms.Application?displayProperty=nameWithType> zawiera podstawową pętlę komunikatów dla aplikacji [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Podczas pracy, pętla komunikatów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie przetwarza komunikatów. W związku z tym należy odtworzyć tę logikę. Procedura obsługi dla zdarzenia <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> wykonuje następujące czynności:  
  
1. Filtruje komunikat przy użyciu interfejsu <xref:System.Windows.Forms.IMessageFilter>.  
  
2. Wywołuje metodę <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>.  
  
3. Tłumaczy i wysyła komunikat, jeśli jest to wymagane.  
  
4. Przekazuje komunikat do kontrolki hostingu, jeśli żaden inny formant nie przetwarza komunikatu.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implementacja IKeyboardInputSink  
 Pętla komunikatów zastępczych obsługuje zarządzanie klawiaturą. W związku z tym Metoda <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> jest jedynym członkiem <xref:System.Windows.Interop.IKeyboardInputSink>, który wymaga implementacji w klasie <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Domyślnie Klasa <xref:System.Windows.Interop.HwndHost> zwraca `false` dla implementacji <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>. Uniemożliwia to przejęcie tabulacji z formantu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> implementacja metody <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> wykonuje następujące czynności:  
  
1. Znajduje pierwszy lub ostatni formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], który jest zawarty w kontrolce <xref:System.Windows.Forms.Integration.WindowsFormsHost> i może odebrać fokus. Wybór kontrolki zależy od informacji przechodzenia.  
  
2. Ustawia fokus na kontrolkę i zwraca `true`.  
  
3. Jeśli żaden formant nie może odbierać fokusu, zwraca `false`.  
  
### <a name="windowsformshost-registration"></a>Rejestracja WindowsFormsHost  
 Po utworzeniu uchwytu okna do kontrolki <xref:System.Windows.Forms.Integration.WindowsFormsHost>, kontrolka <xref:System.Windows.Forms.Integration.WindowsFormsHost> wywołuje wewnętrzną metodę statyczną, która rejestruje swoją obecność dla pętli komunikatów.  
  
 Podczas rejestracji formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> analizuje pętlę komunikatów. Jeśli pętla komunikatów nie została uruchomiona, zostanie utworzona procedura obsługi zdarzeń <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>. Pętla komunikatów jest uważana za działającą po dołączeniu programu obsługi zdarzeń <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>.  
  
 Gdy uchwyt okna zostanie zniszczony, formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> usuwa samego siebie z rejestracji.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>Przetwarzanie komunikatów i klawiatury ElementHost  
 W przypadku obsługi aplikacji [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klawiatury i przetwarzania komunikatów obejmują następujące elementy:  
  
- implementacje interfejsu <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>i <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
- Tabulacja i klawisze strzałek.  
  
- Klucze poleceń i okna dialogowe.  
  
- przetwarzanie akceleratora [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 W poniższych sekcjach opisano te części bardziej szczegółowo.  
  
### <a name="interface-implementations"></a>Implementacje interfejsu  
 W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], komunikaty klawiatury są kierowane do uchwytu okna kontrolki, która ma fokus. W kontrolce <xref:System.Windows.Forms.Integration.ElementHost> te komunikaty są kierowane do hostowanego elementu. W tym celu formant <xref:System.Windows.Forms.Integration.ElementHost> dostarcza wystąpienia <xref:System.Windows.Interop.HwndSource>. Jeśli formant <xref:System.Windows.Forms.Integration.ElementHost> ma fokus, wystąpienie <xref:System.Windows.Interop.HwndSource> kieruje dane wejściowe z klawiatury, aby można było je przetworzyć przez klasę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>.  
  
 Klasa <xref:System.Windows.Interop.HwndSource> implementuje interfejsy <xref:System.Windows.Interop.IKeyboardInputSink> i <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
 Funkcja oparta na klawiaturze polega na zaimplementowaniu metody <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> w celu obsłużenia klawisza TAB i wejścia klawisza Strzałka, które przenosi fokus z elementów hostowanych.  
  
### <a name="tabbing-and-arrow-keys"></a>Tabulacja i klawisze strzałek  
 Logika wyboru [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest mapowana na metody <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> i <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> w celu zaimplementowania nawigacji na karcie i klawiszy strzałek. Zastępowanie metody <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> wykonuje to mapowanie.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Klucze poleceń i klucze okna dialogowego  
 Aby dać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pierwszą okazję do przetworzenia kluczy poleceń i kluczy okna dialogowego, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] wstępnego przetwarzania poleceń jest połączona z metodą <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>. Zastępowanie metody <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> łączy dwie technologie.  
  
 Za pomocą metody <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> elementy hostowane mogą obsługiwać dowolny komunikat o kluczu, taki jak WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN lub WM_SYSKEYUP, w tym klucze poleceń, takie jak TAB, ENTER, ESC i klawisze strzałek. Jeśli komunikat klucza nie jest obsługiwany, zostanie on wysłany do obsługi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hierarchii nadrzędnej.  
  
### <a name="accelerator-processing"></a>Przetwarzanie akceleratora  
 Aby prawidłowo przetwarzać akceleratory, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] przetwarzanie akceleratora musi być połączone z klasą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager>. Ponadto wszystkie komunikaty WM_CHAR muszą być poprawnie kierowane do elementów hostowanych.  
  
 Ponieważ domyślna implementacja <xref:System.Windows.Interop.HwndSource> metody <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> zwraca `false`, WM_CHAR komunikaty są przetwarzane przy użyciu następującej logiki:  
  
- Metoda <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> jest zastępowana, aby upewnić się, że wszystkie komunikaty WM_CHAR są przekazywane do elementów hostowanych.  
  
- Po naciśnięciu klawisza ALT komunikat jest WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie przetwarza wstępnie tego komunikatu za pomocą metody <xref:System.Windows.Forms.Control.IsInputChar%2A>. W związku z tym Metoda <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> jest zastępowana, aby zbadać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> dla zarejestrowanego akceleratora. Jeśli zostanie znaleziony zarejestrowany akcelerator, <xref:System.Windows.Input.AccessKeyManager> przetwarza go.  
  
- Jeśli klawisz ALT nie zostanie wciśnięty, Klasa <xref:System.Windows.Input.InputManager> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przetwarza nieobsłużone dane wejściowe. Jeśli dane wejściowe są akceleratorem, <xref:System.Windows.Input.AccessKeyManager> je przetwarza. Zdarzenie <xref:System.Windows.Input.InputManager.PostProcessInput> jest obsługiwane dla WM_CHAR komunikatów, które nie zostały przetworzone.  
  
 Gdy użytkownik naciśnie klawisz ALT, podpowiedzi wizualizacji akceleratora są wyświetlane w całym formularzu. Aby obsłużyć to zachowanie, wszystkie kontrolki <xref:System.Windows.Forms.Integration.ElementHost> w aktywnym formularzu odbierają komunikaty WM_SYSKEYDOWN, niezależnie od tego, który formant ma fokus.  
  
 Komunikaty są wysyłane tylko do kontrolek <xref:System.Windows.Forms.Integration.ElementHost> w aktywnym formularzu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
