---
title: Obsługa błędów
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: 548d93e63440e256ddb54c3ca792a49817c9b059
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452852"
---
# <a name="error-handling"></a>Obsługa błędów
## <a name="error-handling-in-windows-communication-foundation"></a>Obsługa błędów w programie Windows Communication Foundation  
 Gdy usługa napotka nieoczekiwany wyjątek lub błąd, istnieje wiele sposobów, aby zaprojektować rozwiązanie do obsługi wyjątków. Gdy nie ma jednego "poprawny" lub "najlepsze praktyki" obsługi błędów rozwiązania, istnieje wiele ścieżek prawidłowy, aby móc wziąć pod uwagę. Zwykle zaleca się, że jeden wdrożyć rozwiązanie hybrydowe, które łączy wiele metod z listy poniżej, w zależności od złożoności implementacji usługi WCF, rodzaj i częstotliwość wyjątki obsługiwane, a nieobsługiwany rodzaj wyjątki i wszystkie skojarzone śledzenie, logowania lub wymagania zasad.  
  
 Te rozwiązania zostały wyjaśnione bardziej szczegółowo w dalszej części tej sekcji.  
  
### <a name="the-microsoft-enterprise-library"></a>Biblioteka firmy Microsoft dla przedsiębiorstw  
 Microsoft Enterprise Library obsługi aplikacji bloku wyjątków pomaga w realizacji typowych wzorców projektowania i tworzenia spójnej strategii przetwarzania wyjątków, które występują w wszystkie warstwy architektury aplikacji przedsiębiorstwa. Jest on przeznaczony do obsługi typowego kod zawarty w instrukcji catch w składników aplikacji. Zamiast powtarzania tego kodu (na przykład kod, który rejestruje informacje o wyjątku) w blokach catch identyczne w całej aplikacji, bloku aplikacji obsługi wyjątków umożliwia deweloperom hermetyzacji tę logikę jako programów obsługi wyjątków do ponownego użycia.  
  
 Ta biblioteka zawiera out-of--box program obsługi wyjątku kontraktu błędów. Ten program obsługi wyjątków jest przeznaczony do użytku na granicach usługi Windows® Communication Foundation (WCF), a następnie generuje nowy kontrakt błędu z wyjątku.  
  
 Bloki aplikacji Staraj się zastosować powszechnie używane najlepsze rozwiązania i podaj typowym podejściem wyjątków, obsługa w całej aplikacji. Z drugiej strony procedury obsługi błędów niestandardowych oraz umów błędów opracowane na podstawie własnych może również być bardzo przydatne. Na przykład obsługi błędu niestandardowego zapewniają doskonała okazja automatycznie Przenieś wszystkie wyjątki FaultExceptions, a także dodawanie funkcji logowania do aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [Microsoft Enterprise Library](https://msdn.microsoft.com/library/ff632023.aspx).  
  
### <a name="dealing-with-expected-exceptions"></a>Zajmowanie się oczekiwane wyjątki  
 Prawidłowego sposobu działania jest catch oczekiwane wyjątki w każdej operacji lub punkt odpowiednich rozszerzeń, zdecyduj, czy ich można odzyskać z zwrócić prawidłowego błędów niestandardowych w FaultException —\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Obsługa wyjątków nieoczekiwany, za pomocą IErrorHandler  
 Aby poradzić sobie z nieoczekiwane wyjątki, zalecany sposób postępowania jest "dołączyć" IErrorHandler. Procedury obsługi błędów tylko przechwytywać wyjątków, na poziomie środowiska uruchomieniowego usługi WCF (warstwa "model usługi"), a nie w warstwie kanału. Jedynym sposobem na utworzenie punktu zaczepienia IErrorHandler na poziomie kanału jest Utwórz kanał niestandardowy, który nie jest zalecane w większości scenariuszy.  
  
 "Nieoczekiwany wyjątek" ogólnie nie jest nieodwracalny wyjątek ani wyjątku przetwarzania; jest zamiast tego użytkownik nieoczekiwany wyjątek. Wystąpił nieodwracalny wyjątek (na przykład wyjątek braku pamięci) — jeden ogólnie obsługiwane przez [Obsługa wyjątków modelu usługi](xref:System.ServiceModel.Dispatcher.ExceptionHandler) automatycznie — nie jest ogólnie można obsługiwać poprawnie, a jedyny przypadek, kiedy do obsługi takiego wyjątku może być w ogóle wykonaj dodatkowe rejestrowanie lub w celu zwrócenia standardowych wyjątków do klienta. Wystąpi wyjątek przetwarzania w przetwarzanie komunikatu — na przykład poziomie serializacji, koder lub program formatujący — ogólnie nie mogą być obsługiwane na IErrorHandler, ponieważ jest zazwyczaj zbyt wcześnie albo za późno obsługi błędów interweniować przez razem te wyjątki występują. Podobnie transportowanie wyjątków nie mogą być obsługiwane w IErrorHandler.  
  
 Za pomocą IErrorHandler można jawnie kontrolować zachowanie aplikacji, gdy wyjątek jest zgłaszany. Użytkownik może:  
  
1.  Zdecyduj, czy chce wysłać błędów do klienta  
  
2.  Zamień wyjątek po awarii  
  
3.  Zamień na inną awarię usterki  
  
4.  Wykonać rejestrowania i śledzenia  
  
5.  Wykonaj innych działania niestandardowe  
  
 Jeden można zainstalować obsługi błędów niestandardowych, dodając ją do właściwości ErrorHandlers dyspozytorów kanału dla usługi.  Może mieć więcej niż jedną procedurę obsługi błędów i są one wywoływane w kolejności, w której są dodane do tej kolekcji.  
  
 IErrorHandler.ProvideFault Określa komunikat o błędzie, który jest wysyłany do klienta. Ta metoda jest wywoływana bez względu na typ wyjątku zgłoszonego przez operację w usłudze. Jeśli żadna operacja jest wykonywana w tym miejscu, WCF zakłada jej zachowanie domyślne i jest kontynuowane tak, jakby było nie obsługi błędów niestandardowych.  
  
 Jeden obszar, że być może można używać tego podejścia jest, gdy chcesz utworzyć centralne miejsce do konwertowania wyjątki na błędy przed wysłaniem ich do klienta (zapewnienie, że nie usunięto alokowanego wystąpienia i kanał nie jest przenoszony do stanu Faulted).  
  
 Metoda IErrorHandler.HandleError zwykle jest używana do zaimplementowania błąd związany zachowań, takich jak rejestrowanie, błędów powiadomień systemowych, zamykanie aplikacji itp. IErrorHandler.HandleError mogą być wywoływane w wielu miejscach w usłudze i w zależności od tego, gdzie jest zgłaszany błąd, metoda HandleError może lub nie można wywołać w tym samym wątku, ponieważ operacja; w związku z tym stają się żadnych gwarancji.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Obsługa wyjątków poza WCF  
 Często konfiguracji wyjątków, wyjątki ciąg połączenia bazy danych i inne podobne wyjątki mogą wystąpić w kontekście aplikacji WCF, ale same nie są wyjątków spowodowanych przez model usługi lub samej usługi sieci web. Te wyjątki wyjątków "regularne" zewnętrzne w stosunku do usługi sieci web i powinno zostać obsłużone tak, jak powinny być traktowane innych zewnętrznych wyjątków w środowisku.  
  
### <a name="tracing-exceptions"></a>Śledzenie wyjątków  
 Śledzenie jest miejsce tylko "wychwytywania", w której jeden potencjalnie zobaczyć wszystkie wyjątki. Aby uzyskać więcej informacji na temat śledzenia i rejestrowaniem wyjątków Zobacz Śledzenie i rejestrowanie.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Identyfikator URI szablonu błędy podczas korzystania z WebGetAttribute i WebInvokeAttribute  
 Atrybuty WebGet i WebInvoke umożliwiają określenie szablon identyfikatora URI, który mapuje składniki adres żądania parametry operacji. Na przykład szablon URI "pogoda / {state} / {Miasto}" map adres żądania do tokenów literałów, parametr o nazwie stanu i parametr o nazwie miasta. Te parametry mogą następnie powiązać według nazwy niektórych parametrów formalnych operacji.  
  
 Parametry szablonu są wyświetlane w postaci ciągów w identyfikatorze URI parametrów formalnych wpisane zamówienia może być typów innych niż ciąg. W związku z tym konwersja wymaga ma miejsce przed operację może być wywołana. A [tabeli konwersji formatów](wcf-web-http-programming-model-overview.md) jest dostępna.  
  
 Jeśli konwersja nie powiedzie się, następnie istnieje jednak sposób kontynuowania operacji, o których wiadomo, że Niestety, wystąpił problem. Konwersja typu prezentuje zamiast tego w postaci błędów wysyłania.  
  
 Błąd wysyłania konwersji typów może być taki sam, jak wiele innych typów błędów wysyłania sprawdził, instalując program obsługi błędów. Punkt rozszerzeń IErrorHandler nosi nazwę do obsługi wyjątków na poziomie usługi. W efekcie odpowiedzi wysyłane z powrotem do obiektu wywołującego — jak również wykonują wszelkie niestandardowe zadania i raportowanie — może zostać wybrany.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy programowania przy użyciu programu WCF](../basic-wcf-programming.md)
