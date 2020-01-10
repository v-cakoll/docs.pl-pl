---
title: Udostępnianie pętli komunikatów pomiędzy Win32 i WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 5c1d75ab9598196e9cffc78a2f116993e722fd38
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740319"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Udostępnianie pętli komunikatów pomiędzy Win32 i WPF
W tym temacie opisano sposób implementacji pętli komunikatów dla operacji międzyoperacyjnych z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], przy użyciu istniejącej ekspozycji pętli komunikatów w <xref:System.Windows.Threading.Dispatcher> lub przez utworzenie oddzielnej pętli komunikatów na stronie Win32 kodu międzyoperacyjnego.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher i pętla komunikatów  
 Normalny scenariusz obsługi zdarzeń międzyoperacyjnych i klawiatury polega na wdrożeniu <xref:System.Windows.Interop.IKeyboardInputSink>lub do podklasy z klas, które już implementują <xref:System.Windows.Interop.IKeyboardInputSink>, takich jak <xref:System.Windows.Interop.HwndSource> lub <xref:System.Windows.Interop.HwndHost>. Jednak obsługa ujścia klawiatury nie dotyczy wszystkich możliwych pętli komunikatów, które mogą wystąpić podczas wysyłania i otrzymywania komunikatów między granicami operacji. Aby ułatwić prace prowadzone architektury pętli komunikatów aplikacji, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia klasę <xref:System.Windows.Interop.ComponentDispatcher>, która definiuje prosty protokół dla pętli komunikatów do wykonania.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> jest klasą statyczną, która uwidacznia kilka członków. Zakres każdej metody jest niejawnie powiązany z wywołaniem wątku. Pętla komunikatów musi wywoływać niektóre z tych interfejsów API w sytuacjach krytycznych (zgodnie z definicją w następnej sekcji).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> udostępnia zdarzenia, które mogą nasłuchiwać inne składniki (na przykład ujścia klawiatury). Klasa <xref:System.Windows.Threading.Dispatcher> wywołuje wszystkie odpowiednie metody <xref:System.Windows.Interop.ComponentDispatcher> w odpowiedniej kolejności. W przypadku wdrażania własnej pętli komunikatów kod jest odpowiedzialny za wywoływanie metod <xref:System.Windows.Interop.ComponentDispatcher> w podobny sposób.  
  
 Wywoływanie metod <xref:System.Windows.Interop.ComponentDispatcher> w wątku wywoła tylko programy obsługi zdarzeń zarejestrowane w tym wątku.  
  
