---
title: 'Programowanie asynchroniczne w języku C#'
description: 'Omówienie C# Obsługa języków programowania asynchronicznego przy użyciu async, operator await, zadań i zadań<T>'
ms.date: 03/18/2019
---
# <a name="the-task-asynchronous-programming-model-in-c"></a>Zadania asynchronicznego modelu programowania wC# #

Z zadań modelu programowania asynchronicznego (TAP) udostępnia abstrakcję za pośrednictwem kodu asynchronicznego. Pisanie kodu jako sekwencja instrukcji, tak jak zawsze. Możesz przeczytać ten kod tak, jakby każda instrukcja kończy się przed rozpoczęciem następnego. Kompilator wykonuje szereg przekształcenia, ponieważ niektóre z tych instrukcji może rozpocząć pracę i zwracają <xref:System.Threading.Tasks.Task> reprezentujący pracy w toku.

Jest celem tej składni: Włącz kod odczytuje np. sekwencja instrukcji, ale jest wykonywany w kolejności dużo bardziej skomplikowany, oparte na alokacji zasobów zewnętrznych, a po zakończeniu zadania. Jest to analogiczne jak osoby wskazówki dotyczące procesów, które obejmuje zadań asynchronicznych. W tym artykule użyjemy przykładowe instrukcje dokonywania śniadanie, aby zobaczyć, jak `async` i `await` słowa kluczowe ułatwiają przeglądanie informacji o kod, który zawiera szereg instrukcji asynchronicznego. Możesz napisać instrukcje podobną do poniższej liście, aby wyjaśnić, jak śniadanie:

1. Umieścić napić się kawy.
1. Cieplnej się pan, a następnie FRJ potrawach dwa.
1. FRJ trzy wycinki bekon.
1. Wyskakujące dwóch rodzajów chleb.
1. Dodaj masła i zakleszczenie do wyskakującego powiadomienia.
1. Umieścić szkła soku pomarańczowego.

Jeśli masz doświadczenie gotowania, będzie wykonać te instrukcje **asynchronicznie**. czy start ciepły pan dla potrawach, a następnie uruchomić bekon. Czy umieścić chleb w tostera, a następnie uruchomić potrawach. W każdym kroku procesu można będzie uruchomić zadanie, a następnie zwrócić uwagę na zadania, które są gotowe do Twojej uwagi.

Gotowania śniadanie jest dobrym przykładem pracę asynchroniczną, która nie jest równoległe. Jedna osoba (lub wątek) może obsługiwać te zadania. Trwając w sposób analogiczny śniadanie, jedna osoba ułatwia śniadanie asynchronicznie przez uruchomienie kolejnego przed ukończeniem pierwszego. Gotowania w miarę czy ktoś obserwuje go. Zaraz po uruchomieniu ciepły pan dla potrawach, możesz rozpocząć smażeniu bekon. Po rozpoczęciu bekon można umieścić chleb w tostera.

Dla algorytmu równoległego będziesz potrzebować wielu kucharzy (lub wątki). Jeden czyniłyby potrawach, jeden bekon, i tak dalej. Każdy z nich będzie koncentrować się na wystarczy, że jedno zadanie. Każdy Cooka (lub wątek) zostałby zablokowany synchronicznie oczekuje bekon gotowość do przerzucenia lub wyskakujące przeskoczyć do. 

Teraz należy wziąć pod uwagę te tych samych instrukcji, zapisywane jako C# instrukcji:

