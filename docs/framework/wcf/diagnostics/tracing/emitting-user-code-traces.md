---
title: Emitowanie danych śledzenia elementu User-Code
ms.date: 03/30/2017
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
ms.openlocfilehash: e8b2031165a83e24ba15a2fcf847a170f47e696a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589295"
---
# <a name="emitting-user-code-traces"></a>Emitowanie danych śledzenia elementu User-Code

Oprócz włączania śledzenia w konfiguracji w celu zbierania danych Instrumentacji generowanych przez Windows Communication Foundation (WCF), można również emitować dane śledzenia programowo w kodzie użytkownika. W ten sposób można aktywnie tworzyć dane instrumentacji, które można zapoznania później do celów diagnostycznych. W tym temacie omówiono, jak to zrobić.

Ponadto [rozszerzanie](../../samples/extending-tracing.md) przykładu śledzenia obejmuje cały kod zademonstrowany w poniższych sekcjach.

## <a name="creating-a-trace-source"></a>Tworzenie źródła śledzenia

Możesz użyć poniższego kodu, aby utworzyć źródło śledzenia użytkownika.

```csharp
TraceSource ts = new TraceSource("myUserTraceSource");
```

## <a name="creating-activities"></a>Tworzenie działań

Działania są logiczną jednostką przetwarzania. Można utworzyć jedno działanie dla każdej głównej jednostki przetwarzania, w której mają być zgrupowane dane śledzenia. Na przykład można utworzyć jedno działanie dla każdego żądania do usługi. Aby to zrobić, wykonaj następujące czynności.

1. Zapisz identyfikator działania w zakresie.

2. Utwórz nowy identyfikator działania.

3. Przenieś z działania w zakresie do nowego, Ustaw nowe działanie w zakresie i Emituj śledzenie uruchamiania dla tego działania.

Poniższy kod demonstruje, jak to zrobić.

```csharp
Guid oldID = Trace.CorrelationManager.ActivityId;
Guid traceID = Guid.NewGuid();
ts.TraceTransfer(0, "transfer", traceID);
Trace.CorrelationManager.ActivityId = traceID; // Trace is static
ts.TraceEvent(TraceEventType.Start, 0, "Add request");
```

## <a name="emitting-traces-within-a-user-activity"></a>Emitowanie śladów w działaniu użytkownika

Poniższy kod emituje ślady w działaniu użytkownika.

```csharp
double value1 = 100.00D;
double value2 = 15.99D;
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);
double result = client.Add(value1, value2);
ts.TraceInformation("Client receives Add response '" + result + "'");
```

## <a name="stopping-the-activities"></a>Zatrzymywanie działań

Aby zatrzymać działania, prześlij ponownie do starego działania, Zatrzymaj bieżący identyfikator działania i zresetuj stary identyfikator działania w zakresie.

Poniższy kod demonstruje, jak to zrobić.

```csharp
ts.TraceTransfer(0, "transfer", oldID);
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");
Trace.CorrelationManager.ActivityId = oldID;
```

## <a name="propagating-the-activity-id-to-a-service"></a>Propagowanie identyfikatora działania do usługi

Jeśli ustawisz `propagateActivity` atrybut na `true` dla `System.ServiceModel` źródła śledzenia zarówno w pliku konfiguracji klienta, jak i usługi, przetwarzanie usługi dla żądania Add będzie odbywać się w tym samym działaniu jak w przypadku tego, co zostało zdefiniowane w kliencie. Jeśli usługa definiuje własne działania i transfery, ślady usług nie są wyświetlane w działaniu propagowanym przez klienta. Zamiast tego pojawiają się one w działaniu skorelowanym przez dane śledzenia przeniesienia do działania, którego identyfikator jest propagowany przez klienta.

> [!NOTE]
> Jeśli `propagateActivity` atrybut jest ustawiony na `true` zarówno dla klienta, jak i usługi, działanie otoczenia w zakresie operacji usługi jest ustawiane przez funkcję WCF.

Można użyć poniższego kodu, aby sprawdzić, czy działanie zostało ustawione w zakresie przez WCF.

```csharp
// Check if an activity was set in scope by WCF, if it was
// propagated from the client. If not, ( ambient activity is
// equal to Guid.Empty), create a new one.
if(Trace.CorrelationManager.ActivityId == Guid.Empty)
{
    Guid newGuid = Guid.NewGuid();
    Trace.CorrelationManager.ActivityId = newGuid;
}
// Emit your Start trace.
ts.TraceEvent(TraceEventType.Start, 0, "Add Activity");

// Emit the processing traces for that request.
serviceTs.TraceInformation("Service receives Add "
                            + n1 + ", " + n2);
// double result = n1 + n2;
serviceTs.TraceInformation("Service sends Add result" + result);

// Emit the Stop trace and exit the method scope.
ts.TraceEvent(TraceEventType.Stop, 0, "Add Activity");
// return result;
```

## <a name="tracing-exceptions-thrown-in-code"></a>Śledzenie wyjątków zgłoszonych w kodzie

Gdy zgłaszasz wyjątek w kodzie, możesz również śledzić wyjątek na poziomie ostrzeżenia lub przy użyciu następującego kodu.

```csharp
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");
```

## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Wyświetlanie śladów użytkowników w narzędziu Podgląd śledzenia usługi

Ta sekcja zawiera zrzuty ekranu śledzenia wygenerowane przez uruchomienie przykładowego [śledzenia](../../samples/extending-tracing.md) , gdy jest wyświetlany za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md).

Na poniższym diagramie jest zaznaczone działanie "Dodaj żądanie" utworzone wcześniej w panelu po lewej stronie. Jest on wyświetlany na trzy inne działania operacji matematycznych (dzielenie, odejmowanie, mnożenie) stanowiące program klienta aplikacji. Kod użytkownika definiuje jedno nowe działanie dla każdej operacji, aby odizolować potencjalne wystąpienia błędów w różnych żądaniach.

Aby zademonstrować użycie transferów w przykładzie [Rozszerzanie śledzenia](../../samples/extending-tracing.md) , tworzone jest również działanie kalkulatora, które hermetyzuje cztery żądania operacji. Dla każdego żądania istnieje transfer z powrotem i z działania kalkulatora do działania żądania (Trace jest wyróżniony w prawym górnym panelu na rysunku).

Po wybraniu działania w lewym panelu ślady zawarte w tym działaniu są wyświetlane w prawym górnym panelu. Jeśli `propagateActivity` jest w `true` każdym punkcie końcowym w ścieżce żądania, ślady w działaniu żądania pochodzą ze wszystkich procesów, które uczestniczą w żądaniu. W tym przykładzie można zobaczyć ślady zarówno klienta, jak i usługi w czwartej kolumnie panelu.

To działanie pokazuje następującą kolejność przetwarzania:

1. Klient wysyła komunikat do dodania.

2. Usługa otrzymuje komunikat żądania dodania.

3. Usługa wysyła odpowiedź na dodanie.

4. Klient otrzymuje odpowiedź na dodanie.

Wszystkie te ślady zostały emitowane na poziomie informacji. Kliknięcie śladu w prawym górnym okienku powoduje wyświetlenie szczegółów tego śladu w prawym dolnym panelu.

Na poniższym diagramie przedstawiono również dane śledzenia transferu z i do działania kalkulatora, a także dwie pary uruchamiania i zatrzymywania śledzenia na żądanie, jeden dla klienta i jeden dla usługi (po jednym dla każdego źródła śledzenia).

![Podgląd śledzenia: emitowanie śladów kodu&#45;użytkownika](media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd") Lista działań według czasu utworzenia (lewy panel) i ich działań zagnieżdżonych (Panel w prawym górnym rogu)

Jeśli kod usługi zgłasza wyjątek, który powoduje, że klient może zgłosić się również (na przykład gdy klient nie otrzymał odpowiedzi na żądanie), zarówno ostrzeżenie usługi, jak i komunikaty o błędach są wykonywane w tym samym działaniu dla bezpośredniej korelacji. Na poniższej ilustracji usługa zgłasza wyjątek informujący o tym, że usługa odmówi, aby przetworzyć to żądanie w kodzie użytkownika ". Klient zgłasza również wyjątek informujący o tym, że serwer nie może przetworzyć żądania z powodu błędu wewnętrznego. "

Poniższe obrazy pokazują, że błędy między punktami końcowymi danego żądania pojawiają się w tym samym działaniu, jeśli identyfikator działania żądania został rozpropagowany:

![Zrzut ekranu pokazujący błędy w punktach końcowych dla danego żądania.](./media/emitting-user-code-traces/trace-viewer-endpoint-errors.gif)

Dwukrotne kliknięcie w lewym panelu działania operacji pomnóż powoduje wyświetlenie poniższego wykresu z śladami działania pomnożenie dla każdego procesu. Zobaczysz ostrzeżenie podczas pierwszego wystąpienia usługi (zgłoszono wyjątek), po którym następuje ostrzeżenia i błędy na kliencie, ponieważ nie można przetworzyć żądania. W związku z tym możemy oznaczać relację błędu przyczynowego między punktami końcowymi i utworzyć główną przyczynę błędu.

Na poniższej ilustracji przedstawiono widok wykresu korelacji błędów:

![Zrzut ekranu pokazujący widok wykresu korelacji błędów.](./media/emitting-user-code-traces/trace-viewer-error-correlation.gif)

Aby uzyskać poprzednie dane śledzenia, należy ustawić `ActivityTracing` dla źródeł śledzenia użytkownika i `propagateActivity=true` dla `System.ServiceModel` źródła śledzenia. Nie ustawiono `ActivityTracing` `System.ServiceModel` źródła śledzenia, aby umożliwić propagację działania kodu użytkownika na kod użytkownika. (Gdy śledzenie aktywności ServiceModel jest włączone, identyfikator działania zdefiniowany w kliencie nie jest propagowany do kodu użytkownika usługi; Transfery są jednak skorelowane z działaniami kodu użytkownika klienta i usługi do pośrednich działań WCF.

Definiowanie działań i propagowanie identyfikatora działania umożliwia nam wykonywanie bezpośrednich korelacji błędów w punktach końcowych. Dzięki temu możemy szybciej zlokalizować główną przyczynę błędu.

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie śledzenia](../../samples/extending-tracing.md)
