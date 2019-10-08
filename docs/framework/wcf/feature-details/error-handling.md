---
title: Obsługa błędów
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: f6c0d676a37648678b2b726a46a6238ccc1b3331
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004890"
---
# <a name="error-handling-in-windows-communication-foundation-wcf"></a>Obsługa błędów w Windows Communication Foundation (WCF)

Gdy usługa napotka nieoczekiwany wyjątek lub błąd, istnieje wiele sposobów projektowania rozwiązania do obsługi wyjątków. Chociaż nie istnieje jedno rozwiązanie do obsługi błędów "poprawne" lub "najlepsze rozwiązanie", istnieje wiele prawidłowych ścieżek, które należy wziąć pod uwagę. Zwykle zaleca się, aby jeden Implementuj rozwiązanie hybrydowe, które łączy wiele metod z poniższej listy, w zależności od złożoności implementacji programu WCF, typu i częstotliwości wyjątków, obsługiwanego a nieobsługiwanego charakteru wyjątki i wszystkie powiązane wymagania dotyczące śledzenia, rejestrowania lub zasad.

Te rozwiązania zostały wyjaśnione dokładniej w pozostałej części tej sekcji.

## <a name="the-microsoft-enterprise-library"></a>Biblioteka Microsoft Enterprise

Blok aplikacji obsługujący wyjątek biblioteki przedsiębiorstwa firmy Microsoft pomaga zaimplementować typowe wzorce projektowania i utworzyć spójną strategię przetwarzania wyjątków, które występują we wszystkich warstwach architektury aplikacji przedsiębiorstwa. Jest ona przeznaczona do obsługi typowego kodu zawartego w instrukcjach catch w składnikach aplikacji. Zamiast powtarzania tego kodu (takiego jak kod, który rejestruje informacje o wyjątku) w identycznych blokach catch w aplikacji, blok aplikacji obsługującej wyjątki umożliwia deweloperom hermetyzację tej logiki jako obsługi wyjątków wielokrotnego użytku.

Ta biblioteka zawiera wbudowaną procedurę obsługi wyjątków kontraktu błędów. Ta procedura obsługi wyjątków została zaprojektowana do użycia w granicach usługi WCF i generuje nowy kontrakt błędu z tego wyjątku.

Bloki aplikacji dążą do uwzględnienia często używanych najlepszych rozwiązań i zapewnienia typowego podejścia do obsługi wyjątków w aplikacji. Z drugiej strony programy obsługi błędów niestandardowych i kontrakty błędów opracowane na własne mogą być również bardzo przydatne. Na przykład niestandardowe programy obsługi błędów oferują doskonałą szansę na automatyczne podwyższenie poziomu wszystkich wyjątków do FaultExceptions oraz dodanie funkcji rejestrowania do aplikacji.

