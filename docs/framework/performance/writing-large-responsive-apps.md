---
title: Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03c2620913aff2ef2934e7c07574c130923c7139
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540666"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="ffb30-102">Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ffb30-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="ffb30-103">Ten artykuł zawiera wskazówki dotyczące poprawy wydajności dużych aplikacji .NET Framework lub aplikacje, które przetwarzają dużą ilość danych, takie jak pliki lub bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ffb30-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="ffb30-104">Te wskazówki pochodzą ponowne napisanie kompilatory C# i Visual Basic w kodzie zarządzanym, a w tym artykule przedstawiono kilka przykładów rzeczywistych z kompilatorem C#.</span><span class="sxs-lookup"><span data-stu-id="ffb30-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="ffb30-105">Program .NET Framework jest wysoce wydajna, do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="ffb30-106">Zaawansowane i bezpieczne, a bogaty zbiór bibliotek należy wysoce rozwijającemu tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="ffb30-107">Jednak doskonałym produktywne pochodzi odpowiedzialności.</span><span class="sxs-lookup"><span data-stu-id="ffb30-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="ffb30-108">Powinny korzystaj z możliwości programu .NET Framework, ale należy przygotować do dostrajania wydajności kodu, gdy potrzebne.</span><span class="sxs-lookup"><span data-stu-id="ffb30-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span> 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="ffb30-109">Dlaczego nowe wydajne kompilatora ma zastosowanie do aplikacji</span><span class="sxs-lookup"><span data-stu-id="ffb30-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="ffb30-110">Zespół platformy kompilatora .NET ("Roslyn") rewrote języka C# i Kompilatory języka Visual Basic w zarządzany kod, aby podać nowe interfejsy API do modelowania i analizowanie kodu, narzędzia do tworzenia i włączania znacznie bardziej rozbudowane, kod środowiska w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ffb30-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="ffb30-111">Ponowne napisanie kompilatorów i programu Visual Studio do tworzenia środowiska na nowych kompilatory ujawniło szczegółowe informacje o wydajności przydatne, które mają zastosowanie do wszystkich dużych aplikacji .NET Framework lub dowolną aplikację, która przetwarza dużą ilość danych.</span><span class="sxs-lookup"><span data-stu-id="ffb30-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="ffb30-112">Nie musisz wiedzieć o kompilatory, aby móc korzystać z szczegółowych informacji i przykłady z kompilatorem C#.</span><span class="sxs-lookup"><span data-stu-id="ffb30-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="ffb30-113">Visual Studio używa kompilatora interfejsów API do tworzenia wszystkie funkcje IntelliSense, które lubią użytkowników, takie jak zygzaki kolorowanie identyfikatorów i słów kluczowych, uzupełniania składni, błędy, parametr porad, problemów z kodem, i działania kodu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="ffb30-114">Program Visual Studio zapewnia tę pomoc podczas deweloperów są wpisywania i zmienianie ich kod i programu Visual Studio musi nadal odpowiadać, gdy kompilator stale modeluje kod, który deweloperzy edycji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span> 
  
 <span data-ttu-id="ffb30-115">Gdy użytkownikom końcowym interakcję z aplikacją, ich powinien odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="ffb30-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="ffb30-116">Wpisywanie lub obsługi polecenia nigdy nie powinien być blokowany.</span><span class="sxs-lookup"><span data-stu-id="ffb30-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="ffb30-117">Pomoc powinny się pojawiać, szybko lub zrezygnować, jeśli użytkownik nadal, wpisując.</span><span class="sxs-lookup"><span data-stu-id="ffb30-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="ffb30-118">Aplikację należy unikać blokowania wątku interfejsu użytkownika z długich obliczeń, które aplikacji wydawać się wolne.</span><span class="sxs-lookup"><span data-stu-id="ffb30-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span> 
  
 <span data-ttu-id="ffb30-119">Aby uzyskać więcej informacji na temat kompilatory Roslyn zobacz [zestawu SDK platformy kompilatora .NET](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="ffb30-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="ffb30-120">Po prostu fakty</span><span class="sxs-lookup"><span data-stu-id="ffb30-120">Just the Facts</span></span>  
 <span data-ttu-id="ffb30-121">Należy wziąć pod uwagę następujące fakty podczas dostosowywania wydajności i tworzenie szybko reagujących aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ffb30-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span> 
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="ffb30-122">Fakt 1: Przedwczesne nie Optymalizuj</span><span class="sxs-lookup"><span data-stu-id="ffb30-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="ffb30-123">Pisanie kodu, który jest bardziej złożona, nie musi to być naliczane konserwacji, debugowania i wygładzanie kosztów.</span><span class="sxs-lookup"><span data-stu-id="ffb30-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="ffb30-124">Doświadczeni programiści mają opanujesz intuicyjny sposób rozwiązywania problemów kodowania i napisać kod, bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="ffb30-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="ffb30-125">Jednak mogą czasami przedwcześnie optymalizacji ich kodu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="ffb30-126">Na przykład używają tabeli mieszania podczas prostej tablicy może wystarczyć lub używanie buforowania skomplikowane, że dochodzi do wycieku pamięci, a nie po prostu ponowne obliczanie wartości.</span><span class="sxs-lookup"><span data-stu-id="ffb30-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="ffb30-127">Nawet jeśli jesteś programistą środowisko, możesz testowanie wydajności i Analizuj swój kod, gdy znajdziesz problemy.</span><span class="sxs-lookup"><span data-stu-id="ffb30-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span> 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="ffb30-128">Fakt 2: Jeśli użytkownik nie notuje, jesteś zgadywania</span><span class="sxs-lookup"><span data-stu-id="ffb30-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="ffb30-129">Profile i pomiarów nie znajdować się.</span><span class="sxs-lookup"><span data-stu-id="ffb30-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="ffb30-130">Profile dowiesz się, czy Procesor jest w pełni załadowane lub tego, czy w przypadku zablokowania na We/Wy dysku.</span><span class="sxs-lookup"><span data-stu-id="ffb30-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="ffb30-131">Profile wyświetla komunikat informujący o tym, jakiego rodzaju i jak ilość pamięci alokowaniu i czy your CPU zużywa dużo czasu w [wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="ffb30-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../../docs/standard/garbage-collection/index.md) (GC).</span></span> 
  
 <span data-ttu-id="ffb30-132">Należy ustawić środowiska lub scenariuszy celami wydajności dla klientów w aplikacji i pisania testów do pomiaru wydajności.</span><span class="sxs-lookup"><span data-stu-id="ffb30-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="ffb30-133">Badanie niepowodzenie testów, stosując metodę wykładniczej: aby ułatwiają, hipotezę, co może być problem, użyj profilów i testowanie Twojej hipotezę z eksperymentu lub zmiany kodu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="ffb30-134">Wraz z upływem czasu z regularnych testowania, należy ustanowić pomiarów wydajności bazowego, dzięki czemu można izolować zmiany, które powodują regresji wydajności.</span><span class="sxs-lookup"><span data-stu-id="ffb30-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="ffb30-135">Zbliża się wydajność pracy, w sposób rygorystyczne, będzie uniknąć marnowania czasu za pomocą aktualizacji kodu, które nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="ffb30-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span> 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="ffb30-136">Fakt 3: Dobre narzędzia sprawiają, że wszystkie różnicy</span><span class="sxs-lookup"><span data-stu-id="ffb30-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="ffb30-137">Dobre narzędzia pozwalają szybko przejść do szczegółów największych problemów z wydajnością (procesor CPU, pamięć lub dysk) i pomoc, możesz znaleźć kod, który powoduje, że te wąskich gardeł.</span><span class="sxs-lookup"><span data-stu-id="ffb30-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="ffb30-138">Microsoft dostarczany szeroką gamą narzędzi wydajności, takich jak [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [narzędzie do analizy Windows Phone](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), i [narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="ffb30-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone Analysis Tool](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span> 
  
 <span data-ttu-id="ffb30-139">Narzędzia PerfView jest bezpłatne i niezwykle wydajne narzędzia, która pozwala skupić się na szczegółowe zagadnienia, takie jak We/Wy dysku, zdarzenia odzyskiwania pamięci i pamięci.</span><span class="sxs-lookup"><span data-stu-id="ffb30-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="ffb30-140">Można przechwycić związane z wydajnością [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) zdarzeń (ETW) i widok prosty sposób na aplikację, na proces, na stosie i na informacje o wątku.</span><span class="sxs-lookup"><span data-stu-id="ffb30-140">You can capture performance-related [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="ffb30-141">Narzędzia PerfView pokazuje, ile i jakiego rodzaju pamięci są przydzielane aplikację, i które funkcji lub wywołanie stosów Współtworzenie ile alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="ffb30-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="ffb30-142">Aby uzyskać więcej informacji, zobacz zaawansowane tematy pomocy, pokazy i filmy wideo, włączone za pomocą narzędzia (takie jak [samouczki narzędzia PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) w witrynie Channel 9).</span><span class="sxs-lookup"><span data-stu-id="ffb30-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span> 
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="ffb30-143">Fakt 4: Przede wszystkim chodzi o alokacji</span><span class="sxs-lookup"><span data-stu-id="ffb30-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="ffb30-144">Może się wydawać, że tworzenie szybko reagujących aplikacji .NET Framework to przede wszystkim algorytmy, takie jak za pomocą szybkiego sortowania zamiast sortowania bąbelków, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="ffb30-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="ffb30-145">Największe czynnikiem tworzenia szybko reagujących aplikacji jest alokacji pamięci, szczególnie w przypadku, gdy Twoja aplikacja jest bardzo duża lub przetwarza duże ilości danych.</span><span class="sxs-lookup"><span data-stu-id="ffb30-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span> 
  
 <span data-ttu-id="ffb30-146">Prawie wszystko, co środowisk pracy, aby tworzyć odpowiednie środowisko IDE, za pomocą kompilatora nowe interfejsy API związane z unikanie alokacji i zarządzanie nimi strategii buforowania.</span><span class="sxs-lookup"><span data-stu-id="ffb30-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="ffb30-147">Ślady narzędzia PerfView Pokaż wydajność nowych Kompilatory języka C# i Visual Basic jest rzadko powiązana procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="ffb30-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="ffb30-148">Kompilatory mogą być operacji We/Wy powiązany podczas odczytywania setki tysięcy lub milionów wierszy kodu, podczas odczytywania metadanych, lub emitowania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="ffb30-149">Opóźnienia wątku interfejsu użytkownika są prawie wszystkich z powodu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ffb30-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="ffb30-150">.NET Framework GC jest ona dostrojona o wysokiej wydajności i wykonuje znaczną część swojej pracy, jednocześnie, gdy kod aplikacji jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="ffb30-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="ffb30-151">Jednak możesz wyzwolić kosztowne pojedynczą alokację [gen2](../../../docs/standard/garbage-collection/fundamentals.md) kolekcji, zatrzymanie wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="ffb30-151">However, a single allocation can trigger an expensive [gen2](../../../docs/standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span> 
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="ffb30-152">Typowe alokacji i przykłady</span><span class="sxs-lookup"><span data-stu-id="ffb30-152">Common allocations and examples</span></span>  
 <span data-ttu-id="ffb30-153">Przykładowe wyrażenia w tej sekcji zostały ukryte alokacje są niewielkie.</span><span class="sxs-lookup"><span data-stu-id="ffb30-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="ffb30-154">Jednak w przypadku dużych aplikacji wykonuje wyrażeń kilka razy, mogą oni powoduje, że kilkuset megabajtów, nawet gigabajtów alokacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="ffb30-155">Na przykład co minutę testów, które symulowane dewelopera wpisywania w edytorze gigabajtów pamięci przydzielonych i prowadzone zespołu wydajności, aby skoncentrować się na wpisywanie scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="ffb30-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span> 
  
### <a name="boxing"></a><span data-ttu-id="ffb30-156">Boxing</span><span class="sxs-lookup"><span data-stu-id="ffb30-156">Boxing</span></span>  
 <span data-ttu-id="ffb30-157">[Konwersja boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) występuje, gdy wartość typy, które zwykle na żywo na stosie lub dane struktury są zapakowane w obiekt.</span><span class="sxs-lookup"><span data-stu-id="ffb30-157">[Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="ffb30-158">Oznacza to przydzielić obiektu w celu przechowywania danych, a następnie zwraca wskaźnik do obiektu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="ffb30-159">.NET Framework czasami pola wartości, ponieważ podpis metody lub typu lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="ffb30-160">Zawijanie typu wartości w alokacji pamięci powoduje, że obiekt.</span><span class="sxs-lookup"><span data-stu-id="ffb30-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="ffb30-161">Wiele operacji pakowania może współtworzyć zawartość w megabajtach lub gigabajtach alokacji do swojej aplikacji, co oznacza, że aplikacji spowoduje, że więcej wykazów globalnych.</span><span class="sxs-lookup"><span data-stu-id="ffb30-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="ffb30-162">.NET Framework i Kompilatory języka uniknąć pakowania, gdy jest to możliwe, ale czasami występuje, jeśli co najmniej oczekuje.</span><span class="sxs-lookup"><span data-stu-id="ffb30-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span> 
  
 <span data-ttu-id="ffb30-163">Aby zobaczyć pakowania w PerfView, otwórz śledzenia i przyjrzyj się stosy alokacji sterty GC w swojej aplikacji, nazwa procesu (Pamiętaj, że narzędzia PerfView raport dotyczący wszystkich procesów).</span><span class="sxs-lookup"><span data-stu-id="ffb30-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="ffb30-164">Jeśli widzisz typów, takich jak <xref:System.Int32?displayProperty=nameWithType> i <xref:System.Char?displayProperty=nameWithType> w ramach przydziałów, czy konwersja boxing typów wartości.</span><span class="sxs-lookup"><span data-stu-id="ffb30-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="ffb30-165">Wybranie jednego z następujących typów zostaną wyświetlone stosy i funkcje, w których są ramce.</span><span class="sxs-lookup"><span data-stu-id="ffb30-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span> 
  
 <span data-ttu-id="ffb30-166">**Przykład 1: ciąg metody i wartości argumentów typu**</span><span class="sxs-lookup"><span data-stu-id="ffb30-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="ffb30-167">Ten przykładowy kod przedstawia potencjalnie niepotrzebnych i nadmierne opakowania:</span><span class="sxs-lookup"><span data-stu-id="ffb30-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 <span data-ttu-id="ffb30-168">Ten kod zawiera funkcje rejestrowania, dzięki czemu aplikacja może wywołać `Log` często może działać milionów razy.</span><span class="sxs-lookup"><span data-stu-id="ffb30-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="ffb30-169">Problem jest wywołanie `string.Format` jest rozpoznawana jako <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="ffb30-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span> 
  
 <span data-ttu-id="ffb30-170">To przeciążenie wymaga programu .NET Framework do pola `int` wartości na obiekty w celu przekazania ich wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="ffb30-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="ffb30-171">Częściowe obejście polega na wywołanie `id.ToString()` i `size.ToString()` i Przekaż wszystkie ciągi, (które są obiektami) do `string.Format` wywołania.</span><span class="sxs-lookup"><span data-stu-id="ffb30-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="ffb30-172">Wywoływanie `ToString()` przydzielić ciągu, jednak, że alokacji zostanie obsłużony mimo to w `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span> 
  
 <span data-ttu-id="ffb30-173">Należy rozważyć oznacza w tym podstawowe wywołanie `string.Format` jest po prostu ciągów, dzięki czemu może napisać ten kod:</span><span class="sxs-lookup"><span data-stu-id="ffb30-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="ffb30-174">Jednak ten wiersz kodu wprowadza alokacji pakowanie, ponieważ kompiluje, aby <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="ffb30-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="ffb30-175">.NET Framework należy polu znak literału do wywołania `Concat`</span><span class="sxs-lookup"><span data-stu-id="ffb30-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="ffb30-176">**Na przykład rozwiązać 1**</span><span class="sxs-lookup"><span data-stu-id="ffb30-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="ffb30-177">Pełne poprawka jest proste.</span><span class="sxs-lookup"><span data-stu-id="ffb30-177">The complete fix is simple.</span></span> <span data-ttu-id="ffb30-178">Wystarczy zastąpić literał znakowy z ciągiem literału, którą jest naliczana nie pakowanie, ponieważ ciągi są już obiektami:</span><span class="sxs-lookup"><span data-stu-id="ffb30-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="ffb30-179">**Przykład 2: wyliczenia pakowania**</span><span class="sxs-lookup"><span data-stu-id="ffb30-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="ffb30-180">W tym przykładzie była odpowiedzialna za ogromna ilość alokacji w nowych Kompilatory języka C# i Visual Basic z powodu często są używane typy wyliczeniowe, szczególnie w przypadku operacji wyszukiwania w słowniku.</span><span class="sxs-lookup"><span data-stu-id="ffb30-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span> 
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 <span data-ttu-id="ffb30-181">Ten problem jest bardzo subtelne.</span><span class="sxs-lookup"><span data-stu-id="ffb30-181">This problem is very subtle.</span></span> <span data-ttu-id="ffb30-182">Narzędzia PerfView będzie Zgłoś to jako <xref:System.Enum.GetHashCode> pakowanie, ponieważ metody pól bazowego reprezentacja na typ wyliczenia ze względów implementacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="ffb30-183">Jeśli wygląda ściśle znajduje się w PerfView, może zostać wyświetlony dwóch alokacje pakowania dla każdego wywołania <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="ffb30-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="ffb30-184">Kompilator powoduje wstawienie jednego, a .NET Framework drugiego.</span><span class="sxs-lookup"><span data-stu-id="ffb30-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span> 
  
 <span data-ttu-id="ffb30-185">**Na przykład rozwiązać 2**</span><span class="sxs-lookup"><span data-stu-id="ffb30-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="ffb30-186">Łatwo można uniknąć zarówno alokacje przez rzutowanie do podstawowej reprezentacji przed wywołaniem <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="ffb30-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="ffb30-187">Jest innym źródłem wspólnej pakowania na typy wyliczeniowe <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ffb30-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ffb30-188">Argumentu przekazanego do <xref:System.Enum.HasFlag%28System.Enum%29> musi zostać opakowany.</span><span class="sxs-lookup"><span data-stu-id="ffb30-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="ffb30-189">W większości przypadków zastępowania wywołań do <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bitowe testu jest prostszy i zwolnić alokacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span> 
  
 <span data-ttu-id="ffb30-190">Pamiętać pierwszy fakt wydajności (czyli nie przedwcześnie Optymalizacja) i nie należy uruchamiać ponowne napisanie kodu w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="ffb30-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="ffb30-191">Należy pamiętać o tych kosztów pakowania, ale tylko po profilowania aplikacji i znajdowanie punktów aktywnych zmian w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ffb30-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span> 
  
### <a name="strings"></a><span data-ttu-id="ffb30-192">Ciągi</span><span class="sxs-lookup"><span data-stu-id="ffb30-192">Strings</span></span>  
 <span data-ttu-id="ffb30-193">Działań na ciągach są niektóre z największych sprawcami dla alokacji i są one często wyświetlane w PerfView w alokacjach pięć.</span><span class="sxs-lookup"><span data-stu-id="ffb30-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="ffb30-194">Programy używać parametrów dla serializacji JSON i interfejsów API REST.</span><span class="sxs-lookup"><span data-stu-id="ffb30-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="ffb30-195">Ciągi jako programowe stałe służy do współpracy z systemami, gdy nie można używać typów wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="ffb30-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="ffb30-196">Gdy usługi profilowania wskazuje, czy ciągi są wysoce wpływających na wydajność, poszukaj wywołania <xref:System.String> metody takie jak <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="ffb30-197">Za pomocą <xref:System.Text.StringBuilder> Aby uniknąć kosztów tworzenie jednego ciągu z wielu fragmentów pomaga, ale nawet przydzielanie <xref:System.Text.StringBuilder> obiektu może stać się wąskim gardłem, potrzebne do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="ffb30-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span> 
  
 <span data-ttu-id="ffb30-198">**Przykład 3: operacje na ciągach**</span><span class="sxs-lookup"><span data-stu-id="ffb30-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="ffb30-199">Kompilator języka C# nie ten kod, który zapisuje tekst sformatowany komentarza dokumentacji XML:</span><span class="sxs-lookup"><span data-stu-id="ffb30-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 <span data-ttu-id="ffb30-200">Aby zobaczyć, że ten kod wykonuje wiele manipulowanie ciągami.</span><span class="sxs-lookup"><span data-stu-id="ffb30-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="ffb30-201">Kod używa metody biblioteki do podziału wierszy w oddzielnych ciągi, można przycięcia biały znak, aby sprawdzić, czy argument `text` jest komentarz dokumentacji XML i wyodrębnianie podciągów z wierszy.</span><span class="sxs-lookup"><span data-stu-id="ffb30-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span> 
  
 <span data-ttu-id="ffb30-202">W pierwszym wierszu wewnątrz `WriteFormattedDocComment`, `text.Split` wywołanie za każdym razem, gdy jest on nazywany przydziela nowe trzy elementowej tablicy jako argument.</span><span class="sxs-lookup"><span data-stu-id="ffb30-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="ffb30-203">Kompilator musi emitują kod, aby przydzielić każdorazowo tej tablicy.</span><span class="sxs-lookup"><span data-stu-id="ffb30-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="ffb30-204">To, ponieważ kompilator nie wie, jeśli <xref:System.String.Split%2A> przechowuje tablicy gdzieś gdzie tablicy mogą zostać zmodyfikowane przez inny kod, który będzie wpływać na nowsze wywołania `WriteFormattedDocComment`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="ffb30-205">Wywołanie <xref:System.String.Split%2A> również przydziela ciąg dla każdego wiersza w `text` i przydziela innej pamięci do wykonania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span> 
  
 <span data-ttu-id="ffb30-206">`WriteFormattedDocComment` ma trzy wywołania <xref:System.String.TrimStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ffb30-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="ffb30-207">Dwa znajdują się w wewnętrznej pętli, które zduplikowane pracy i przydziałów.</span><span class="sxs-lookup"><span data-stu-id="ffb30-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="ffb30-208">Zapewnienie liczy co gorsza, wywołanie <xref:System.String.TrimStart%2A> metody bez argumentów przydziela pusta tablica (dla `params` parametr) oprócz wynikowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="ffb30-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span> 
  
 <span data-ttu-id="ffb30-209">Ponadto występuje po wywołaniu <xref:System.String.Substring%2A> metody, która zwykle przydziela nowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="ffb30-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span> 
  
 <span data-ttu-id="ffb30-210">**Na przykład rozwiązać 3**</span><span class="sxs-lookup"><span data-stu-id="ffb30-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="ffb30-211">W przeciwieństwie do wcześniejszych przykładach drobnych modyfikacji nie może rozwiązać tych przydziałów.</span><span class="sxs-lookup"><span data-stu-id="ffb30-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="ffb30-212">Musisz cofnijmy, Przyjrzyj się problem i podejście do inaczej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="ffb30-213">Na przykład, można zauważyć, że argument `WriteFormattedDocComment()` jest ciągiem, który zawiera wszystkie informacje, które wymaga metody, dzięki czemu kod może zrobić więcej indeksowania, zamiast przydzielać wiele ciągi częściowe.</span><span class="sxs-lookup"><span data-stu-id="ffb30-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span> 
  
 <span data-ttu-id="ffb30-214">Kompilator wydajności zespołu rozwiązywane tych przydziałów za pomocą kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ffb30-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc... 
```  
  
 <span data-ttu-id="ffb30-215">Pierwsza wersja `WriteFormattedDocComment()` przydzielone tablicę, kilku podciągów i podciągu przycięcia wraz z pustą `params` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ffb30-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="ffb30-216">Również sprawdzane dla "/ / /".</span><span class="sxs-lookup"><span data-stu-id="ffb30-216">It also checked for "///".</span></span> <span data-ttu-id="ffb30-217">Poprawiony kod wykorzystuje tylko indeksowania i przydziela nothing.</span><span class="sxs-lookup"><span data-stu-id="ffb30-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="ffb30-218">Znajduje pierwszy znak, który nie jest biały znak, a następnie sprawdza, czy znak po znaku aby zobaczyć, czy ciąg rozpoczyna się od "/ / /".</span><span class="sxs-lookup"><span data-stu-id="ffb30-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="ffb30-219">Nowy kod używa `IndexOfFirstNonWhiteSpaceChar` zamiast <xref:System.String.TrimStart%2A> do zwrócenia pierwszego indeksu (po wskaźniku początkową), w którym występuje znak inny niż biały.</span><span class="sxs-lookup"><span data-stu-id="ffb30-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="ffb30-220">Poprawka nie została ukończona, ale możesz dowiedzieć się, jak można zastosować poprawki podobne pełne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="ffb30-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="ffb30-221">Dzięki zastosowaniu tej metody w całym kodzie, można usunąć wszystkie alokacje w `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span> 
  
 <span data-ttu-id="ffb30-222">**Przykład 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="ffb30-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="ffb30-223">W tym przykładzie użyto <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="ffb30-224">Poniższa funkcja generuje Pełna nazwa typu dla typów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="ffb30-224">The following function generates a full type name for generic types:</span></span>  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 <span data-ttu-id="ffb30-225">Fokus znajduje się w wierszu, który tworzy nową <xref:System.Text.StringBuilder> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ffb30-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="ffb30-226">Kod powoduje, że przydział `sb.ToString()` i wewnętrzne alokacje w ramach <xref:System.Text.StringBuilder> implementacji, ale nie można kontrolować te alokacji, jeśli chcesz, aby wynikowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="ffb30-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span> 
  
 <span data-ttu-id="ffb30-227">**Na przykład rozwiązać 4**</span><span class="sxs-lookup"><span data-stu-id="ffb30-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="ffb30-228">Aby naprawić `StringBuilder` obiekt alokacji; obiektu w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="ffb30-229">Buforowanie nawet pojedyncze wystąpienie, które mogą uzyskać wyrzucać może znacznie poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="ffb30-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="ffb30-230">Jest to funkcja nową metodę implementacji, pomijając cały kod, z wyjątkiem nowej linii imię i nazwisko:</span><span class="sxs-lookup"><span data-stu-id="ffb30-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="ffb30-231">Kluczowe elementy są nowe `AcquireBuilder()` i `GetStringAndReleaseBuilder()` funkcje:</span><span class="sxs-lookup"><span data-stu-id="ffb30-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 <span data-ttu-id="ffb30-232">Ponieważ kompilatory nowe korzystają z wątków, tych implementacji użyć pola statyczne wątku (<xref:System.ThreadStaticAttribute> atrybutu) do pamięci podręcznej <xref:System.Text.StringBuilder>, i prawdopodobnie można uniknąć `ThreadStatic` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="ffb30-233">Pola statyczne wątku przechowuje unikatową wartość dla każdego wątku, który jest wykonywany ten kod.</span><span class="sxs-lookup"><span data-stu-id="ffb30-233">The thread-static field holds a unique value for each thread that executes this code.</span></span> 
  
 <span data-ttu-id="ffb30-234">`AcquireBuilder()` Zwraca buforowane <xref:System.Text.StringBuilder> wystąpienia, jeśli istnieje, po ich czyszczenie i ustawienie pola lub pamięci podręcznej na wartość null.</span><span class="sxs-lookup"><span data-stu-id="ffb30-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="ffb30-235">W przeciwnym razie `AcquireBuilder()` tworzy nowe wystąpienie i zwraca go, pozostawiając pole lub pamięci podręcznej zestawu o wartości null.</span><span class="sxs-lookup"><span data-stu-id="ffb30-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span> 
  
 <span data-ttu-id="ffb30-236">Gdy ukończysz pracę z <xref:System.Text.StringBuilder> , należy wywołać `GetStringAndReleaseBuilder()` można pobrać wynik ciągu, Zapisz <xref:System.Text.StringBuilder> wystąpienia w polu lub pamięci podręcznej, a następnie zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="ffb30-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="ffb30-237">Jest możliwe do wykonania, ponownie wprowadź ten kod i utworzyć wiele <xref:System.Text.StringBuilder> obiektów (chociaż, rzadko wykonywane).</span><span class="sxs-lookup"><span data-stu-id="ffb30-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="ffb30-238">Zapisuje kodu tylko ostatnia wydana <xref:System.Text.StringBuilder> wystąpienia do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="ffb30-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="ffb30-239">Ten prosty strategii buforowania znacząco zmniejszyć alokacji w nowych kompilatory.</span><span class="sxs-lookup"><span data-stu-id="ffb30-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="ffb30-240">Części środowiska .NET Framework i programu MSBuild ("MSBuild") użyć podobne techniki, aby zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="ffb30-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span> 
  
 <span data-ttu-id="ffb30-241">Ten prosty strategii buforowania działa zgodnie z projektu dobre pamięci podręcznej, ponieważ ma ona limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="ffb30-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="ffb30-242">Istnieje jednak więcej kodu teraz niż w oryginalnym, co oznacza więcej kosztów konserwacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="ffb30-243">Należy przyjąć strategii buforowania, tylko wtedy, gdy wykryto problemy z wydajnością, narzędzia PerfView wykazało, że <xref:System.Text.StringBuilder> są znaczące współautora.</span><span class="sxs-lookup"><span data-stu-id="ffb30-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span> 
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="ffb30-244">LINQ i wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="ffb30-244">LINQ and lambdas</span></span>  
<span data-ttu-id="ffb30-245">Language-Integrated Query (LINQ), w połączeniu z wyrażenia lambda jest przykładem funkcji produktywności.</span><span class="sxs-lookup"><span data-stu-id="ffb30-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="ffb30-246">Jednak jego użycia może mieć znaczący wpływ na wydajność wraz z upływem czasu i może się okazać, że trzeba poprawić kod.</span><span class="sxs-lookup"><span data-stu-id="ffb30-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="ffb30-247">**Przykład 5: Wyrażenia lambda, lista\<T >, a IEnumerable\<T >**</span><span class="sxs-lookup"><span data-stu-id="ffb30-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="ffb30-248">W tym przykładzie użyto [LINQ i funkcjonalności stylu kodu](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) można znaleźć symbolu w modelu kompilatora podany ciąg nazwy:</span><span class="sxs-lookup"><span data-stu-id="ffb30-248">This example uses [LINQ and functional style code](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 <span data-ttu-id="ffb30-249">Nowy kompilator i środowisk IDE zbudowane na nim wywołania `FindMatchingSymbol()` bardzo często i są kilka ukryte alokacji w tej funkcji nawet jednego wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="ffb30-250">Aby zbadać te przydziały, najpierw podzielić funkcji nawet jednego wiersza kodu dwa wiersze:</span><span class="sxs-lookup"><span data-stu-id="ffb30-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="ffb30-251">W pierwszym wierszu [wyrażenia lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [zamyka za pośrednictwem](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) zmienna lokalna `name`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-251">In the first line, the [lambda expression](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) the local variable `name`.</span></span> <span data-ttu-id="ffb30-252">Oznacza to, że oprócz przydzielanie obiektu dla [delegować](~/docs/csharp/language-reference/keywords/delegate.md) , `predicate` przechowuje, kod przydziela klasy statycznej, aby pomieścić środowisko, które przechwytuje wartość `name`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-252">This means that in addition to allocating an object for the [delegate](~/docs/csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="ffb30-253">Kompilator generuje kod, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="ffb30-253">The compiler generates code like the following:</span></span>  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 <span data-ttu-id="ffb30-254">Dwa `new` alokacje (jeden dla klasy środowiska) i jeden dla delegata jawne są teraz.</span><span class="sxs-lookup"><span data-stu-id="ffb30-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span> 
  
 <span data-ttu-id="ffb30-255">Teraz sprawdźmy wywołanie `FirstOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="ffb30-256">Ta metoda rozszerzenia na <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typu jest zbyt naliczana alokacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="ffb30-257">Ponieważ `FirstOrDefault` przyjmuje <xref:System.Collections.Generic.IEnumerable%601> obiektu jako pierwszego argumentu, można rozwinąć wywołanie następujący kod (uproszczony nieco dla dyskusji):</span><span class="sxs-lookup"><span data-stu-id="ffb30-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ... 
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 <span data-ttu-id="ffb30-258">`symbols` Zmienna ma typ <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="ffb30-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ffb30-259"><xref:System.Collections.Generic.List%601> Kolekcji typ implementuje <xref:System.Collections.Generic.IEnumerable%601> i sprytnie definiuje moduł wyliczający (<xref:System.Collections.Generic.IEnumerator%601> interfejsu) który <xref:System.Collections.Generic.List%601> implementuje z `struct`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="ffb30-260">Przy użyciu struktury zamiast klasy oznacza, że zwykle należy unikać Alokacje sterty, które z kolei może mieć wpływ na wydajność odzyskiwania pamięci zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="ffb30-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="ffb30-261">Moduły wyliczające są zwykle używane w języku `foreach` pętli, która używa struktury modułu wyliczającego, ponieważ jest on zwracany w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="ffb30-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="ffb30-262">Zwiększanie wskaźnika stosu wywołań, aby zwolnić miejsce dla obiektu nie wpływa na tak jak w alokacji sterty GC.</span><span class="sxs-lookup"><span data-stu-id="ffb30-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span> 
  
 <span data-ttu-id="ffb30-263">W przypadku rozwiniętym okienku `FirstOrDefault` wywołaniu, kod musi wywołać `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ffb30-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="ffb30-264">Przypisywanie `symbols` do `enumerable` zmiennej typu `IEnumerable<Symbol>` utraci informacje faktyczny obiekt <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="ffb30-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ffb30-265">Oznacza to, że gdy kod pobiera moduł wyliczający z `enumerable.GetEnumerator()`, ma pola zwróconej struktury, aby przypisać je do programu .NET Framework `enumerator` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span> 
  
 <span data-ttu-id="ffb30-266">**Na przykład rozwiązać 5**</span><span class="sxs-lookup"><span data-stu-id="ffb30-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="ffb30-267">Obejście polega na edycji `FindMatchingSymbol` następująco, zastępując sześć wierszy kodu, które są nadal zwięzły, łatwe do odczytania i zinterpretowania i łatwa w obsłudze jego nawet jednego wiersza kodu:</span><span class="sxs-lookup"><span data-stu-id="ffb30-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 <span data-ttu-id="ffb30-268">Ten kod nie korzysta z metod rozszerzeń LINQ, wyrażenia lambda lub moduły wyliczające i wiąże się nie alokacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="ffb30-269">Istnieją nie alokacji, ponieważ kompilator może być wyświetlana `symbols` kolekcja jest <xref:System.Collections.Generic.List%601> i może powiązać wynikowy modułu wyliczającego (struktury) do zmiennej lokalnej przy użyciu właściwego typu, aby uniknąć pakowania.</span><span class="sxs-lookup"><span data-stu-id="ffb30-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="ffb30-270">Oryginalna wersja tej funkcji został świetny przykład wszechstronnym możliwościom języka C# i efektywność programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ffb30-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="ffb30-271">Ta wersja nowe i bardziej wydajne zachowuje tych klas bez dodawania żadnych złożonego kodu do konserwowania.</span><span class="sxs-lookup"><span data-stu-id="ffb30-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span> 
  
### <a name="async-method-caching"></a><span data-ttu-id="ffb30-272">Buforowanie metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="ffb30-272">Async method caching</span></span>  

<span data-ttu-id="ffb30-273">W kolejnym przykładzie pokazano powszechny problem podczas próby użycia pamięci podręcznej powoduje [async](../../csharp/programming-guide/concepts/async/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ffb30-273">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="ffb30-274">**Przykład 6: buforowanie w metodach asynchronicznych**</span><span class="sxs-lookup"><span data-stu-id="ffb30-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="ffb30-275">Funkcje środowiska IDE programu Visual Studio, zbudowany na nowej Kompilatory języka C# i Visual Basic często pobrać drzewa składni i kompilatorów zachować za pomocą async czyniąc programu Visual Studio dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="ffb30-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="ffb30-276">Poniżej przedstawiono pierwszą wersję kodu, który może zapisać, można pobrać drzewa składni:</span><span class="sxs-lookup"><span data-stu-id="ffb30-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="ffb30-277">Widać, że wywołanie `GetSyntaxTreeAsync()` tworzy `Parser`, analizuje kod, a następnie zwraca <xref:System.Threading.Tasks.Task> obiektu `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="ffb30-278">Przydzielanie jest kosztowne część `Parser` wystąpienie i analizy kodu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="ffb30-279">Funkcja zwraca <xref:System.Threading.Tasks.Task> tak, aby obiekty wywołujące mogą await pracy analizy i bezpłatnie przez wątek interfejsu użytkownika, aby reagować na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ffb30-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span> 
  
 <span data-ttu-id="ffb30-280">Kilka funkcji programu Visual Studio może próbować uzyskać tym samym drzewie składni, dzięki czemu można napisać następujący kod do Zbuforuj wynik analizy, aby oszczędzić czas i alokacje.</span><span class="sxs-lookup"><span data-stu-id="ffb30-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="ffb30-281">Jednak ten kod powoduje alokację:</span><span class="sxs-lookup"><span data-stu-id="ffb30-281">However, this code incurs an allocation:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 <span data-ttu-id="ffb30-282">Możesz zobaczyć, że nowy kod za pomocą pamięci podręcznej ma `SyntaxTree` pole o nazwie `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="ffb30-283">Gdy to pole ma wartość null, `GetSyntaxTreeAsync()` wykonuje pracę i zapisuje wynik w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="ffb30-284">`GetSyntaxTreeAsync()` Zwraca `SyntaxTree` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ffb30-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="ffb30-285">Ten problem występuje wtedy, gdy masz `async` — funkcja typu `Task<SyntaxTree>`, i zwracanie wartości typu `SyntaxTree`, kompilator generuje kod do przydzielania zadań do przechowywania wyników (przy użyciu `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="ffb30-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="ffb30-286">Zadanie jest oznaczone jako ukończone, a wynik jest natychmiast dostępna.</span><span class="sxs-lookup"><span data-stu-id="ffb30-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="ffb30-287">W kodzie dla nowych kompilatorów <xref:System.Threading.Tasks.Task> obiektów, które już zakończono wystąpił tak często oznacza naprawiania tych przydziałów zwiększona szybkość reakcji znacznie.</span><span class="sxs-lookup"><span data-stu-id="ffb30-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span> 
  
 <span data-ttu-id="ffb30-288">**Na przykład rozwiązać 6**</span><span class="sxs-lookup"><span data-stu-id="ffb30-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="ffb30-289">Aby usunąć ukończoną <xref:System.Threading.Tasks.Task> alokacji, można buforować obiekt zadania z wynikiem zakończone:</span><span class="sxs-lookup"><span data-stu-id="ffb30-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??   
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="ffb30-290">Ten kod zmienia typ `cachedResult` do `Task<SyntaxTree>` i stosuje `async` funkcja pomocnicza, która zawiera oryginalny kod z `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="ffb30-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="ffb30-291">`GetSyntaxTreeAsync()` używa teraz [null operatora łączącego](../../csharp/language-reference/operators/null-coalescing-operator.md) do zwrócenia `cachedResult` Jeśli nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="ffb30-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="ffb30-292">Jeśli `cachedResult` ma wartość null, następnie `GetSyntaxTreeAsync()` wywołania `GetSyntaxTreeUncachedAsync()` i zapisuje wynik w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="ffb30-293">Należy zauważyć, że `GetSyntaxTreeAsync()` nie await wywołanie `GetSyntaxTreeUncachedAsync()` jako kod normalny.</span><span class="sxs-lookup"><span data-stu-id="ffb30-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="ffb30-294">Nie używa await oznacza że w przypadku `GetSyntaxTreeUncachedAsync()` zwraca jego <xref:System.Threading.Tasks.Task> obiektu `GetSyntaxTreeAsync()` natychmiast zwraca <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="ffb30-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="ffb30-295">Teraz jest buforowany wynik <xref:System.Threading.Tasks.Task>, więc nie ma żadnych alokacji do zwrócenia wyniku pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span> 
  
### <a name="additional-considerations"></a><span data-ttu-id="ffb30-296">Dodatkowe zagadnienia</span><span class="sxs-lookup"><span data-stu-id="ffb30-296">Additional considerations</span></span>  
 <span data-ttu-id="ffb30-297">Poniżej przedstawiono kilka więcej punktów o potencjalnych problemach w dużych aplikacji lub aplikacji, które przetwarzają dużą ilość danych.</span><span class="sxs-lookup"><span data-stu-id="ffb30-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span> 
  
 <span data-ttu-id="ffb30-298">**słowniki**</span><span class="sxs-lookup"><span data-stu-id="ffb30-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="ffb30-299">Słowniki są używane w wielu programach w ubiquitously i mimo że słowniki są bardzo wygodny i wydajny założenia.</span><span class="sxs-lookup"><span data-stu-id="ffb30-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="ffb30-300">Jednak często służą one niewłaściwie.</span><span class="sxs-lookup"><span data-stu-id="ffb30-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="ffb30-301">W Visual Studio i nowe kompilatory analizy pokazuje, że wiele słowników zawiera pojedynczy element lub były puste.</span><span class="sxs-lookup"><span data-stu-id="ffb30-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="ffb30-302">Pusta <xref:System.Collections.Generic.Dictionary%602> ma dziesięć pola i zajmuje 48 bajtów na stosie na x86 maszyny.</span><span class="sxs-lookup"><span data-stu-id="ffb30-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="ffb30-303">Słowniki to idealne rozwiązanie w przypadku, gdy będziesz potrzebować mapowanie lub asocjacyjnych struktury danych z wyszukiwanie w czasie stałym.</span><span class="sxs-lookup"><span data-stu-id="ffb30-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="ffb30-304">Jednak jeśli masz tylko kilka elementów, możesz tracić dużo miejsca za pomocą słownika.</span><span class="sxs-lookup"><span data-stu-id="ffb30-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="ffb30-305">Zamiast tego, na przykład, można wielokrotnie poszukać za pośrednictwem `List<KeyValuePair\<K,V>>`, po prostu tak szybko.</span><span class="sxs-lookup"><span data-stu-id="ffb30-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="ffb30-306">Jeśli używasz słownik tylko do załadować je z danymi, a następnie zapoznaj się z niego (bardzo typowy wzorzec) posortowaną tablicę przy użyciu wyszukiwania N(log(N)) może być prawie jako szybkiego działania, w zależności od liczby elementów, których używasz.</span><span class="sxs-lookup"><span data-stu-id="ffb30-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span> 
  
 <span data-ttu-id="ffb30-307">**Klas lub struktur**</span><span class="sxs-lookup"><span data-stu-id="ffb30-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="ffb30-308">W sposób bezpieczny klas i struktur Obejmij kosztem klasycznego miejsca/godziny dostosowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffb30-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="ffb30-309">Klasy pociągnąć za sobą 12-bajtowy obciążenie x86 komputera, nawet jeśli mają one żadnych pól, ale są one niedrogie w celu przejścia wokół, ponieważ tylko pobiera wskaźnik do odwoływania się do wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="ffb30-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="ffb30-310">Struktury pociągnąć za sobą nie alokacji sterty, jeśli nie są one zapakowany, ale podczas przekazywania dużych struktury jako argumenty funkcji lub zwracania wartości zajmuje trochę czasu procesora CPU niepodzielne skopiować wszystkie składowe danych struktury.</span><span class="sxs-lookup"><span data-stu-id="ffb30-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="ffb30-311">Zwróć uwagę na wielokrotnego wywołania do właściwości, które zwracają struktur i wartości właściwości w zmiennej lokalnej, aby uniknąć nadmiernego kopiowania danych w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span> 
  
 <span data-ttu-id="ffb30-312">**Caches**</span><span class="sxs-lookup"><span data-stu-id="ffb30-312">**Caches**</span></span>  
  
 <span data-ttu-id="ffb30-313">Typowe wydajności jest do wyników z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="ffb30-314">Jednak bez zasad zakończenia lub usuwania rozmiar pamięci podręcznej może być przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="ffb30-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="ffb30-315">Podczas przetwarzania dużych ilości danych, jeśli przytrzymasz dużej ilości pamięci w pamięci podręcznej, można wywołać wyrzucanie elementów bezużytecznych zastąpić korzyści wynikające z Twojej wyszukiwań w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ffb30-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span> 
  
 <span data-ttu-id="ffb30-316">W tym artykule omówiono, jak należy pamiętać o objawy wąskich gardeł wydajności, które mogą wpływać na czas reakcji aplikacji, szczególnie w przypadku dużych systemów i systemów, które przetwarzają duże ilości danych.</span><span class="sxs-lookup"><span data-stu-id="ffb30-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="ffb30-317">Typowe sprawcami obejmują pakowania, działań na ciągach, LINQ i lambda, buforowania w metodach asynchronicznych, buforowanie bez rozmiar limit lub usuwania zasad, nieodpowiednie użycie słowniki i przekazywanie wokół struktury.</span><span class="sxs-lookup"><span data-stu-id="ffb30-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="ffb30-318">Należy pamiętać, cztery fakty dostrojenia aplikacji:</span><span class="sxs-lookup"><span data-stu-id="ffb30-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
-   <span data-ttu-id="ffb30-319">Nie przedwcześnie Optymalizuj — produktywności i dostrajanie aplikacji, gdy zauważać problemy.</span><span class="sxs-lookup"><span data-stu-id="ffb30-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span> 
  
-   <span data-ttu-id="ffb30-320">Profile nie leży — jesteś zgadywania, jeśli nie pomiarowego.</span><span class="sxs-lookup"><span data-stu-id="ffb30-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span> 
  
-   <span data-ttu-id="ffb30-321">Dobre narzędzia zależy od — Pobierz narzędzia PerfView i wypróbuj jej działanie.</span><span class="sxs-lookup"><span data-stu-id="ffb30-321">Good tools make all the difference – download PerfView and try it out.</span></span> 
  
-   <span data-ttu-id="ffb30-322">To wszystko o alokacji — oznacza to, gdzie zespół platformy kompilatora poświęcony większość czasu poprawę wydajności nowych kompilatory.</span><span class="sxs-lookup"><span data-stu-id="ffb30-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="ffb30-323">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffb30-323">See also</span></span>

- [<span data-ttu-id="ffb30-324">Film wideo: prezentacja części tego tematu</span><span class="sxs-lookup"><span data-stu-id="ffb30-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="ffb30-325">Profilowanie wydajności — przewodnik dla początkujących</span><span class="sxs-lookup"><span data-stu-id="ffb30-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="ffb30-326">Wydajność</span><span class="sxs-lookup"><span data-stu-id="ffb30-326">Performance</span></span>](../../../docs/framework/performance/index.md)
- [<span data-ttu-id="ffb30-327">Wskazówki dotyczące wydajności .NET</span><span class="sxs-lookup"><span data-stu-id="ffb30-327">.NET Performance Tips</span></span>](https://msdn.microsoft.com/library/ms973839.aspx)
- [<span data-ttu-id="ffb30-328">Narzędzie do analizy wydajności Windows Phone</span><span class="sxs-lookup"><span data-stu-id="ffb30-328">Windows Phone Performance Analysis Tool</span></span>](https://msdn.microsoft.com/magazine/hh781024.aspx)
- [<span data-ttu-id="ffb30-329">Znajdź wąskie gardła za pomocą programu Visual Studio Profiler</span><span class="sxs-lookup"><span data-stu-id="ffb30-329">Find Application Bottlenecks with Visual Studio Profiler</span></span>](https://msdn.microsoft.com/magazine/cc337887.aspx)
- [<span data-ttu-id="ffb30-330">Channel 9 samouczki narzędzia PerfView</span><span class="sxs-lookup"><span data-stu-id="ffb30-330">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="ffb30-331">Zestaw SDK platformy kompilatora .NET</span><span class="sxs-lookup"><span data-stu-id="ffb30-331">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="ffb30-332">repozytorium DotNet/roslyn w witrynie GitHub</span><span class="sxs-lookup"><span data-stu-id="ffb30-332">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
