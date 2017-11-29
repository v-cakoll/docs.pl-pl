---
title: "Udostępnianie pętli komunikatów pomiędzy Win32 i WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dcf8baa87038bc5625d46968b39d759daae25cbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Udostępnianie pętli komunikatów pomiędzy Win32 i WPF
W tym temacie opisano implementowania na współdziałanie z pętli komunikatów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], przy użyciu istniejących komunikatów narażenia pętli w <xref:System.Windows.Threading.Dispatcher> lub przez tworzenie pętli osobnej wiadomości na [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] obok siebie współdziałanie kodu.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher i pętli komunikatów  
 Scenariusz normalnej obsługi zdarzeń współdziałanie i klawiatury jest zaimplementowanie <xref:System.Windows.Interop.IKeyboardInputSink>, lub do podklasy z klasy, które zawierają już implementację <xref:System.Windows.Interop.IKeyboardInputSink>, takich jak <xref:System.Windows.Interop.HwndSource> lub <xref:System.Windows.Interop.HwndHost>. Obsługa zbiornik klawiatury nie odnosi jednak wszystkie potrzeby pętli możliwe wiadomości, które mogą wystąpić podczas wysyłania i odbierania wiadomości bariery współdziałanie. Aby ułatwić formalnego pętli komunikatów architektura [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia <xref:System.Windows.Interop.ComponentDispatcher> klasy, która definiuje prosty protokół dla pętli komunikatów, które należy wykonać.  
  
 <xref:System.Windows.Interop.ComponentDispatcher>to statyczny klasa, która udostępnia kilka elementów członkowskich. Wątek wywołujący jest niejawnie powiązany zakresu każdej metody. Pętla wiadomości należy wywołać tych [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] w czasie krytyczne (zgodnie z definicją w następnej sekcji).  
  
 <xref:System.Windows.Interop.ComponentDispatcher>zapewnia zdarzenia, które można nasłuchiwać innych składników (na przykład zbiornik klawiatury). <xref:System.Windows.Threading.Dispatcher> Klasy wywołania wszystkie odpowiednie <xref:System.Windows.Interop.ComponentDispatcher> metod w odpowiedniej kolejności. W przypadku wdrażania własnych pętli komunikatów kodu jest odpowiedzialny za wywoływanie <xref:System.Windows.Interop.ComponentDispatcher> metod w podobny sposób.  
  
 Wywoływanie <xref:System.Windows.Interop.ComponentDispatcher> metod w wątku tylko wywoła procedury obsługi zdarzeń, które zostały zarejestrowane na tym wątku.  
  
## <a name="writing-message-loops"></a>Pisanie pętli komunikatów  
 Poniżej znajduje się lista kontrolna <xref:System.Windows.Interop.ComponentDispatcher> elementów członkowskich będzie używać podczas pisania własnych pętli komunikatów:  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: z pętli komunikatów powinny wywoływać, aby wskazać, że wątek jest modalne.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: z pętli komunikatów powinny wywoływać, aby wskazać, że wątek został przywrócony do nonmodal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: z pętli komunikatów powinny wywoływać, aby wskazać, że <xref:System.Windows.Interop.ComponentDispatcher> należy podnieść <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> zdarzeń. <xref:System.Windows.Interop.ComponentDispatcher>nie będą powodowały <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> Jeśli <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> jest `true`, ale zrezygnować pętli komunikatów do wywołania <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> nawet wtedy, gdy <xref:System.Windows.Interop.ComponentDispatcher> nie może odpowiadać na ona w stanie modalne.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: z pętli komunikatów powinny wywoływać, aby wskazać, że dostępny jest nowy komunikat. Zwracana wartość wskazuje, czy odbiornik do <xref:System.Windows.Interop.ComponentDispatcher> zdarzeń obsługi wiadomości. Jeśli <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> zwraca `true` (obsługiwane) Dyspozytor powinien nic nie rób więcej wiadomości. Jeśli wartość zwracana jest `false`, powinien wywołać Dyspozytor [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcja `TranslateMessage`, następnie wywołaj `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Za pomocą ComponentDispatcher i istniejący komunikat — Obsługa  
 Poniżej znajduje się lista kontrolna <xref:System.Windows.Interop.ComponentDispatcher> elementów członkowskich będzie używać, jeśli użytkownik korzysta z nieodłącznej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pętli komunikatów.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: zwraca, czy aplikacja przeszedł modalne (np. pętli komunikatów modalnych ma zostać przypisany). <xref:System.Windows.Interop.ComponentDispatcher>można śledzić ten stan, ponieważ klasa przechowuje liczbę <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> i <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> wywołania z pętli komunikatów.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>i <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> zdarzenia wykonaj standardowe zasady dotyczące delegowanie wywołań. Obiekty delegowane są wywoływane w nieokreślonej kolejności, a wszystkie obiekty delegowane są wywoływane nawet wtedy, gdy pierwszy oznacza komunikat jako obsłużone.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: wskazuje odpowiednią i efektywny czas bezczynności przetwarzania (nie ma żadnych innych komunikatów oczekujących na wątek). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>nie będą zgłaszane w przypadku wątku modalne.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: wywoływane przekazywanie komunikatów przetwarza wszystkie wiadomości.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: wywoływane dla wszystkich wiadomości, które nie zostały obsłużone podczas <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Komunikat jest uznawany za obsługiwany w przypadku po <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> zdarzenia lub <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> zdarzenia `handled` parametr przekazywany przez odwołanie w danych zdarzenia jest `true`. Programy obsługi zdarzeń należy zignorować ten komunikat, jeśli `handled` jest `true`, ponieważ oznacza to, że inny program obsługi najpierw obsługi wiadomości. Programy obsługi zdarzeń do obu zdarzeń mogą być modyfikowane wiadomości. Dyspozytor powinien wysyłania wiadomości zmodyfikowany i nie oryginalnej wiadomości bez zmian. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>jest dostarczany do wszystkich obiektów nasłuchujących, ale zamiar architektury jest to, że tylko najwyższego poziomu okna zawierającego HWND jaką komunikaty docelowe należy wywołać kod w odpowiedzi na wiadomość.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Jak HwndSource traktuje ComponentDispatcher zdarzeń  
 Jeśli <xref:System.Windows.Interop.HwndSource> jest oknem najwyższego poziomu (nie element nadrzędny HWND), będą rejestrować się za <xref:System.Windows.Interop.ComponentDispatcher>. Jeśli <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> jest wywoływane, a jeśli komunikat jest przeznaczony dla <xref:System.Windows.Interop.HwndSource> lub okno podrzędne <xref:System.Windows.Interop.HwndSource> wywołania jego <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> sekwencji zbiornik klawiatury.  
  
 Jeśli <xref:System.Windows.Interop.HwndSource> nie jest okno najwyższego poziomu (ma element nadrzędny HWND), nie będzie żadnych obsługi. Oczekiwano tylko okno najwyższego poziomu do obsługi i powinien być oknem najwyższego poziomu z obsługą zbiornik klawiatury współdziałanie sytuacja, w ramach.  
  
 Jeśli <xref:System.Windows.Interop.HwndHost.WndProc%2A> na <xref:System.Windows.Interop.HwndSource> jest wywoływana bez odpowiedniej klawiatury zbiornika wywołania metody najpierw, aplikacja będzie odbierać wyższej zdarzenia klawiatury poziomu takich jak <xref:System.Windows.UIElement.KeyDown>. Jednak żadnych metod zbiornik klawiatury zostanie wywołana, który prowadzenia pożądane klawiatury wejściowych modelu funkcje, takie jak obsługa klucza dostępu. Taka sytuacja może wystąpić, ponieważ pętli komunikatów nie prawidłowo powiadomienia odpowiednich wątku na <xref:System.Windows.Interop.ComponentDispatcher>, lub ponieważ nadrzędny HWND nie wywołała odpowiedzi zbiornik klawiatury właściwe.  
  
 Komunikat, który jest przesyłany do zbiornik klawiatury nie może być wysyłane do HWND, jeśli punkty zaczepienia dla tej wiadomości są dodawane przy użyciu <xref:System.Windows.Interop.HwndSource.AddHook%2A> metody. Komunikat może być obsługiwane na poziomie komunikatu pompa bezpośrednio i nie przesłano `DispatchMessage` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.ComponentDispatcher>  
 <xref:System.Windows.Interop.IKeyboardInputSink>  
 [WPF i współdziałanie Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Model wątkowości](../../../../docs/framework/wpf/advanced/threading-model.md)  
 [Dane wejściowe — omówienie](../../../../docs/framework/wpf/advanced/input-overview.md)