[!code-csharp[SynchronousBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-starter/Program.cs#Main)]

Komputery nie interpretuje tych instrukcji, co zrobić z tymi samymi osobami sposób. Komputer będzie blokować na każdej instrukcji, przed zakończeniem pracy przed przejściem do następnej instrukcji. Tworząca unsatisfying śniadanie. Nie można uruchomić kolejnych zadaniach, aż do zakończenia miał wcześniej zadania. Zajęłoby znacznie dłużej w celu utworzenia śniadanie, a niektóre elementy będą stają się coraz zimnych przed obsługiwanych. 

Jeśli chcesz, aby komputer asynchroniczne wykonywanie instrukcje powyżej, należy napisać kod asynchroniczny.

Te rozważania są ważne dla programów, które piszesz już dziś. Podczas pisania programów klienckich ma interfejsu użytkownika, aby reagować na dane wejściowe użytkownika. Aplikacja nie powinna upewnij telefonu sprawiać wrażenie podczas pobierania danych z sieci web. Podczas pisania programów serwera, które nie mają zablokowane wątki. Te wątki mogą obsługująca innych żądań. Przy użyciu kodu synchronicznego, gdy asynchronicznych rozwiązań alternatywnych istnieją dobrze jest możliwość skalowania w poziomie mniej opracowanego. Płacisz za tych zablokowane wątki.

Pomyślne nowoczesne aplikacje wymagają kodu asynchronicznego. Bez obsługi języka kodu asynchronicznego zapisywać wywołań zwrotnych, zakończenia zdarzenia lub inne oznacza, że zostanie przesłonięty, oryginalnym celem kodu. Zaletą synchroniczny kod jest ona łatwa do zrozumienia. Akcje krok po kroku ułatwiają przeskanować i zrozumieć. Tradycyjne modelami asynchronicznymi wymuszone możesz skoncentrować się na asynchroniczne rodzaj kodu, a nie na podstawowe działania kodu.

## <a name="dont-block-await-instead"></a>Nie blokuj, zamiast tego await

Poprzedni kod pokazuje złym zwyczajem: konstruowanie synchroniczny kod w celu wykonywania operacji asynchronicznej. W ten kod blokuje wątku, ale wykonanie go z innymi dostawcami. Nie były wyświetlane, gdy dowolne zadania są w toku. Jest tak, jakby stared na tostera po umieszczenie chleb w. Czy można zignorować każdy rozmawiając aż wyskakujące zdjęte ze stosu. 

Zacznijmy od, aktualizując ten kod, tak aby nie blokuje wątku, podczas wykonywania zadania. `await` — Słowo kluczowe umożliwia nieblokującej na poziomie uruchomić zadanie, a następnie kontynuuj wykonywanie po zakończeniu tego zadania. Prosta wersja asynchronicznego wykonującego kodu śniadanie będzie wyglądać poniższy fragment kodu:

[!code-csharp[SimpleAsyncBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V2/Program.cs#Main)]

Ten kod nie blokuje, gdy są gotowania potrawach lub bekon. Ten kod nie będzie jednak uruchomić innych zadań. Czy nadal umieścić wyskakujące w tostera, a stare go do momentu jej POP. Ale co najmniej reaguje dla każdego, kto chce Twojej uwagi. Restauracji, gdzie są umieszczone wiele zamówień Cooka uruchomiła inny śniadanie podczas pierwszego jest gotowania.

Wątek nad śniadanie nie jest blokowane podczas oczekiwania na rozpoczęte zadanie, które nie zostało jeszcze zakończone. W niektórych aplikacjach ta zmiana ma wszystko, co jest potrzebne. Aplikacji GUI nadal odpowiada na użytkownika za pomocą tylko tej zmiany. Jednak w tym scenariuszu ma więcej. Nie chcesz każdego składnika zadań, które mają być wykonywane sekwencyjnie. Zaleca się rozpoczynać każde z zadań składnik przed oczekiwanie na ukończenie poprzedniego zadania.

## <a name="start-tasks-concurrently"></a>Równoczesne zadania uruchamiania

W wielu przypadkach chcesz uruchomić kilka niezależnych zadań od razu. Następnie gdy poszczególne podzadania zakończą, można kontynuować inne prace, które jest gotowe. Analogicznie śniadanie to jak się dostać śniadanie wykonywane szybciej. Możesz także uzyskać, wszystko gotowe blisko tym samym czasie. Przedstawiamy śniadanie gorąca.

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i powiązanych typów klas, które umożliwia przeglądanie informacji o zadania, które są w toku. Która pozwala napisać kod, który bardziej przypomina sposób, w rzeczywistości utworzyłoby śniadanie. Chce się uruchomić, gotowania potrawach, bekon i powiadomienie typu toast w tym samym czasie. Każdy wymaga akcji, czy zwrócić uwagę na to zadanie, zajmie się następnej akcji, następnie await do czegoś innego, która wymaga uwagi.

Uruchomienie zadania i przechowywania w <xref:System.Threading.Tasks.Task> obiekt, który reprezentuje pracę. Będziesz `await` każdego zadania, przed rozpoczęciem pracy z jego wynik.

Upewnijmy się te zmiany do kodu śniadanie. Pierwszym krokiem jest do przechowywania zadań dla operacji podczas uruchamiania, a nie oczekuje na ich:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggTask = FryEggs(2);
Egg eggs = await eggTask;
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

Następnie możesz przenieść `await` instrukcji bekon i potrawach na końcu metody, zanim śniadanie:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggTask = FryEggs(2);
Task<Bacon> baconTask = FryBacon(3);
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

Powyższy kod działa lepiej. Asynchroniczne zadania możesz rozpocząć tylko raz. Każde zadanie podrzędne jest await, tylko wtedy, gdy potrzebujesz wyników. Powyższy kod może być podobny do kodu w aplikacji sieci web, który zgłasza żądania dotyczące różnych mikrousług, a następnie scala wyniki w pojedynczej strony. Wprowadzisz wszystkich żądań, następnie `await` wszystkie te zadania i narzędzia compose strony sieci web.

## <a name="composition-with-tasks"></a>Kompozycja z zadaniami

 Masz wszystko gotowe do śniadanie w tym samym czasie, z wyjątkiem wyskakującego powiadomienia. Tworzenie wyskakujące jest skład operację asynchroniczną (toasting chleb) oraz operacje synchroniczne (dodanie masła i zakleszczenie). Aktualizowanie tego kodu pokazano bardzo ważnym pojęciem:

> [!IMPORTANT]
> Skład następuje Praca synchroniczna operacja asynchroniczna jest operacją asynchroniczną. Określona w inny sposób, jeśli jakakolwiek część operacji jest asynchroniczne, cała operacja jest asynchroniczna.

Powyższy kod wykazało, że można użyć <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektów, aby pomieścić uruchomione zadania podrzędne. Możesz `await` każdego zadania, przed rozpoczęciem korzystania z jego wynik. Następnym krokiem jest, aby utworzyć metody, które reprezentują kombinacji innych zadań. Przed rozpoczęciem obsługi śniadanie, należy poczekać na zadanie, które reprezentuje toasting chleb przed dodaniem masła i zakleszczenie. Może reprezentować pracę z następującym kodem:

[!code-csharp[ComposeToastTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

Powyższa metoda ma `async` modyfikator w podpisie. Który sygnalizuje kompilatorowi, ta metoda zawiera `await` instrukcji; zawiera on operacji asynchronicznych. Ta metoda reprezentuje zadanie, które toasts chleb, a następnie dodaje masła i zakleszczenie. Ta metoda zwraca <xref:System.Threading.Tasks.Task%601> reprezentujący kompozycji te trzy operacje. Główny blok kodu staje się:

[!code-csharp[StartConcurrentTasks](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#Main)]

Poprzednia zmiana zilustrowane ważną technikę do pracy z kodu asynchronicznego. Dzięki oddzieleniu operacji na nową metodę, która zwraca klasę task, redagowania zadań. Możesz wybrać, kiedy należy poczekać na zadanie. Można jednocześnie uruchomić inne zadania.

## <a name="await-tasks-efficiently"></a>Efektywne await zadania

Seria `await` instrukcji na końcu poprzedniego kodu można zwiększyć za pomocą metody `Task` klasy. Jedną z tych interfejsów API jest <xref:System.Threading.Tasks.Task.WhenAll%2A>, co powoduje zwrócenie <xref:System.Threading.Tasks.Task> którego działanie jest kończone po zakończeniu wszystkich zadań w swojej listy argumentów, jak pokazano w poniższym kodzie:

```csharp
await Task.WhenAll(eggTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Innym rozwiązaniem jest użycie <xref:System.Threading.Tasks.Task.WhenAny%2A>, co powoduje zwrócenie `Task<Task>` , działanie jest kończone po zakończeniu przez dowolny z jej argumentów. Zwrócone zadanie może poczekać, wiedząc, że zostało już zakończone. Poniższy kod przedstawia sposób użycia <xref:System.Threading.Tasks.Task.WhenAny%2A> aby poczekać na pierwsze zadanie, aby zakończyć i następnie przetworzyć jego wynik. Po przetworzeniu wynikiem ukończone zadanie podrzędne, usuń ukończone zadania z listy zadań przekazany do `WhenAny`.

[!code-csharp[AwaitAnyTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

Po wprowadzeniu wszystkich tych zmian, ostateczną wersją `Main` wygląda podobnie do poniższego kodu:

[!code-csharp[Final](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#Main)]

Ten kod końcowy jest asynchroniczna. Odzwierciedla dokładniej, jak osoba będzie Cooka śniadanie. Należy porównać poprzedni kod z pierwszym przykładowy kod w tym artykule. Akcje podstawowe są nadal jasne z kodu. Możesz przeczytać ten kod w taki sam sposób, wczytane tych instrukcji składania śniadanie na początku tego artykułu. Funkcje języka `async` i `await` Podaj tłumaczenia sprawia, że każda osoba z tymi pisemnych instrukcji: uruchamiania zadań, jak można, a nie blokować oczekiwanie na ukończenie zadań.