Aby uzyskać więcej informacji, zobacz [Biblioteka firmy Microsoft dla przedsiębiorstw](https://docs.microsoft.com/previous-versions/msp-n-p/ff632023(v=pandp.10)).

## <a name="dealing-with-expected-exceptions"></a>Postępowanie z oczekiwanymi wyjątkami

Odpowiednim sposobem działania jest przechwycenie oczekiwanych wyjątków w każdej operacji lub w odpowiednim punkcie rozszerzalności, podjęcie decyzji o tym, czy można odzyskać z programu, i zwrócić niestandardową usterkę w elemencie FaultException @ no__t-0T >.
  
## <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Postępowanie z nieoczekiwanymi wyjątkami za pomocą IErrorHandler

Aby zająć się nieoczekiwanymi wyjątkami, zalecanym kursem akcji jest "hak" IErrorHandler. Programy obsługi błędów przechwytuje tylko wyjątki na poziomie środowiska uruchomieniowego WCF (warstwa "model usługi"), a nie w warstwie kanału. Jedynym sposobem, aby podłączyć IErrorHandler na poziomie kanału, jest utworzenie niestandardowego kanału, który nie jest zalecany w większości scenariuszy.

"Nieoczekiwany wyjątek" zazwyczaj nie ma nieodwracalnego wyjątku ani wyjątku przetwarzania; jest to raczej nieoczekiwany wyjątek użytkownika. Nieodwracalny wyjątek (na przykład wyjątek braku pamięci) — jeden zazwyczaj jest obsługiwany przez [program obsługi wyjątków modelu usług](xref:System.ServiceModel.Dispatcher.ExceptionHandler) automatycznie — nie może być zwykle obsługiwany bezpiecznie i jedyną przyczyną obsługi takiego wyjątku może być dodatkowe rejestrowanie lub zwrócenie standardowego wyjątku do klienta programu. Wyjątek przetwarzania występuje podczas przetwarzania komunikatu — na przykład na poziomie serializacji, kodera lub programu formatującego — zwykle nie można go obsługiwać w IErrorHandler, ponieważ jest on zwykle zbyt wczesny lub zbyt późno, aby program obsługi błędów mógł interweniować przez czas wystąpienia tych wyjątków. Podobnie wyjątki transportowe nie mogą być obsługiwane w IErrorHandler.

Za pomocą IErrorHandler można jawnie kontrolować zachowanie aplikacji w przypadku zgłoszenia wyjątku. Możesz:  

1. Zdecyduj, czy wysłać błąd do klienta.

2. Zastąp wyjątek błędem.

3. Zastąp błąd innym błędem.

4. Wykonaj rejestrowanie lub śledzenie.

5. Wykonywanie innych działań niestandardowych.

Jeden z nich może zainstalować niestandardową procedurę obsługi błędów, dodając ją do właściwości ErrorHandlers dla dyspozytorów kanałów dla usługi.  Możliwe jest posiadanie więcej niż jednego programu obsługi błędów i są one wywoływane w kolejności, w jakiej są dodawane do tej kolekcji.

IErrorHandler. ProvideFault kontroluje komunikat o błędzie, który jest wysyłany do klienta. Ta metoda jest wywoływana niezależnie od typu wyjątku zgłoszonego przez operację w usłudze. Jeśli żadna operacja nie zostanie wykonana w tym miejscu, WCF przyjmie zachowanie domyślne i kontynuuje tak, jakby nie było żadnych niestandardowych programów obsługi błędów.

Jednym z obszarów, które mogą być używane w tym podejściu, jest utworzenie centralnego miejsca do konwertowania wyjątków na błędy przed ich wysłaniem do klienta (bez względu na to, że wystąpienie nie jest usuwane, a kanał nie jest przenoszony do stanu błędu).

Metoda IErrorHandler. HandleError jest zwykle używana do implementowania zachowań związanych z błędami, takich jak rejestrowanie błędów, powiadomienia systemowe, zamykanie aplikacji itp. IErrorHandler. HandleError można wywołać w wielu miejscach wewnątrz usługi i w zależności od tego, gdzie wystąpił błąd, Metoda HandleError może lub nie może być wywołana przez ten sam wątek co operacja; w związku z tym nie są wykonywane żadne gwarancje.

## <a name="dealing-with-exceptions-outside-wcf"></a>Postępowanie z wyjątkami poza WCF

Często wyjątki konfiguracji, wyjątki parametrów połączenia bazy danych i inne podobne wyjątki mogą wystąpić w kontekście aplikacji WCF, ale same nie są wyjątkami spowodowanymi przez model usług lub samą usługę sieci Web. Te wyjątki są "regularnymi" wyjątkami zewnętrznymi względem usługi sieci Web i powinny być obsługiwane tylko w przypadku, gdy inne wyjątki zewnętrzne w środowisku mają być obsługiwane.

## <a name="tracing-exceptions"></a>Śledzenie wyjątków

Śledzenie jest jedynym miejscem "catch-all", gdzie jeden może potencjalnie zobaczyć wszystkie wyjątki. Aby uzyskać więcej informacji na temat śledzenia i rejestrowania wyjątków, zobacz Śledzenie i rejestrowanie.

## <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Błędy szablonów identyfikatorów URI podczas korzystania z obiektu WebGetAttribute i WebInvokeAttribute

Atrybuty WebGet i WebInvoke umożliwiają określenie szablonu identyfikatora URI, który mapuje składniki adresu żądania na parametry operacji. Na przykład szablon URI "Pogoda/{State}/{miasto}" mapuje adres żądania na tokeny literału, nazwany stan parametru i parametr o nazwie miasto. Te parametry mogą być następnie powiązane według nazwy z niektórymi parametrami formalnymi operacji.

Parametry szablonu są wyświetlane w postaci ciągów w identyfikatorze URI, podczas gdy formalne parametry kontraktu z typem mogą być typu niebędącego ciągiem. W związku z tym przed wywołaniem operacji należy wykonać konwersję. [Tabela formatów konwersji](wcf-web-http-programming-model-overview.md) jest dostępna.

Jeśli jednak konwersja nie powiedzie się, nie ma możliwości poinformowania o tym, że coś się nie stało. Konwersja typu zamiast tego ma miejsce w postaci niepowodzenia wysyłania.

Błąd wysyłania konwersji typu można sprawdzić tak samo jak w przypadku wielu innych typów niepowodzeń wysyłania, instalując procedurę obsługi błędów. Punkt rozszerzalności IErrorHandler jest wywoływany w celu obsługi wyjątków na poziomie usług. Z tego miejsca odpowiedź ma być wysyłana z powrotem do obiektu wywołującego — można również wybrać dowolne zadania niestandardowe i raportowanie —.

## <a name="see-also"></a>Zobacz także

- [Podstawy programowania przy użyciu programu WCF](../basic-wcf-programming.md)
