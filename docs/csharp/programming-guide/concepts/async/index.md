---
title: 'Programowanie asynchroniczne w języku C #'
description: Przegląd obsługi języka Języka C# dla programowania asynchronicznego przy użyciu async, await, Task i Task<T>
ms.date: 03/18/2019
ms.openlocfilehash: 4cbbff0f2c48f0ec2f8befa234ea5023465a1c5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169912"
---
# <a name="asynchronous-programming-with-async-and-await"></a>Programowanie asynchroniczne przy użyciu elementów async i await

Task asynchroniczny model programowania (TAP) zapewnia abstrakcję za pomocą kodu asynchronicznego. Piszesz kod jako sekwencję instrukcji, tak jak zawsze. Można odczytać ten kod tak, jakby każda instrukcja kończy się przed rozpoczęciem następnego. Kompilator wykonuje szereg przekształceń, ponieważ niektóre z tych <xref:System.Threading.Tasks.Task> instrukcji może rozpocząć pracę i zwrócić a, który reprezentuje trwającej pracy.

To jest cel tej składni: włącz kod, który odczytuje jak sekwencja instrukcji, ale jest wykonywany w znacznie bardziej skomplikowanej kolejności na podstawie zewnętrznej alokacji zasobów i po zakończeniu zadań. Jest to analogiczne do tego, jak ludzie udzielają instrukcji dla procesów, które zawierają zadania asynchroniczne. W tym artykule użyjesz przykładu instrukcji dotyczących tworzenia śniadania, aby zobaczyć, jak `async` słowa kluczowe i `await` ułatwiają rozumowanie kodu zawierającego serię instrukcji asynchronicznych. Chcesz napisać instrukcje coś w rodzaju poniższej listy, aby wyjaśnić, jak zrobić śniadanie:

1. Wlać filiżankę kawy.
1. Podgrzać patelnię, a następnie smażyć dwa jajka.
1. Smażyć trzy plasterki boczku.
1. Toast dwa kawałki chleba.
1. Dodaj masło i dżem do tosty.
1. Wlać szklankę soku pomarańczowego.

Jeśli masz doświadczenie z gotowaniem, należy wykonać te instrukcje **asynchronicznie**. Zacząłbyś rozgrzewać patelnię do jaj, a następnie rozpocząć bekon. Włożyłeś chleb do tostera, a potem zacząłeś jajka. Na każdym etapie procesu należy rozpocząć zadanie, a następnie zwrócić uwagę na zadania, które są gotowe do uwagi.

Gotowanie śniadania jest dobrym przykładem pracy asynchronicznej, która nie jest równoległa. Jedna osoba (lub wątek) może obsłużyć wszystkie te zadania. Kontynuując analogię śniadania, jedna osoba może zrobić śniadanie asynchronicznie, rozpoczynając następne zadanie przed zakończeniem pierwszego. Gotowanie postępuje niezależnie od tego, czy ktoś go obserwuje. Jak tylko zaczniesz rozgrzewać patelnię do jaj, możesz rozpocząć smażenie boczku. Po rozpoczęciu boczku można umieścić chleb w tosterze.

Dla algorytmu równoległego, trzeba wielu kucharzy (lub wątków). Można by zrobić jajka, jeden bekon, i tak dalej. Każdy z nich będzie koncentrować się tylko na tym jednym zadaniu. Każdy kucharz (lub nici) będzie zablokowany synchronicznie czekając na boczek, aby być gotowym do przerzucenia, lub toast pop.

Teraz należy wziąć pod uwagę te same instrukcje napisane jako instrukcje C#:

