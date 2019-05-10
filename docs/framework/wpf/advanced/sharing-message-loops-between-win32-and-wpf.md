---
title: Udostępnianie pętli komunikatów pomiędzy Win32 i WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: d2fe63ed4bdefc91e4847af799747219bd7b4a76
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611727"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Udostępnianie pętli komunikatów pomiędzy Win32 i WPF
W tym temacie opisano sposób implementacji pętlę komunikatów do współpracy z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], przy użyciu istniejących komunikatów narażenia pętli w <xref:System.Windows.Threading.Dispatcher> lub poprzez utworzenie pętli oddzielną wiadomość na [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] obok współdziałanie kodu.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher i pętli komunikatów  
 Scenariusz normalnej obsługi zdarzeń klawiatury i współdziałanie jest zaimplementowanie <xref:System.Windows.Interop.IKeyboardInputSink>, lub do podklasy z klas, które zawierają już implementację <xref:System.Windows.Interop.IKeyboardInputSink>, takich jak <xref:System.Windows.Interop.HwndSource> lub <xref:System.Windows.Interop.HwndHost>. Jednak obsługa ujścia klawiatury nie opisano kwestii możliwe komunikat pętli wszystkiego, które mogą wystąpić podczas wysyłania i odbierania wiadomości granice współdziałanie. Celu formalnego pętli komunikatów architektura [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia <xref:System.Windows.Interop.ComponentDispatcher> klasy, która definiuje prosty protokół pętlę komunikatów do wykonania.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> jest klasą statyczną, która udostępnia kilka elementów członkowskich. Zakres każdej metody niejawnie jest powiązany do wątku wywołującego. Pętla wiadomości musi wywołać niektóre z nich [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] czasami krytyczne (zgodnie z definicją w następnej sekcji).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> dostępne są zdarzenia, które mogą nasłuchiwać inne składniki (takie jak klawiatury ujścia). <xref:System.Windows.Threading.Dispatcher> Klasy wywołania wszystkich odpowiednich <xref:System.Windows.Interop.ComponentDispatcher> metod w odpowiedniej kolejności. W przypadku wdrażania własnych pętli komunikatów, Twój kod jest odpowiedzialny za wywołanie <xref:System.Windows.Interop.ComponentDispatcher> metod w podobny sposób.  
  
 Wywoływanie <xref:System.Windows.Interop.ComponentDispatcher> metod w wątku, tylko będzie wywoływać procedury obsługi zdarzeń, które zostały zarejestrowane na tym wątku.  
  
## <a name="writing-message-loops"></a>Zapisywanie pętli komunikatów  
 Oto lista kontrolna <xref:System.Windows.Interop.ComponentDispatcher> składowe, które będą używane, jeśli piszesz własnego pętli komunikatów:  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: wywołać ten element, aby wskazać, że wątek modalne pętli komunikatów dla usługi.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: ten element, aby wskazać, że wątek został przywrócony na nonmodal wywołać pętli komunikatów dla usługi.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: Twoje pętli komunikatów powinna wywołać ten element, aby wskazać, że <xref:System.Windows.Interop.ComponentDispatcher> powinny wywoływać <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> zdarzeń. <xref:System.Windows.Interop.ComponentDispatcher> nie zgłosi <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> Jeśli <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> jest `true`, ale pętli komunikatów może wywołać <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> nawet wtedy, gdy <xref:System.Windows.Interop.ComponentDispatcher> nie może odpowiadać na znajduje się w stan modalny.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: Twoje pętli komunikatów powinna wywołać ten element, aby wskazać, że nowa wiadomość jest dostępna. Zwracana wartość wskazuje, czy odbiornik do <xref:System.Windows.Interop.ComponentDispatcher> zdarzenie obsługi wiadomości. Jeśli <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> zwraca `true` (obsługiwane) Dyspozytor nie powinny nic robić dalej z komunikatem. Jeśli wartość zwracana jest `false`, Dyspozytor oczekuje się, aby wywołać [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcja `TranslateMessage`, następnie wywołać `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Za pomocą ComponentDispatcher oraz istniejące Obsługa komunikatów  
 Oto lista kontrolna <xref:System.Windows.Interop.ComponentDispatcher> elementów członkowskich będzie używać, jeśli użytkownik korzysta z używaniem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pętli komunikatów.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: zwraca, czy aplikacja stała się modalne (np. pętli komunikatów modalnych zostało wypchnięte). <xref:System.Windows.Interop.ComponentDispatcher> można śledzić ten stan, ponieważ klasa przechowuje liczbę <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> i <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> wywołania z pętli komunikatów.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> i <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> zdarzenia obowiązują standardowe reguły delegowanie wywołań. Delegaty są wywoływane w nieokreślonej kolejności, a wszystkie obiekty delegowane są wywoływane, nawet wtedy, gdy pierwszy z nich oznacza komunikat jako obsługiwane.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: wskazuje odpowiednie i efektywne czas bezczynności (%) przetwarzania (nie ma żadnych oczekujących komunikatów dla wątku). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> nie zostaną wywołane Jeśli wątek jest modalnych.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: wywoływane dla wszystkich wiadomości, które przetwarza "pompy komunikatów".  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: wywoływane dla wszystkich wiadomości, które nie były obsługiwane podczas <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Komunikat jest uznawany za obsługiwany Jeżeli po <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> zdarzeń lub <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> zdarzeń, `handled` parametr przekazywany przez odwołanie w danych zdarzenia jest `true`. Programy obsługi zdarzeń należy zignorować ten komunikat, jeśli `handled` jest `true`, ponieważ oznacza to, że najpierw obsługiwane innego programu obsługi wiadomości. Programy obsługi zdarzeń do obu zdarzeń może modyfikować komunikat. Dyspozytor powinien wysyłać komunikat zmodyfikowany i nie oryginalnej wiadomości bez zmian. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> jest dostarczane do wszystkich obiektów nasłuchujących, ale zamiar architektury jest to, że tylko najwyższego poziomu okna zawierającego HWND, jaką komunikaty docelowych należy wywołać kod w odpowiedzi na wiadomość.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Jak HwndSource traktuje ComponentDispatcher zdarzenia  
 Jeśli <xref:System.Windows.Interop.HwndSource> jest oknem najwyższego poziomu (nie nadrzędnego HWND), będą rejestrować się za pomocą <xref:System.Windows.Interop.ComponentDispatcher>. Jeśli <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> jest wywoływane, i jeśli komunikat jest przeznaczony dla <xref:System.Windows.Interop.HwndSource> lub okien podrzędnych <xref:System.Windows.Interop.HwndSource> wywołuje jego <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> klawiatury sekwencji ujścia.  
  
 Jeśli <xref:System.Windows.Interop.HwndSource> nie jest oknem najwyższego poziomu (ma element nadrzędny HWND), będzie nie obsługi. Oknem najwyższego poziomu jest oczekiwana w celu obsługi i powinien być oknem najwyższego poziomu z obsługą ujścia klawiatury w ramach dowolnego scenariusza współdziałanie.  
  
 Jeśli <xref:System.Windows.Interop.HwndHost.WndProc%2A> na <xref:System.Windows.Interop.HwndSource> nosi nazwę otrzyma bez konieczności odpowiednie skróty ujścia wywołania metody najpierw, aplikacji wyższej zdarzenia klawiatury poziomu takich jak <xref:System.Windows.UIElement.KeyDown>. Jednak żadnych metod ujścia klawiatury będzie miała nazwę, która zmierzone pożądane klawiatury modelu wejściowym funkcje, takie jak Obsługa kluczy dostępu. Może się to zdarzyć, ponieważ pętli komunikatów nie prawidłowo powiadomienia odpowiednie wątku na <xref:System.Windows.Interop.ComponentDispatcher>, lub ponieważ nadrzędny HWND nie wywołała odpowiedzi ujścia odpowiednie klawiatury.  
  
 Komunikat, który prowadzi do ujścia klawiatury nie mogą być wysyłane do HWND, jeśli dodano punkty zaczepienia dla tego komunikatu przy użyciu <xref:System.Windows.Interop.HwndSource.AddHook%2A> metody. Komunikat może być obsługiwany na poziomie pompy komunikatów bezpośrednio i nie są przesyłane do `DispatchMessage` funkcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Model wątkowości](threading-model.md)
- [Przegląd danych wejściowych](input-overview.md)
