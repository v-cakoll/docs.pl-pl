---
title: Obsługa błędów
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: ffcc817eb463a1787972bc9c4ae1434ff74f7bb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495671"
---
# <a name="error-handling"></a>Obsługa błędów
## <a name="error-handling-in-windows-communication-foundation"></a>Obsługa błędów w systemie Windows Communication Foundation  
 Gdy usługa napotka nieoczekiwany wyjątek lub błędu, istnieje wiele sposobów, aby zaprojektować rozwiązanie do obsługi wyjątków. Gdy nie jest jednym "Popraw" ani "najlepsze praktyki" Obsługa błędów rozwiązania, istnieje wiele ścieżek prawidłowy dla jednego wziąć pod uwagę. Zwykle zaleca się, że jeden wdrożyć rozwiązanie hybrydowe, które łączy wiele metod z listy poniżej, w zależności od złożoności implementacji usługi WCF, typ i częstotliwość wyjątków obsłużonych a nieobsługiwany rodzaj wyjątki i wszystkie skojarzone śledzenie, logowania lub wymagania dotyczące zasad.  
  
 Te rozwiązania głębsze opisano w dalszej części tej sekcji.  
  
### <a name="the-microsoft-enterprise-library"></a>Biblioteka Microsoft Enterprise  
 Microsoft Enterprise biblioteki obsługi aplikacji bloku wyjątków ułatwia wdrożenie typowe wzorce projektowe oraz utworzenia spójnej strategii przetwarzania wyjątków, które występują w wszystkie warstwy architektury aplikacji przedsiębiorstwa. Zaprojektowano go do obsługi typowy kod źródłowy znajdujący się w instrukcji catch w składników aplikacji. Zamiast tego kodu (na przykład kodu, który rejestruje informacje o wyjątku) należy powtórzyć w blokach catch identyczne w całej aplikacji, bloku aplikacji obsługi wyjątków umożliwia deweloperom Hermetyzowanie tę logikę jako programów obsługi wyjątków do ponownego użycia.  
  
 Ta biblioteka zawiera out-of--box obsługi wyjątków kontraktu błędów. Ten program obsługi wyjątku jest przeznaczony do użytku na granicach usługi Windows® Communication Foundation (WCF), a następnie generuje nowy kontrakt błędu z wyjątkiem.  
  
 Bloki aplikacja Staraj się zastosować często używane najlepszych rozwiązań i podaj typowym podejściem wyjątków, obsługa w całej aplikacji. Z drugiej strony programy obsługi błędów niestandardowych i kontrakty usterki utworzone przy użyciu własnych może również być bardzo przydatne. Na przykład programy obsługi błędów niestandardowych Podaj doskonała okazja automatycznie Przenieś wszystkie wyjątki FaultExceptions i dodać możliwości rejestrowania zdarzeń do aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [biblioteki Microsoft Enterprise](http://msdn.microsoft.com/library/ff632023.aspx).  
  
### <a name="dealing-with-expected-exceptions"></a>Zajmujących się oczekiwane wyjątki  
 Jest właściwy sposobu działania catch oczekiwane wyjątki w każdej operacji punkt odpowiednich rozszerzeń, zdecydować, czy ich można odzyskać od i zwróć prawidłowego błędów niestandardowych zgłoszenie wyjątku FaultException\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Zajmujących się nieoczekiwane wyjątków przy użyciu interfejsy IErrorHandler  
 Na wypadek nieoczekiwanych wyjątków, zalecany sposób postępowania jest "Połącz" interfejsy IErrorHandler. Programy obsługi błędów tylko przechwytywanie wyjątków na poziomie środowiska uruchomieniowego WCF (warstwa "model usługi"), a nie w warstwie kanału. Jedynym sposobem na utworzenie punktu zaczepienia interfejsy IErrorHandler na poziomie kanału jest tworzenie niestandardowych kanału, co nie jest zalecane w większości przypadków.  
  
 "Nieoczekiwany wyjątek" zazwyczaj nie jest wystąpił nieodwracalny wyjątek ani wyjątku przetwarzania; jest, zamiast tego użytkownik nieoczekiwany wyjątek. Wystąpił nieodwracalny wyjątek (np. wyjątek braku pamięci) — jeden ogólnie obsługiwane przez [obsługi wyjątków modelu usługi](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) automatycznie — nie ogólnie można obsługiwać poprawnie i tylko Przyczyna do obsługi takich wyjątku może być w ogóle wykonaj dodatkowe rejestrowanie Aby przywrócić standardowego wyjątek do klienta. Wyjątek przetwarzania występuje podczas przetwarzania komunikatu — na przykład na poziomie elementu formatującego — serializacji, koder lub zazwyczaj nie mogą być obsługiwane na interfejsy IErrorHandler, ponieważ jest zazwyczaj zbyt wcześnie albo za późno interweniować przez program obsługi błędów czas, będą wykonywane te wyjątki. Podobnie transportowanie wyjątków nie mogą być obsługiwane na interfejsy IErrorHandler.  
  
 Z interfejsy IErrorHandler można jawnie kontrolować zachowanie aplikacji, gdy wyjątek. Użytkownik może:  
  
1.  Zdecyduj, czy należy wysłać do klienta błąd  
  
2.  Zamień na błąd wystąpił wyjątek  
  
3.  Zamień na inny błąd usterki  
  
4.  Wykonaj rejestrowania i śledzenia  
  
5.  Wykonywanie innych czynności niestandardowe  
  
 Co można zainstalować obsługi błędów niestandardowych, dodając ją do właściwości ErrorHandlers dyspozytorów kanał dla usługi.  Użytkownik może mieć więcej niż jeden program obsługi błędów i są wywoływane w kolejności, są one dodawane do tej kolekcji.  
  
 IErrorHandler.ProvideFault Określa komunikat o błędzie, który jest wysyłany do klienta. Ta metoda jest wywoływana bez względu na typ wyjątku zgłoszonego przez operacji w usłudze. Jeśli żadna operacja jest wykonywana w tym miejscu, WCF zakłada jego zachowania domyślnego i kontynuuje tak, jakby nie było żadnych programy obsługi błędów niestandardowych w miejscu.  
  
 Jednego obszaru można tego podejścia być może użyć jest, gdy chcesz utworzyć centralne miejsce do konwertowania wyjątków na błędy przed ich wysłaniem do klienta (zapewnienie, że wystąpienie nie zostanie usunięty, i kanał nie jest przenoszony do stan końcowy: Faulted).  
  
 Metoda IErrorHandler.HandleError zwykle jest używana do zaimplementowania błąd związany zachowań, takich jak rejestrowanie, błędów powiadomień systemowych, zamykanie aplikacji itp. IErrorHandler.HandleError można wywołać w wielu miejscach wewnątrz usługi, a w zależności od tego, gdzie zostanie zgłoszony błąd, metoda HandleError może lub nie można wywołać w tym samym wątku, co operację; gwarancje nie zostały wprowadzone w tym zakresie.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Postępowania z wyjątkami poza WCF  
 Często, może wystąpić w kontekście aplikacji WCF konfiguracji wyjątków, wyjątki ciąg połączenia bazy danych i inne podobne wyjątki, ale same nie są wyjątki spowodowane przez model usługi lub samej usługi sieci web. Te wyjątki są zewnętrzne względem usługi sieci web "regularne" wyjątki, a powinien zostać obsłużony, podobnie jak inne zewnętrznych wyjątki w środowisku powinny być traktowane.  
  
### <a name="tracing-exceptions"></a>Śledzenie wyjątków  
 Śledzenie jest miejsce tylko "wychwytywania", której jeden potencjalnie zobaczyć wszystkie wyjątki. Aby uzyskać więcej informacji dotyczących śledzenia i rejestrowaniem wyjątków Zobacz Śledzenie i rejestrowanie.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Identyfikator URI szablonu błędy podczas korzystania z obiektu WebGetAttribute i WebInvokeAttribute  
 Atrybuty WebGet i WebInvoke umożliwiają Określ szablon identyfikatora URI, który mapuje składniki adresu żądania do parametrów operacji. Na przykład szablon identyfikatora URI "pogody / {stanu} / {Miasto}" mapuje adres żądania do tokenów literałów, parametr o nazwie stanu i parametr o nazwie miasta. Te parametry mogą następnie powiązać według nazwy niektórych parametrów formalnych operacji.  
  
 Parametry szablonu są wyświetlane w postaci ciągów w identyfikatorze URI podczas parametrów formalnych typu kontraktu może być typów innych niż ciąg. W związku z tym konwersji ma miejsce przed operację można wywołać. A [tabeli konwersji formatów](http://msdn.microsoft.com/library/bb412172.aspx) jest dostępna.  
  
 Jednak jeśli konwersji nie powiedzie się, to nie ma sposób umożliwić wiedzieć, że coś niepowodzenia operacji. Konwersja typów powierzchni zamiast tego w formie Błąd wysyłania.  
  
 Błąd wysyłania konwersji typów może być taki sam, jak wiele innych typów błędy wysyłania inspekcji, instalując program obsługi błędów. Punkt rozszerzeń interfejsy IErrorHandler nazywa się do obsługi wyjątków na poziomie usługi. Z tego miejsca odpowiedzi na wysłane z powrotem do wywołującego — oraz wykonywać żadnych niestandardowych zadań i raportowania — może zostać wybrany.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów podstawowe usługi WCF](http://msdn.microsoft.com/library/gg281715.aspx)