## <a name="writing-message-loops"></a>Pisanie pętli komunikatów  
 Poniżej znajduje się lista kontrolna <xref:System.Windows.Interop.ComponentDispatcher> członków, których będziesz używać w przypadku pisania własnej pętli komunikatów:  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: Pętla komunikatów powinna wywołać tę metodę, aby wskazać, że wątek jest modalny.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: Pętla komunikatów powinna wywołać tę metodę, aby wskazać, że wątek został przywrócony do niemodalny.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: Pętla komunikatów powinna wywołać tę metodę, aby wskazać, że <xref:System.Windows.Interop.ComponentDispatcher> powinna zgłosić zdarzenie <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>. <xref:System.Windows.Interop.ComponentDispatcher> nie będzie zgłaszać <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>, jeśli <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> jest `true`, ale pętle komunikatów mogą wybrać wywołanie <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> nawet wtedy, gdy <xref:System.Windows.Interop.ComponentDispatcher> nie mogą odpowiedzieć na to w stanie modalnym.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: Pętla komunikatów powinna wywołać ten element, aby wskazać, że jest dostępny nowy komunikat. Wartość zwracana wskazuje, czy odbiornik zdarzenia <xref:System.Windows.Interop.ComponentDispatcher> obsłużył komunikat. Jeśli <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> zwraca `true` (obsłużony), Dyspozytor nie powinien niczego robić. Jeśli wartość zwracana jest `false`, Dyspozytor oczekuje na wywołanie funkcji Win32 `TranslateMessage`, a następnie Wywołaj `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Korzystanie z ComponentDispatcher i istniejącej obsługi komunikatów  
 Poniżej znajduje się lista kontrolna <xref:System.Windows.Interop.ComponentDispatcher> elementów członkowskich, które będą używane w przypadku polegania na pętli nieodłącznej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komunikatów.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: zwraca czy aplikacja ma niemodalny (np. pętla komunikatu modalnego została wypchnięcia). <xref:System.Windows.Interop.ComponentDispatcher> może śledzić ten stan, ponieważ Klasa utrzymuje liczbę wywołań <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> i <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> z pętli komunikatów.  
  
- zdarzenia <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> i <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> są zgodne ze standardowymi regułami dotyczącymi delegatów wywołań. Delegaty są wywoływane w nieokreślonej kolejności, a wszystkie Delegaty są wywoływane nawet wtedy, gdy pierwszy raz oznacza komunikat jako obsłużony.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: wskazuje odpowiedni i wydajny czas na przetworzenie bezczynności (nie ma żadnych innych oczekujących komunikatów dla wątku). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> nie zostanie zgłoszony, jeśli wątek jest modalny.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: wywołane dla wszystkich komunikatów, które są przetwarzane przez przekaźnik komunikatów.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: wywołane dla wszystkich komunikatów, które nie zostały obsłużone podczas <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Komunikat jest uznawany za obsłużony, jeśli po zdarzeniu <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> lub <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>, parametr `handled` przeszedł przez odwołanie w danych zdarzenia jest `true`. Programy obsługi zdarzeń powinny ignorować komunikat, jeśli `handled` jest `true`, ponieważ oznacza to, że inna procedura obsługi najpierw obsłuży komunikat. Programy obsługi zdarzeń do obu zdarzeń mogą zmodyfikować komunikat. Dyspozytor powinien wysłać zmodyfikowany komunikat, a nie oryginalny komunikat niezmieniony. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> jest dostarczany do wszystkich odbiorników, ale zamiarem architektury jest to, że tylko okno najwyższego poziomu zawierające Właściwość HWND, w której będą wskazywane komunikaty, powinny wywołać kod w odpowiedzi na komunikat.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Jak HwndSource traktuje zdarzenia ComponentDispatcher  
 Jeśli <xref:System.Windows.Interop.HwndSource> jest oknem najwyższego poziomu (brak nadrzędnego elementu HWND), zostanie on zarejestrowany z <xref:System.Windows.Interop.ComponentDispatcher>. Jeśli <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> jest zgłaszane i jeśli komunikat jest przeznaczony dla <xref:System.Windows.Interop.HwndSource> lub okien podrzędnych, <xref:System.Windows.Interop.HwndSource> wywołuje <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> sekwencję ujścia klawiatury.  
  
 Jeśli <xref:System.Windows.Interop.HwndSource> nie jest oknem najwyższego poziomu (ma element nadrzędny HWND), nie będzie żadnej obsługi. Oczekiwano obsługi tylko okna najwyższego poziomu, a oczekuje się, że jest oknem najwyższego poziomu z obsługą ujścia klawiatury w ramach dowolnego scenariusza międzyoperacyjnego.  
  
 Jeśli <xref:System.Windows.Interop.HwndHost.WndProc%2A> na <xref:System.Windows.Interop.HwndSource> jest wywoływana bez uprzedniego wywołania odpowiedniej metody ujścia klawiatury, aplikacja otrzyma zdarzenia klawiatury wyższego poziomu, takie jak <xref:System.Windows.UIElement.KeyDown>. Jednak żadna metoda ujścia klawiatury nie zostanie wywołana, co spowoduje obejście pożądanych funkcji modelu wprowadzania z klawiatury, takich jak obsługa kluczy dostępu. Może się tak zdarzyć, ponieważ pętla komunikatów nie powiadomiła prawidłowo odpowiedniego wątku na <xref:System.Windows.Interop.ComponentDispatcher>lub ponieważ właściwość HWND elementu nadrzędnego nie wywołała właściwych odpowiedzi ujścia klawiatury.  
  
 Komunikat, który przechodzi do ujścia klawiatury, może nie zostać wysłany do parametru HWND, jeśli dodano punkty zaczepienia dla tego komunikatu przy użyciu metody <xref:System.Windows.Interop.HwndSource.AddHook%2A>. Komunikat mógł zostać obsłużony bezpośrednio na poziomie pompy komunikatów i nie został przesłany do funkcji `DispatchMessage`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Model wątkowości](threading-model.md)
- [Przegląd danych wejściowych](input-overview.md)