[!code-csharp[SynchronousBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-starter/Program.cs#Main)]

Komputery nie interpretują tych instrukcji w taki sam sposób, jak ludzie. Komputer zablokuje każdą instrukcję, dopóki praca nie zostanie zakończona przed przejściem do następnej instrukcji. To tworzy niesatysfakcjonujące śniadanie. Późniejsze zadania nie zostaną uruchomione, dopóki nie zostaną ukończone wcześniejsze zadania. Stworzenie śniadania zajęłoby znacznie więcej czasu, a niektóre produkty stałyby się zimne przed serwem.

Jeśli chcesz, aby komputer wykonywał powyższe instrukcje asynchronicznie, musisz napisać kod asynchroniczny.

Te obawy są ważne dla programów, które piszesz dzisiaj. Podczas pisania programów klienckich, chcesz interfejsu użytkownika, aby reagować na dane wejściowe użytkownika. Aplikacja nie powinna sprawiać, że telefon jest wyświetlany na zablokowanej, podczas pobierania danych z sieci Web. Podczas pisania programów serwerowych nie chcesz blokować wątków. Te wątki mogą obsługiwać inne żądania. Przy użyciu kodu synchronicznego, gdy istnieją alternatywy asynchroniczne boli zdolność do skalowania w sposób tańszy. Płacisz za te zablokowane wątki.

Pomyślne nowoczesne aplikacje wymagają kodu asynchronicznego. Bez obsługi języka, pisanie kodu asynchronicznego wymagane wywołania wywołania, zdarzenia zakończenia lub inne środki, które zasłonięte oryginalne intencji kodu. Zaletą kodu synchronicznego jest to, że jest łatwy do zrozumienia. Akcje krok po kroku ułatwiają skanowanie i rozumienie. Tradycyjne modele asynchroniczne zmusiły do skupienia się na asynchronicznym charakterze kodu, a nie na podstawowych akcjach kodu.

## <a name="dont-block-await-instead"></a>Nie blokuj, zamiast tego czekaj

Poprzedni kod demonstruje złe praktyki: konstruowanie kodu synchronicznego do wykonywania operacji asynchronicznych. Jak napisano, ten kod blokuje wątek wykonującgo go z wykonywania innych prac. Nie zostanie ona przerwana, gdy którekolwiek z zadań jest w toku. Byłoby tak, jakby patrzył na toster po włożeniu chleba. Chcesz zignorować ktoś mówi do ciebie, aż toast pojawiło.

Zacznijmy od zaktualizowania tego kodu, aby wątek nie blokować, gdy zadania są uruchomione. Słowo `await` kluczowe zapewnia nieblokujący sposób, aby rozpocząć zadanie, a następnie kontynuować wykonywanie po zakończeniu tego zadania. Prosta asynchroniczna wersja kodu śniadaniowego będzie wyglądać następująco:

[!code-csharp[SimpleAsyncBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V2/Program.cs#Main)]

Ten kod nie blokuje się podczas gotowania jaj lub bekonu. Ten kod nie uruchamia żadnych innych zadań, chociaż. Nadal można umieścić toast w tosterze i patrzeć na to, aż wyskoczy. Ale przynajmniej, chcesz odpowiedzieć na każdego, kto chciał swoją uwagę. W restauracji, w której składa się wiele zamówień, kucharz może rozpocząć kolejne śniadanie, podczas gdy pierwszy gotuje.

Teraz wątek pracujący nad śniadaniem nie jest zablokowany w oczekiwaniu na rozpoczęte zadanie, które jeszcze się nie zakończyło. W przypadku niektórych aplikacji ta zmiana jest wszystkim, co jest potrzebne. Aplikacja GUI nadal odpowiada użytkownikowi tylko z tej zmiany. Jednak w tym scenariuszu chcesz więcej. Nie chcesz, aby każde z zadań składnika było wykonywane sekwencyjnie. Lepiej jest rozpocząć każde z zadań składnika przed oczekiwaniem na zakończenie poprzedniego zadania.

## <a name="start-tasks-concurrently"></a>Jednoczesne uruchamianie zadań

W wielu scenariuszach chcesz natychmiast uruchomić kilka niezależnych zadań. Następnie po zakończeniu każdego zadania można kontynuować inną pracę, która jest gotowa. W analogii śniadaniowej, w ten sposób można dostać śniadanie zrobić szybciej. Można również uzyskać wszystko zrobić blisko tego samego czasu. Otrzymasz gorące śniadanie.

Typy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i pokrewne są klasy, których można użyć do powoda dotyczące zadań, które są w toku. Dzięki temu można napisać kod, który bardziej przypomina sposób, w jaki faktycznie tworzysz śniadanie. W tym samym czasie zacząłbyś gotować jajka, bekon i tosty. Ponieważ każdy wymaga działania, należy zwrócić uwagę na to zadanie, dbać o następnedziałanie, a następnie czekać na coś innego, co wymaga twojej uwagi.

Uruchomić zadanie i przytrzymaj <xref:System.Threading.Tasks.Task> obiekt, który reprezentuje pracę. Będziesz `await` każde zadanie przed pracą z jego wynikiem.

Wytoczmy te zmiany w kodzie śniadaniowym. Pierwszym krokiem jest przechowywanie zadań dla operacji po ich uruchomieniu, a nie oczekiwanie na nie:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggsTask = FryEggs(2);
Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Task<Bacon> baconTask = FryBacon(3);
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Console.WriteLine("Breakfast is ready!");
```

Następnie możesz przenieść `await` oświadczenia o bekon i jajka do końca metody, przed podaniem śniadania:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggsTask = FryEggs(2);
Task<Bacon> baconTask = FryBacon(3);
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

Poprzedni kod działa lepiej. Wszystkie zadania asynchroniczne są uruchamiane jednocześnie. Możesz czekać na każde zadanie tylko wtedy, gdy potrzebujesz wyników. Poprzedni kod może być podobny do kodu w aplikacji sieci web, który sprawia, że żądania różnych mikrousług, a następnie łączy wyniki w jednej stronie. Natychmiast zrobisz wszystkie żądania, `await` a następnie wszystkie te zadania i skomponujesz stronę internetową.

## <a name="composition-with-tasks"></a>Kompozycja z zadaniami

 Masz wszystko gotowe na śniadanie w tym samym czasie z wyjątkiem tosty. Dokonywanie toast jest skład operacji asynchronicznej (opiekanie chleba) i operacji synchronicznych (dodawanie masła i dżemu). Aktualizacja tego kodu ilustruje ważną koncepcję:

> [!IMPORTANT]
> Skład operacji asynchronicznej, po której następuje praca synchroniczna, jest operacją asynchroniczną. Podana w inny sposób, jeśli jakakolwiek część operacji jest asynchroniczna, cała operacja jest asynchroniczna.

Poprzedni kod pokazał, że można <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> użyć lub obiektów do przechowywania uruchomionych zadań. Każde `await` zadanie przed użyciem jego wyniku. Następnym krokiem jest utworzenie metod, które reprezentują kombinację innej pracy. Przed podaniem śniadania, chcesz poczekać na zadanie, które reprezentuje opiekanie chleba przed dodaniem masła i dżemu. Można reprezentować tę pracę z następującym kodem:

[!code-csharp[ComposeToastTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

Poprzednia metoda ma `async` modyfikator w podpisie. Sygnalizuje kompilatorowi, `await` że ta metoda zawiera instrukcję; zawiera operacje asynchroniczne. Ta metoda reprezentuje zadanie, które grzanki chleba, a następnie dodaje masło i dżem. Ta metoda <xref:System.Threading.Tasks.Task%601> zwraca a, który reprezentuje skład tych trzech operacji. Głównym blokiem kodu staje się teraz:

[!code-csharp[StartConcurrentTasks](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#Main)]

Poprzednia zmiana zilustrowała ważną technikę pracy z kodem asynchronicznym. Zadania można składać, oddzielając operacje na nową metodę, która zwraca zadanie. Możesz wybrać, kiedy należy czekać na to zadanie. Można uruchomić inne zadania jednocześnie.

## <a name="await-tasks-efficiently"></a>Sprawnie czekaj na zadania

Seria instrukcji `await` na końcu poprzedniego kodu można poprawić przy użyciu metod `Task` klasy. Jednym z tych <xref:System.Threading.Tasks.Task.WhenAll%2A>interfejsów API jest , który zwraca a, <xref:System.Threading.Tasks.Task> który kończy się po zakończeniu wszystkich zadań na liście argumentów, jak pokazano w następującym kodzie:

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Inną opcją <xref:System.Threading.Tasks.Task.WhenAny%2A>jest użycie `Task<Task>` , który zwraca, że kończy się po zakończeniu któregokolwiek z jego argumentów. Możesz poczekać na zwrócone zadanie, wiedząc, że zostało już zakończone. Poniższy kod pokazuje, jak <xref:System.Threading.Tasks.Task.WhenAny%2A> można użyć do oczekiwania na pierwsze zadanie, aby zakończyć, a następnie przetworzyć jego wynik. Po przetworzeniu wyniku z ukończonego zadania należy usunąć to ukończone `WhenAny`zadanie z listy zadań przekazanych do .

[!code-csharp[AwaitAnyTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

Po tych wszystkich zmianach `Main` ostateczna wersja wygląda jak następujący kod:

[!code-csharp[Final](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#Main)]

Ten końcowy kod jest asynchroniczny. Dokładniej odzwierciedla, jak dana osoba będzie gotować śniadanie. Porównaj poprzedni kod z pierwszym próbku kodu w tym artykule. Podstawowe akcje są nadal jasne z czytania kodu. Możesz przeczytać ten kod w taki sam sposób, jak byś przeczytał te instrukcje dotyczące przygotowania śniadania na początku tego artykułu. Funkcje języka `async` i `await` zapewniają tłumaczenie, które każda osoba wykonuje, aby postępować zgodnie z tymi pisemnymi instrukcjami: uruchamiaj zadania tak, jak to tylko możliwe i nie blokuj oczekiwania na wykonanie zadań.
