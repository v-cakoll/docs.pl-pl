---
title: "Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.workload: wiwagn
ms.openlocfilehash: ac4052773044e44f546894a54dc21728dbd6634a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="f230a-102">Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f230a-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="f230a-103">Ten artykuł zawiera wskazówki dotyczące poprawy wydajności dużych aplikacji .NET Framework lub aplikacje, które przetwarzają dużą ilość danych, takich jak pliki lub bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f230a-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="f230a-104">Te wskazówki pochodzi z ponowne zapisywanie C# i Visual Basic kompilatory w kodzie zarządzanym i ten artykuł zawiera kilka przykładów rzeczywistych kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="f230a-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>  
  
 <span data-ttu-id="f230a-105">.NET Framework jest wydajne do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-105">The .NET Framework is highly productive for building apps.</span></span>  <span data-ttu-id="f230a-106">Wydajne i bezpieczne i sformatowanego kolekcja bibliotek upewnij wysokiej owocnej Kompilowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span>  <span data-ttu-id="f230a-107">Jednak z doskonałą wydajność jest dostarczany odpowiedzialności.</span><span class="sxs-lookup"><span data-stu-id="f230a-107">However, with great productivity comes responsibility.</span></span>  <span data-ttu-id="f230a-108">Należy wykorzystać wszystkie możliwości programu .NET Framework, ale można go przygotować do dopasowywania wydajności swój kod w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="f230a-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>  
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="f230a-109">Dlaczego nowe wydajności kompilatora ma zastosowanie do aplikacji</span><span class="sxs-lookup"><span data-stu-id="f230a-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="f230a-110">Zespół platformy kompilatora .NET ("Roslyn") rewrote C# i Kompilatory języka Visual Basic w zarządzany kod, aby podać nowe interfejsy API do modelowania i analizowanie kodu, narzędzia do tworzenia i włączania znacznie bardziej rozbudowane, obsługujący kod doświadczeń w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f230a-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span>  <span data-ttu-id="f230a-111">Ponowne zapisywanie kompilatory i kompilowania programu Visual Studio doświadczeń w nowych kompilatory ujawniony szczegółowe informacje o wydajności przydatne mających zastosowanie do wszystkich dużych aplikacji .NET Framework lub dowolną aplikację, która przetwarza dużą ilość danych.</span><span class="sxs-lookup"><span data-stu-id="f230a-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span>  <span data-ttu-id="f230a-112">Nie trzeba wiedzieć o kompilatory przeprowadzać szczegółowe informacje i przykłady kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="f230a-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>  
  
 <span data-ttu-id="f230a-113">Visual Studio będzie korzystać kompilatora interfejsów API do tworzenia wszystkie funkcje IntelliSense, które użytkownicy lubią, takie jak zygzaki kolorowania identyfikatorów i słów kluczowych, listy uzupełniania składni, błędów, parametr porady, problemy z kodem i działania kodu.</span><span class="sxs-lookup"><span data-stu-id="f230a-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span>  <span data-ttu-id="f230a-114">Visual Studio zapewnia tę pomoc podczas Deweloperzy są wpisując i zmiany ich kodu i Visual Studio musi pozostać odpowiadać podczas kompilator stale modele deweloperom edytowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="f230a-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>  
  
 <span data-ttu-id="f230a-115">Gdy użytkownikom końcowym interakcję z aplikacją, ich powinien odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="f230a-115">When your end users interact with your app, they expect it to be responsive.</span></span>  <span data-ttu-id="f230a-116">Wpisywanie lub Obsługa polecenia nigdy nie powinien zostać zablokowany.</span><span class="sxs-lookup"><span data-stu-id="f230a-116">Typing or command handling should never be blocked.</span></span>  <span data-ttu-id="f230a-117">Pomoc powinna wyskakujące szybko lub zrezygnować, jeśli użytkownik nie zniknie, wpisując polecenie.</span><span class="sxs-lookup"><span data-stu-id="f230a-117">Help should pop up quickly or give up if the user continues typing.</span></span>  <span data-ttu-id="f230a-118">Aplikację należy unikać blokowania wątku interfejsu użytkownika o długie obliczeń zapewnić, że wolna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>  
  
 <span data-ttu-id="f230a-119">Aby uzyskać więcej informacji na temat kompilatory Roslyn, odwiedź stronę [dotnet/roslyn](https://github.com/dotnet/roslyn) repozytorium w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="f230a-119">For more information about Roslyn compilers, visit the [dotnet/roslyn](https://github.com/dotnet/roslyn) repo on GitHub.</span></span>
 <!-- TODO: replace with link to Roslyn conceptual docs once that's published -->
  
## <a name="just-the-facts"></a><span data-ttu-id="f230a-120">Po prostu faktów</span><span class="sxs-lookup"><span data-stu-id="f230a-120">Just the Facts</span></span>  
 <span data-ttu-id="f230a-121">Należy wziąć pod uwagę następujące fakty podczas dostrajania wydajności i tworzenia reakcji aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f230a-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>  
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="f230a-122">Fakt 1: Przedwcześnie nie optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="f230a-123">Pisanie kodu, który jest bardziej złożone niż musi on być wiąże konserwacji, debugowanie i wygładzanie kosztów.</span><span class="sxs-lookup"><span data-stu-id="f230a-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span>  <span data-ttu-id="f230a-124">Doświadczeni programiści ma intuicyjne ujmij sposobu rozwiązywania problemów kodowania i większą wydajność w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f230a-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span>  <span data-ttu-id="f230a-125">Jednak ich czasami przedwcześnie optymalizacji ich kodu.</span><span class="sxs-lookup"><span data-stu-id="f230a-125">However, they sometimes prematurely optimize their code.</span></span>  <span data-ttu-id="f230a-126">Na przykład używa tablicy skrótów przy proste tablicy może wystarczyć lub Używaj buforowania skomplikowane, który dochodzi do wycieku pamięci zamiast po prostu recomputing wartości.</span><span class="sxs-lookup"><span data-stu-id="f230a-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span>  <span data-ttu-id="f230a-127">Nawet jeśli programista środowisko, należy testowanie wydajności i analizowania kodu w przypadku napotkania problemów.</span><span class="sxs-lookup"><span data-stu-id="f230a-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>  
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="f230a-128">Fakt 2: Jeśli nie notuje, użytkownik jest odgadnięcie</span><span class="sxs-lookup"><span data-stu-id="f230a-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="f230a-129">Profile i pomiarów nie znajdują się.</span><span class="sxs-lookup"><span data-stu-id="f230a-129">Profiles and measurements don’t lie.</span></span>  <span data-ttu-id="f230a-130">Profili wyświetlić czy Procesora jest w pełni załadowany lub czy jest zablokowany na We/Wy dysku.</span><span class="sxs-lookup"><span data-stu-id="f230a-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span>  <span data-ttu-id="f230a-131">Profile wyświetla komunikat informujący o tym, jakiego rodzaju i ilość pamięci w przypadku alokowania i czy ten Procesor zużywa dużo czasu, w [wyrzucanie elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="f230a-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../../docs/standard/garbage-collection/index.md) (GC).</span></span>  
  
 <span data-ttu-id="f230a-132">Należy ustawić cele dotyczące wydajności dla klucza klienta środowiska lub scenariuszy w aplikacji i napisać testy do pomiaru wydajności.</span><span class="sxs-lookup"><span data-stu-id="f230a-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span>  <span data-ttu-id="f230a-133">Zbadaj w przypadku braku testy, stosując metodę wykładniczej: Profile umożliwiają pomocne, można przyjąć hipotezę, co może być problem i przetestować użytkownika hipoteza z eksperyment lub zmiany kodu.</span><span class="sxs-lookup"><span data-stu-id="f230a-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span>  <span data-ttu-id="f230a-134">Ustanowić miary wydajności bazowej wraz z upływem czasu z testowaniem regularnie, więc można odizolować zmiany, które powodują regresji w wydajności.</span><span class="sxs-lookup"><span data-stu-id="f230a-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span>  <span data-ttu-id="f230a-135">W sposób rygorystyczne zbliża się wydajność pracy, będzie uniknąć traci czasu z aktualizacjami kodu, które nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="f230a-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>  
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="f230a-136">Fakt 3: Dobrej narzędziom do wszystkich różnicy</span><span class="sxs-lookup"><span data-stu-id="f230a-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="f230a-137">Dobrym narzędzia pozwalają szybko przejść do szczegółów największych problemy z wydajnością (procesora CPU, pamięć lub dysk) i pomocy możesz znaleźć kod, który powoduje, że te wąskich gardeł.</span><span class="sxs-lookup"><span data-stu-id="f230a-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span>  <span data-ttu-id="f230a-138">Microsoft dostarczany różnych narzędzi wydajności, takich jak [programu Visual Studio profilera](/visualstudio/profiling/beginners-guide-to-performance-profiling), [narzędzie do analizy Windows Phone](http://msdn.microsoft.com/en-us/e67e3199-ea43-4d14-ab7e-f7f19266253f), i [narzędzia PerfView](http://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="f230a-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone Analysis Tool](http://msdn.microsoft.com/en-us/e67e3199-ea43-4d14-ab7e-f7f19266253f), and [PerfView](http://www.microsoft.com/download/details.aspx?id=28567).</span></span>  
  
 <span data-ttu-id="f230a-139">Narzędzia PerfView jest bezpłatny i zdumiewająco zaawansowane narzędzie, które pozwala skupić się na bezpośrednich problemów, takich jak We/Wy dysku, zdarzenia GC i pamięci.</span><span class="sxs-lookup"><span data-stu-id="f230a-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span>  <span data-ttu-id="f230a-140">Można przechwycić związanych z wydajnością [śledzenia zdarzeń dla systemu Windows](../../../docs/framework/wcf/samples/etw-tracing.md) zdarzeń (ETW) i widoku łatwo na aplikacji, na proces, na stosie i na informacje o wątku.</span><span class="sxs-lookup"><span data-stu-id="f230a-140">You can capture performance-related [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span>  <span data-ttu-id="f230a-141">Narzędzia PerfView pokazuje, ile i jakie rodzaj pamięci są przydzielane aplikacji, które funkcje i wywołania stosy współtworzyć ile alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="f230a-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="f230a-142">Aby uzyskać więcej informacji, zobacz sformatowanego tematy pomocy, pokazy i filmy wideo uwzględnione za pomocą narzędzia (takie jak [samouczki narzędzia PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial) witrynie Channel 9).</span><span class="sxs-lookup"><span data-stu-id="f230a-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](http://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>  
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="f230a-143">Fakt 4: Przede wszystkim chodzi o alokacji</span><span class="sxs-lookup"><span data-stu-id="f230a-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="f230a-144">Może się okazać, że tworzenie dynamiczne aplikacja .NET Framework jest wszystkie informacje dotyczące algorytmów, takich jak użycie szybkiego sortowania zamiast bąbelków sortowania, ale nie jest to.</span><span class="sxs-lookup"><span data-stu-id="f230a-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span>  <span data-ttu-id="f230a-145">Współczynnik największych z tworzeniem reakcji aplikacji jest przydzielenie pamięci, szczególnie w przypadku, gdy aplikacja jest bardzo duże lub przetwarzania dużych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="f230a-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>  
  
 <span data-ttu-id="f230a-146">Prawie wszystkie wykonywania pracy, aby utworzyć odpowiednie środowisko IDE przez kompilator nowych interfejsów API zaangażowane unikanie alokacji i zarządzanie strategii buforowania.</span><span class="sxs-lookup"><span data-stu-id="f230a-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span>  <span data-ttu-id="f230a-147">Ślady narzędzia PerfView pokazują, że wydajność nowej Kompilatory języka C# i Visual Basic rzadko jest powiązany procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="f230a-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span>  <span data-ttu-id="f230a-148">Kompilatory może być we/wy powiązany podczas odczytywania setki tysięcy lub miliony wierszy kodu, odczytywanie metadanych, lub emitowanie wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="f230a-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span>  <span data-ttu-id="f230a-149">Opóźnienia wątku interfejsu użytkownika są prawie wszystkie ze względu na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f230a-149">The UI thread delays are nearly all due to garbage collection.</span></span>  <span data-ttu-id="f230a-150">.NET Framework GC wysokiej dostosowana pod kątem wydajności i wykona większość pracy, jednocześnie, gdy kod aplikacji jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="f230a-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span>  <span data-ttu-id="f230a-151">Jednak pojedynczy alokacji może wyzwolić kosztowne [gen2](../../../docs/standard/garbage-collection/fundamentals.md) kolekcji zatrzymywanie wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="f230a-151">However, a single allocation can trigger an expensive [gen2](../../../docs/standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>  
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="f230a-152">Typowe przykłady i alokacji</span><span class="sxs-lookup"><span data-stu-id="f230a-152">Common allocations and examples</span></span>  
 <span data-ttu-id="f230a-153">Przykładowe wyrażenia w tej sekcji zostały ukryte przydziałów, które są niewielkie.</span><span class="sxs-lookup"><span data-stu-id="f230a-153">The example expressions in this section have hidden allocations that appear small.</span></span>  <span data-ttu-id="f230a-154">Jednak jeśli dużych aplikacji wykonuje wyrażeń razy, ich można przyczyny setki megabajtów, nawet gigabajtów alokacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span>  <span data-ttu-id="f230a-155">Na przykład co minutę testy symulowane developer, wpisując w edytorze przydzielone gigabajtów pamięci, które doprowadziły zespołu wydajności skupić się na wpisanie scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f230a-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>  
  
### <a name="boxing"></a><span data-ttu-id="f230a-156">Boxing</span><span class="sxs-lookup"><span data-stu-id="f230a-156">Boxing</span></span>  
 <span data-ttu-id="f230a-157">[Konwersja boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) występuje, gdy wartość typy, które zwykle na żywo na stosie lub w danych struktury są pakowane w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="f230a-157">[Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span>  <span data-ttu-id="f230a-158">Oznacza to przydzielić obiektu w celu przechowywania danych, a następnie zwraca wskaźnik do obiektu.</span><span class="sxs-lookup"><span data-stu-id="f230a-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span>  <span data-ttu-id="f230a-159">.NET Framework czasami pola wartości z powodu podpisu metody lub typu lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="f230a-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span>  <span data-ttu-id="f230a-160">Zawijanie typu wartości w alokacji pamięci powoduje, że obiekt.</span><span class="sxs-lookup"><span data-stu-id="f230a-160">Wrapping a value type in an object causes memory allocation.</span></span>  <span data-ttu-id="f230a-161">Wiele operacji opakowanie może przyczynić się w megabajtach lub gigabajtach alokacji do aplikacji, co oznacza, że więcej GC spowoduje, że aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f230a-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="f230a-162">.NET Framework i Kompilatory języka uniknąć pakującej, gdy jest to możliwe, ale czasami występuje, jeśli oczekujesz najmniej.</span><span class="sxs-lookup"><span data-stu-id="f230a-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>  
  
 <span data-ttu-id="f230a-163">Aby wyświetlić opakowanie w narzędzia PerfView, otwórz śledzenia i przyjrzyj się stosy alokacji sterty GC pod nazwą procesu aplikacji (należy pamiętać, że narzędzia PerfView raporty dotyczące wszystkich procesów).</span><span class="sxs-lookup"><span data-stu-id="f230a-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span>  <span data-ttu-id="f230a-164">Jeśli widzisz wykresach <xref:System.Int32?displayProperty=nameWithType> i <xref:System.Char?displayProperty=nameWithType> w ramach przydziałów, są konwersja boxing typów wartości.</span><span class="sxs-lookup"><span data-stu-id="f230a-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span>  <span data-ttu-id="f230a-165">Wybranie jednej z tych typów zostaną wyświetlone stosy i funkcje, w których są ramce.</span><span class="sxs-lookup"><span data-stu-id="f230a-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>  
  
 <span data-ttu-id="f230a-166">**Przykład 1: string, metody i wartości argumentów typu**</span><span class="sxs-lookup"><span data-stu-id="f230a-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="f230a-167">Ten przykładowy kod przedstawia potencjalnie niepotrzebnych i nadmierne opakowanie:</span><span class="sxs-lookup"><span data-stu-id="f230a-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="f230a-168">Ten kod zawiera funkcje rejestrowania, aplikacja może wywołać `Log` często, funkcja może być miliony razy.</span><span class="sxs-lookup"><span data-stu-id="f230a-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span>  <span data-ttu-id="f230a-169">Problem jest wywołanie `string.Format` jest rozpoznawana jako <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="f230a-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>  
  
 <span data-ttu-id="f230a-170">To przeciążenie wymaga programu .NET Framework do pola `int` wartości do obiektów w celu przekazania ich wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="f230a-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span>  <span data-ttu-id="f230a-171">Częściowe poprawka jest wywołanie `id.ToString()` i `size.ToString()` i Przekaż wszystkie ciągi (które są obiektami) do `string.Format` wywołania.</span><span class="sxs-lookup"><span data-stu-id="f230a-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span>  <span data-ttu-id="f230a-172">Wywoływanie `ToString()` przydzielić ciągu, ale ten przydział nastąpi mimo to wewnątrz `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="f230a-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>  
  
 <span data-ttu-id="f230a-173">Należy rozważyć to tym podstawowe wywołanie `string.Format` jest po prostu ciągów, dlatego może być napisać ten kod:</span><span class="sxs-lookup"><span data-stu-id="f230a-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="f230a-174">Jednak wiersza kodu wprowadzono alokacji pakującej, ponieważ kompiluje się do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="f230a-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span>  <span data-ttu-id="f230a-175">.NET Framework musi polu znak literału do wywołania`Concat`</span><span class="sxs-lookup"><span data-stu-id="f230a-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="f230a-176">**Na przykład rozwiązać 1**</span><span class="sxs-lookup"><span data-stu-id="f230a-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="f230a-177">Zakończenie poprawka jest proste.</span><span class="sxs-lookup"><span data-stu-id="f230a-177">The complete fix is simple.</span></span>  <span data-ttu-id="f230a-178">Po prostu zastąpić literał znakowy z ciągiem literału, które generuje nie pakującej ponieważ ciągi są już obiekty:</span><span class="sxs-lookup"><span data-stu-id="f230a-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="f230a-179">**Przykład 2: opakowywanie wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="f230a-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="f230a-180">W tym przykładzie jest odpowiedzialny za ogromnych ilości alokacji w nowych Kompilatory języka C# i Visual Basic z powodu częste używanie typów wyliczenia, szczególnie w słowniku operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f230a-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>  
  
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
  
 <span data-ttu-id="f230a-181">Ten problem jest bardzo niewielkie.</span><span class="sxs-lookup"><span data-stu-id="f230a-181">This problem is very subtle.</span></span>  <span data-ttu-id="f230a-182">Narzędzia PerfView rozpoczną przesyłanie raportów jako <xref:System.Enum.GetHashCode> konwersja boxing, ponieważ metoda pola źródłowego reprezentacja typu wyliczenia ze względów implementacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span>  <span data-ttu-id="f230a-183">Jeśli narzędzia PerfView wyglądać ściśle, mogą pojawić się dwa pakującej alokacji dla każdego wywołania <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="f230a-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span>   <span data-ttu-id="f230a-184">Kompilator powoduje wstawienie jednego, a .NET Framework innych.</span><span class="sxs-lookup"><span data-stu-id="f230a-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span>  
  
 <span data-ttu-id="f230a-185">**Na przykład rozwiązać 2**</span><span class="sxs-lookup"><span data-stu-id="f230a-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="f230a-186">Łatwo można uniknąć zarówno alokacji przez rzutowanie do podstawowej reprezentacja przed wywołaniem <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="f230a-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="f230a-187">Inny wspólne źródło pakującej na typy wyliczeniowe jest <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f230a-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="f230a-188">Argument przekazany do <xref:System.Enum.HasFlag%28System.Enum%29> musi zostać opakowany.</span><span class="sxs-lookup"><span data-stu-id="f230a-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span>  <span data-ttu-id="f230a-189">W większości przypadków, zastępując wywołań <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> z bitowego testu jest prostsze i bez alokacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>  
  
 <span data-ttu-id="f230a-190">Pamiętać pierwszy fakt wydajności (to znaczy nie przedwcześnie Optymalizacja) i nie należy uruchamiać ponowne zapisanie całego kodu w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="f230a-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span>    <span data-ttu-id="f230a-191">Należy pamiętać o tych kosztów pakującej, ale Zmień swój kod, tylko po profilowania aplikacji i znajdowanie punkty aktywne.</span><span class="sxs-lookup"><span data-stu-id="f230a-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>  
  
### <a name="strings"></a><span data-ttu-id="f230a-192">Ciągi</span><span class="sxs-lookup"><span data-stu-id="f230a-192">Strings</span></span>  
 <span data-ttu-id="f230a-193">Na ciągach są niektóre z najważniejszych sprawcami dla alokacji i ich często wyświetlane w narzędzia PerfView w alokacjach 5.</span><span class="sxs-lookup"><span data-stu-id="f230a-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span>  <span data-ttu-id="f230a-194">Programy ciąg znaków używany do serializacji, JSON i interfejsów API REST.</span><span class="sxs-lookup"><span data-stu-id="f230a-194">Programs use strings for serialization, JSON, and REST APIs.</span></span>  <span data-ttu-id="f230a-195">Ciągi jako stałe programowe służącego do współpracy z systemów, gdy nie można użyć typów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f230a-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span>  <span data-ttu-id="f230a-196">Gdy Twoje profilowania pokazuje, że ciągi wysokiej mają wpływ na wydajność, wyszukaj wywołań <xref:System.String> metod, takich jak <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f230a-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span>  <span data-ttu-id="f230a-197">Przy użyciu <xref:System.Text.StringBuilder> Aby uniknąć kosztów Tworzenie ciągu z wielu części pomaga, ale nawet przydziału <xref:System.Text.StringBuilder> obiektu mogą stać się wąskiego gardła, które muszą zarządzać.</span><span class="sxs-lookup"><span data-stu-id="f230a-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>  
  
 <span data-ttu-id="f230a-198">**Przykład 3: operacje na ciągach**</span><span class="sxs-lookup"><span data-stu-id="f230a-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="f230a-199">Kompilator języka C# nie ten kod, który zapisuje tekst sformatowany komentarz dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="f230a-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="f230a-200">Widać, że ten kod wykonuje wiele manipulowanie ciągami.</span><span class="sxs-lookup"><span data-stu-id="f230a-200">You can see that this code does a lot of string manipulation.</span></span>  <span data-ttu-id="f230a-201">W kodzie użyto metody biblioteki podziału wierszy w oddzielnych ciągów, aby przyciąć biały znak, aby sprawdzić, czy argument `text` jest komentarz dokumentacji XML i wyodrębnić podciągów z wierszy.</span><span class="sxs-lookup"><span data-stu-id="f230a-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>  
  
 <span data-ttu-id="f230a-202">W pierwszym wierszu wewnątrz `WriteFormattedDocComment`, `text.Split` wywołanie za każdym razem, gdy jest ona wywoływana przydziela nowej tablicy elementu trzech jako argument.</span><span class="sxs-lookup"><span data-stu-id="f230a-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span>  <span data-ttu-id="f230a-203">Kompilator ma Emituj kod, aby przydzielić tej tablicy zawsze.</span><span class="sxs-lookup"><span data-stu-id="f230a-203">The compiler has to emit code to allocate this array each time.</span></span>  <span data-ttu-id="f230a-204">Wynika to z faktu kompilator nie może ustalić, czy <xref:System.String.Split%2A> przechowuje tablicy miejsce gdzie tablicy mogą zostać zmodyfikowane innego kodu, co może wpływać na nowsze wywołania `WriteFormattedDocComment`.</span><span class="sxs-lookup"><span data-stu-id="f230a-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span>  <span data-ttu-id="f230a-205">Wywołanie <xref:System.String.Split%2A> również przydziela ciąg dla każdego wiersza w `text` i przydziela innych pamięci do wykonania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>  
  
 <span data-ttu-id="f230a-206">`WriteFormattedDocComment`ma trzy wywołania <xref:System.String.TrimStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f230a-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span>  <span data-ttu-id="f230a-207">Dwa znajdują się w wewnętrznej pętle, zawierające zduplikowane pracy i alokacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-207">Two are in inner loops that duplicate work and allocations.</span></span>  <span data-ttu-id="f230a-208">Aby co gorsza sprawach, wywoływania <xref:System.String.TrimStart%2A> metody bez argumentów przydziela pustą tablicę (dla `params` parametru) oprócz wynik ciągu.</span><span class="sxs-lookup"><span data-stu-id="f230a-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>  
  
 <span data-ttu-id="f230a-209">Ponadto jest to wywołanie <xref:System.String.Substring%2A> metodę, która zwykle przydziela nowe parametry.</span><span class="sxs-lookup"><span data-stu-id="f230a-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>  
  
 <span data-ttu-id="f230a-210">**Na przykład rozwiązać 3**</span><span class="sxs-lookup"><span data-stu-id="f230a-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="f230a-211">W przeciwieństwie do wcześniejszych przykłady małych zmiany nie można naprawić tych przydziałów.</span><span class="sxs-lookup"><span data-stu-id="f230a-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span>  <span data-ttu-id="f230a-212">Musisz kroku Wstecz, obejrzyj ten problem i zbliżających się inaczej.</span><span class="sxs-lookup"><span data-stu-id="f230a-212">You need to step back, look at the problem, and approach it differently.</span></span>  <span data-ttu-id="f230a-213">Na przykład można zauważyć, że argument `WriteFormattedDocComment()` jest ciągiem, który ma wszystkie informacje o wymagające metody, więc kod może zrobić więcej indeksowania zamiast przydzielania wiele ciągi częściowe.</span><span class="sxs-lookup"><span data-stu-id="f230a-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>  
  
 <span data-ttu-id="f230a-214">Zespół wydajności kompilatora rozwiązywane tych przydziałów z kodem następująco:</span><span class="sxs-lookup"><span data-stu-id="f230a-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="f230a-215">Pierwszą wersję `WriteFormattedDocComment()` przydzielone tablicy, kilku podciągów i przycięte podciąg wraz z pustą `params` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f230a-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span>  <span data-ttu-id="f230a-216">On również sprawdzane pod kątem `"///"`.</span><span class="sxs-lookup"><span data-stu-id="f230a-216">It also checked for `"///"`.</span></span>  <span data-ttu-id="f230a-217">Poprawione kod używa tylko indeksowanie i przydziela nothing.</span><span class="sxs-lookup"><span data-stu-id="f230a-217">The revised code uses only indexing and allocates nothing.</span></span>  <span data-ttu-id="f230a-218">Znajdzie pierwszego znaku, który nie jest biały znak, a następnie sprawdza znak po znaku, aby zobaczyć, czy ciąg rozpoczyna się od `"///"`.</span><span class="sxs-lookup"><span data-stu-id="f230a-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with `"///"`.</span></span>  <span data-ttu-id="f230a-219">Nowy kod używa `IndexOfFirstNonWhiteSpaceChar` zamiast <xref:System.String.TrimStart%2A> do zwracania indeks pierwszego (po indeks datą początkową), w których występuje znak odstępem.</span><span class="sxs-lookup"><span data-stu-id="f230a-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-whitespace character occurs.</span></span>  <span data-ttu-id="f230a-220">Ta poprawka nie została ukończona, ale możesz dowiedzieć się, jak zastosować poprawki podobne do kompletnego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f230a-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span>  <span data-ttu-id="f230a-221">Przy zastosowaniu tej metody w całym kodzie, należy usunąć wszystkie alokacji w `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="f230a-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>  
  
 <span data-ttu-id="f230a-222">**Przykład 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="f230a-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="f230a-223">W tym przykładzie użyto <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f230a-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span>  <span data-ttu-id="f230a-224">Następująca funkcja generuje Pełna nazwa typu dla typów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="f230a-224">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="f230a-225">Koncentruje się na wiersz, który tworzy nową <xref:System.Text.StringBuilder> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f230a-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span>  <span data-ttu-id="f230a-226">Kod powoduje, że przydział `sb.ToString()` i wewnętrznych alokacji w <xref:System.Text.StringBuilder> implementacji, ale nie może kontrolować te przydziały, jeśli wynik ciąg.</span><span class="sxs-lookup"><span data-stu-id="f230a-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>  
  
 <span data-ttu-id="f230a-227">**Na przykład rozwiązać 4**</span><span class="sxs-lookup"><span data-stu-id="f230a-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="f230a-228">Aby naprawić `StringBuilder` obiekt alokacji, pamięci podręcznej obiektu.</span><span class="sxs-lookup"><span data-stu-id="f230a-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span>  <span data-ttu-id="f230a-229">Buforowanie nawet pojedyncze wystąpienie, które mogą uzyskać wyrzucać może znacząco zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="f230a-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span>  <span data-ttu-id="f230a-230">Jest to funkcja nowej implementacji, pomijając cały kod z wyjątkiem nowych wierszy imię i nazwisko:</span><span class="sxs-lookup"><span data-stu-id="f230a-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="f230a-231">Części klucza są nowe `AcquireBuilder()` i `GetStringAndReleaseBuilder()` funkcje:</span><span class="sxs-lookup"><span data-stu-id="f230a-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="f230a-232">Użyj pola statyczne dla wątku, nowe kompilatory używają wątków, tych implementacji (<xref:System.ThreadStaticAttribute> atrybut) do pamięci podręcznej <xref:System.Text.StringBuilder>, i prawdopodobnie można uniknąć `ThreadStatic` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f230a-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span>  <span data-ttu-id="f230a-233">Pole statyczne dla wątku zawiera unikatową wartość dla każdego wątku, który wykonuje ten kod.</span><span class="sxs-lookup"><span data-stu-id="f230a-233">The thread-static field holds a unique value for each thread that executes this code.</span></span>  
  
 <span data-ttu-id="f230a-234">`AcquireBuilder()`Zwraca buforowane <xref:System.Text.StringBuilder> wystąpienia, jeśli istnieje, po wyczyszczeniem i ustawienie pola lub pamięci podręcznej na wartość null.</span><span class="sxs-lookup"><span data-stu-id="f230a-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span>  <span data-ttu-id="f230a-235">W przeciwnym razie `AcquireBuilder()` tworzy nowe wystąpienie i zwraca go, pozostawiając pole lub pamięci podręcznej zestawu wartości null.</span><span class="sxs-lookup"><span data-stu-id="f230a-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>  
  
 <span data-ttu-id="f230a-236">Po zakończeniu z <xref:System.Text.StringBuilder> , należy wywołać `GetStringAndReleaseBuilder()` można pobrać wyniku ciągu, Zapisz <xref:System.Text.StringBuilder> wystąpienia w polu lub pamięci podręcznej, a następnie zwracają wynik.</span><span class="sxs-lookup"><span data-stu-id="f230a-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span>  <span data-ttu-id="f230a-237">Istnieje możliwość wykonywania ponowne wprowadzenie tego kodu i utworzyć wiele <xref:System.Text.StringBuilder> obiektów (chociaż tak się rzadko stanie).</span><span class="sxs-lookup"><span data-stu-id="f230a-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span>  <span data-ttu-id="f230a-238">Zapisuje kod wydane tylko ostatnich <xref:System.Text.StringBuilder> wystąpienie do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="f230a-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span>  <span data-ttu-id="f230a-239">To proste strategii buforowania znacznie zmniejszyć alokacji w nowych kompilatory.</span><span class="sxs-lookup"><span data-stu-id="f230a-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span>  <span data-ttu-id="f230a-240">Części programu .NET Framework i program MSBuild ("MSBuild") użyć technika podobne do zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="f230a-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>  
  
 <span data-ttu-id="f230a-241">To proste strategii buforowania opiera się na dobrej pamięci podręcznej, ponieważ ma ona limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="f230a-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span>  <span data-ttu-id="f230a-242">Istnieje jednak jeden kod teraz niż w oryginalnym, czyli więcej kosztów obsługi.</span><span class="sxs-lookup"><span data-stu-id="f230a-242">However, there is more code now than in the original, which means more maintenance costs.</span></span>  <span data-ttu-id="f230a-243">Powinna przyjąć strategii buforowania tylko wtedy, gdy uda Ci się znaleźć problemy z wydajnością i narzędzia PerfView wykazała, że <xref:System.Text.StringBuilder> są znaczące współautora.</span><span class="sxs-lookup"><span data-stu-id="f230a-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>  
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="f230a-244">LINQ i wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="f230a-244">LINQ and lambdas</span></span>  
 <span data-ttu-id="f230a-245">Za pomocą wyrażeń język Language-Integrated zapytania (LINQ) i lambda jest doskonałym przykładem zastosowania produktywności funkcje, które mogą być później potrzebne do edycji, gdy kod stanie się znaczący wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="f230a-245">Using Language-Integrated Query (LINQ) and lambda expressions is a great example of using productive features that you might later find you need to rewrite if the code becomes a significant impact on performance.</span></span>  
  
 <span data-ttu-id="f230a-246">**Przykład 5: Wyrażeń lambda, lista\<T >, a IEnumerable\<T >**</span><span class="sxs-lookup"><span data-stu-id="f230a-246">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="f230a-247">W tym przykładzie użyto [LINQ i kodu stylu funkcjonalności](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) można znaleźć symbolu w modelu kompilatora podany ciąg nazwy:</span><span class="sxs-lookup"><span data-stu-id="f230a-247">This example uses [LINQ and functional style code](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="f230a-248">Nowy kompilator i środowiska IDE oparty na jej wywołać `FindMatchingSymbol()` bardzo często i są kilka ukryte alokacji w tej funkcji w jednym wierszu kodu.</span><span class="sxs-lookup"><span data-stu-id="f230a-248">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span>  <span data-ttu-id="f230a-249">Badanie tych przydziałów, najpierw podzielić funkcji pojedynczy wiersz kodu na dwa wiersze:</span><span class="sxs-lookup"><span data-stu-id="f230a-249">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="f230a-250">W pierwszym wierszu [wyrażenia lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[zamyka za pośrednictwem](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) zmiennej lokalnej `name`.</span><span class="sxs-lookup"><span data-stu-id="f230a-250">In the first line, the [lambda expression](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[closes over](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) the local variable `name`.</span></span>  <span data-ttu-id="f230a-251">Oznacza to, że oprócz przydziału dla obiekt [delegować](~/docs/csharp/language-reference/keywords/delegate.md) który `predicate` zawiera kod przydziela Klasa statyczna przechowująca środowiska, który przechwytuje wartość `name`.</span><span class="sxs-lookup"><span data-stu-id="f230a-251">This means that in addition to allocating an object for the [delegate](~/docs/csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span>  <span data-ttu-id="f230a-252">Kompilator generuje kod podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="f230a-252">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="f230a-253">Dwa `new` (jeden dla klasy środowiska) i drugi dla obiekt delegowany są jawne teraz.</span><span class="sxs-lookup"><span data-stu-id="f230a-253">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>  
  
 <span data-ttu-id="f230a-254">Teraz wyglądać na wywołanie `FirstOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="f230a-254">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="f230a-255">Tę metodę rozszerzenie w <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typu generuje zbyt alokacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-255">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span>  <span data-ttu-id="f230a-256">Ponieważ `FirstOrDefault` przyjmuje <xref:System.Collections.Generic.IEnumerable%601> obiekt jako pierwszego argumentu, można rozszerzyć wywołanie następujący kod (uproszczony nieco omówienie):</span><span class="sxs-lookup"><span data-stu-id="f230a-256">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="f230a-257">`symbols` Zmienna ma typ <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f230a-257">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span>  <span data-ttu-id="f230a-258"><xref:System.Collections.Generic.List%601> Implementuje typ kolekcji <xref:System.Collections.Generic.IEnumerable%601> i sprytnie definiuje moduł wyliczający (<xref:System.Collections.Generic.IEnumerator%601> interfejsu) który <xref:System.Collections.Generic.List%601> implementuje z `struct`.</span><span class="sxs-lookup"><span data-stu-id="f230a-258">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span>  <span data-ttu-id="f230a-259">Za pomocą struktury zamiast klasy oznacza zwykle uniknąć Alokacje sterty, co z kolei może negatywnie wpłynąć na wydajność zbierania danych pamięci.</span><span class="sxs-lookup"><span data-stu-id="f230a-259">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span>  <span data-ttu-id="f230a-260">Moduły wyliczające są zazwyczaj używane w języku `foreach` pętli, który używa struktury modułu wyliczającego jest zwracany w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="f230a-260">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span>  <span data-ttu-id="f230a-261">Zwiększanie wskaźnik stosu wywołań, aby zwolnić miejsce dla obiekt nie ma wpływu na tak jak w alokacji sterty GC.</span><span class="sxs-lookup"><span data-stu-id="f230a-261">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>  
  
 <span data-ttu-id="f230a-262">W przypadku rozwinięte `FirstOrDefault` wywołanie, kod musi wywołać `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="f230a-262">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  <span data-ttu-id="f230a-263">Przypisywanie `symbols` do `enumerable` zmiennej typu `IEnumerable<Symbol>` utraci informacje rzeczywistego obiektu <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f230a-263">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span>  <span data-ttu-id="f230a-264">Oznacza to, że jeśli kod pobiera moduł wyliczający z `enumerable.GetEnumerator()`, .NET Framework ma pole zwrócony struktury można przypisać go do `enumerator` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f230a-264">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>  
  
 <span data-ttu-id="f230a-265">**Na przykład rozwiązać 5**</span><span class="sxs-lookup"><span data-stu-id="f230a-265">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="f230a-266">Rozwiązanie polega na edycji `FindMatchingSymbol` , zastępując jego pojedynczy wiersz kodu sześć wierszy kodu, które nadal zwięzła, łatwych do przeczytane i zrozumiane i łatwe w konserwacji:</span><span class="sxs-lookup"><span data-stu-id="f230a-266">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="f230a-267">Ten kod nie korzysta z metody rozszerzenia LINQ, wyrażenia lambda lub moduły wyliczające i wiąże się nie przydziału.</span><span class="sxs-lookup"><span data-stu-id="f230a-267">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span>  <span data-ttu-id="f230a-268">Ponieważ kompilator można stwierdzić, że istnieją nie przydziału `symbols` kolekcja jest <xref:System.Collections.Generic.List%601> i może powiązać wynikowy modułu wyliczającego (struktury) do zmiennej lokalnej z odpowiedniego typu, aby uniknąć boxing.</span><span class="sxs-lookup"><span data-stu-id="f230a-268">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span>  <span data-ttu-id="f230a-269">Oryginalną wersją z tej funkcji jest doskonałym przykładem wszechstronnym możliwościom języka C# i wydajności programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f230a-269">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span>  <span data-ttu-id="f230a-270">Ta wersja nowych i bardziej wydajnych zachowuje tych klas bez dodawania żadnych złożonego kodu do obsługi.</span><span class="sxs-lookup"><span data-stu-id="f230a-270">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>  
  
### <a name="async-method-caching"></a><span data-ttu-id="f230a-271">Buforowanie metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="f230a-271">Async method caching</span></span>  
 <span data-ttu-id="f230a-272">W kolejnym przykładzie pokazano to powszechny problem podczas próby użycia buforowane wyniki w [async](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) metody.</span><span class="sxs-lookup"><span data-stu-id="f230a-272">The next example shows a common problem when you try to use cached results in an [async](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) method.</span></span>  
  
 <span data-ttu-id="f230a-273">**Przykład 6: buforowanie w metodach asynchronicznych**</span><span class="sxs-lookup"><span data-stu-id="f230a-273">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="f230a-274">Funkcje programu Visual Studio IDE zbudowany na nowej Kompilatory języka C# i Visual Basic często pobrać drzewa składni i kompilatory umożliwia asynchroniczne czyniąc zachowanie reakcji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f230a-274">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span>  <span data-ttu-id="f230a-275">Poniżej przedstawiono pierwszą wersję kodu, który może zapisać można pobrać drzewa składni:</span><span class="sxs-lookup"><span data-stu-id="f230a-275">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="f230a-276">Widać, że wywołania `GetSyntaxTreeAsync()` tworzy `Parser`, analizuje kod, a następnie zwraca <xref:System.Threading.Tasks.Task> obiektu `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="f230a-276">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span>  <span data-ttu-id="f230a-277">Przydzielanie jest kosztowne części `Parser` wystąpienia i analizy kodu.</span><span class="sxs-lookup"><span data-stu-id="f230a-277">The expensive part is allocating the `Parser` instance and parsing the code.</span></span>  <span data-ttu-id="f230a-278">Funkcja zwraca <xref:System.Threading.Tasks.Task> tak, aby obiekty wywołujące można oczekiwać podczas analizowania pracy oraz o wolnym wątku interfejsu użytkownika można odbierać dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f230a-278">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>  
  
 <span data-ttu-id="f230a-279">Niektóre funkcje programu Visual Studio może podjąć próbę pobrania tym samym drzewie składni, więc mogą pisać następujący kod do pamięci podręcznej podczas analizowania wyników, aby zaoszczędzić czas i alokacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-279">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span>  <span data-ttu-id="f230a-280">Jednak ten kod wiąże się z alokacji:</span><span class="sxs-lookup"><span data-stu-id="f230a-280">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="f230a-281">Zobacz, czy nowy kod z buforowaniem ma `SyntaxTree` pola o nazwie `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="f230a-281">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span>  <span data-ttu-id="f230a-282">Gdy to pole ma wartość null, `GetSyntaxTreeAsync()` wykonuje pracę i zapisuje go w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f230a-282">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span>  <span data-ttu-id="f230a-283">`GetSyntaxTreeAsync()`Zwraca `SyntaxTree` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f230a-283">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span>  <span data-ttu-id="f230a-284">Problem występuje wtedy, gdy masz `async` — funkcja typu `Task<SyntaxTree>`, i zwracać wartość typu `SyntaxTree`, kompilator emituje kod, aby przydzielić zadania do przechowywania wynik (przy użyciu `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="f230a-284">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span>  <span data-ttu-id="f230a-285">Zadanie zostanie oznaczone jako wykonane, a wynik jest natychmiast dostępna.</span><span class="sxs-lookup"><span data-stu-id="f230a-285">The Task is marked as completed, and the result is immediately available.</span></span>  <span data-ttu-id="f230a-286">W kodzie dla nowego kompilatorów <xref:System.Threading.Tasks.Task> obiektów, które zostały już wykonane wystąpił, dlatego często oznacza ustalające tych przydziałów poprawia czas odpowiedzi znacznie.</span><span class="sxs-lookup"><span data-stu-id="f230a-286">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>  
  
 <span data-ttu-id="f230a-287">**Na przykład rozwiązać 6**</span><span class="sxs-lookup"><span data-stu-id="f230a-287">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="f230a-288">Aby usunąć ukończonej <xref:System.Threading.Tasks.Task> alokacji, może buforować obiekt zadania z wynikiem zakończone:</span><span class="sxs-lookup"><span data-stu-id="f230a-288">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="f230a-289">Ten kod zmienia typ `cachedResult` do `Task<SyntaxTree>` i wykorzystuje `async` funkcji Pomocnik, która przechowuje oryginalny kod z `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="f230a-289">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span>  <span data-ttu-id="f230a-290">`GetSyntaxTreeAsync()`używa teraz [null operatora łączącego](~/docs/csharp/language-reference/operators/null-conditional-operator.md) do zwrócenia `cachedResult` Jeśli nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="f230a-290">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](~/docs/csharp/language-reference/operators/null-conditional-operator.md) to return `cachedResult` if it isn't null.</span></span>  <span data-ttu-id="f230a-291">Jeśli `cachedResult` ma wartość null, następnie `GetSyntaxTreeAsync()` wywołania `GetSyntaxTreeUncachedAsync()` i buforuje wynik.</span><span class="sxs-lookup"><span data-stu-id="f230a-291">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span>  <span data-ttu-id="f230a-292">Zwróć uwagę, że `GetSyntaxTreeAsync()` nie await wywołanie `GetSyntaxTreeUncachedAsync()` jako kod normalnie.</span><span class="sxs-lookup"><span data-stu-id="f230a-292">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span>  <span data-ttu-id="f230a-293">Nie używa await oznacza że w przypadku `GetSyntaxTreeUncachedAsync()` zwraca jego <xref:System.Threading.Tasks.Task> obiektu `GetSyntaxTreeAsync()` natychmiast zwraca <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="f230a-293">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span>  <span data-ttu-id="f230a-294">Teraz jest buforowanego zestawu wyników <xref:System.Threading.Tasks.Task>, więc nie nie przydziału do zwrócenia wyniku pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f230a-294">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>  
  
### <a name="additional-considerations"></a><span data-ttu-id="f230a-295">Dodatkowe uwagi</span><span class="sxs-lookup"><span data-stu-id="f230a-295">Additional considerations</span></span>  
 <span data-ttu-id="f230a-296">Oto kilka punktów więcej o potencjalnych problemach w dużych aplikacji lub aplikacji, które przetwarzają dużą ilość danych.</span><span class="sxs-lookup"><span data-stu-id="f230a-296">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>  
  
 <span data-ttu-id="f230a-297">**Słowników**</span><span class="sxs-lookup"><span data-stu-id="f230a-297">**Dictionaries**</span></span>  
  
 <span data-ttu-id="f230a-298">Słowniki są używane ubiquitously w wielu programach i jednak słowniki są bardzo wygodny i z założenia wydajne.</span><span class="sxs-lookup"><span data-stu-id="f230a-298">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span>  <span data-ttu-id="f230a-299">Jednak są często używane niewłaściwie.</span><span class="sxs-lookup"><span data-stu-id="f230a-299">However, they’re often used inappropriately.</span></span>  <span data-ttu-id="f230a-300">W Visual Studio i nowych kompilatory analizy wskazuje, że wiele słowników zawiera pojedynczy element lub były puste.</span><span class="sxs-lookup"><span data-stu-id="f230a-300">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span>  <span data-ttu-id="f230a-301">Pusta <xref:System.Collections.Generic.Dictionary%602> ma dziesięć pól i zajmuje 48 bajtów w stercie na x86 maszyny.</span><span class="sxs-lookup"><span data-stu-id="f230a-301">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span>  <span data-ttu-id="f230a-302">Słowniki są doskonałe gdy będziesz potrzebować mapowania lub asocjacyjnych struktury danych z stała czas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f230a-302">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span>  <span data-ttu-id="f230a-303">Jednak jeśli masz tylko kilka elementów można odpady dużo miejsca za pomocą słownika.</span><span class="sxs-lookup"><span data-stu-id="f230a-303">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span>  <span data-ttu-id="f230a-304">Zamiast tego, na przykład można wielokrotnie powtarzane dostępne za pośrednictwem `List<KeyValuePair\<K,V>>`, jak szybki.</span><span class="sxs-lookup"><span data-stu-id="f230a-304">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span>  <span data-ttu-id="f230a-305">Jeśli używasz słownik tylko do ładowania danych i następnie odczytanie z niego (bardzo typowy wzorzec) przy użyciu tablicy posortowane w usłudze wyszukiwania N(log(N)) może być niemal jako szybkiego, w zależności od liczby elementów, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="f230a-305">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>  
  
 <span data-ttu-id="f230a-306">**Klasy i struktury**</span><span class="sxs-lookup"><span data-stu-id="f230a-306">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="f230a-307">Klasy i struktury w sposób, podaj zależnościami klasycznego miejsca i godziny dla Dostrajanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f230a-307">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span>  <span data-ttu-id="f230a-308">Klasy pociągnąć za sobą 12 bajtów obciążenie x86 komputera nawet wtedy, gdy mają one nie ma pól, ale są one niedrogich do przekazania wokół, ponieważ trwa tylko wskaźnik do odwoływania się do wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="f230a-308">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span>  <span data-ttu-id="f230a-309">Struktury pociągnąć za sobą nie Alokacje sterty, jeśli nie są one opakowany, ale podczas przekazywania dużych struktury jako argumenty funkcji lub wartości zwracane, czas procesora CPU automatycznie skopiować wszystkie elementy członkowskie danych struktury.</span><span class="sxs-lookup"><span data-stu-id="f230a-309">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span>  <span data-ttu-id="f230a-310">Zwróć uwagę na powtarzane wywołania do właściwości, które zwraca struktury i pamięci podręcznej wartość właściwości w zmiennej lokalnej, aby uniknąć nadmiernego dane kopiowanie.</span><span class="sxs-lookup"><span data-stu-id="f230a-310">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>  
  
 <span data-ttu-id="f230a-311">**Pamięci podręczne**</span><span class="sxs-lookup"><span data-stu-id="f230a-311">**Caches**</span></span>  
  
 <span data-ttu-id="f230a-312">Typowe lewy wydajności jest wyniki pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f230a-312">A common performance trick is to cache results.</span></span>  <span data-ttu-id="f230a-313">Jednak bez zakończenia lub usuwania zasad rozmiar pamięci podręcznej może być przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="f230a-313">However, a cache without a size cap or disposal policy can be a memory leak.</span></span>  <span data-ttu-id="f230a-314">Podczas przetwarzania dużych ilości danych, jeśli mają celu dużej ilości pamięci w pamięci podręcznej, może spowodować wyrzucanie elementów bezużytecznych do przesłonięcia korzyści z pamięci podręcznej wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f230a-314">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>  
  
 <span data-ttu-id="f230a-315">W tym artykule omówiono sposób należy zwrócić uwagę objawy wąskich gardeł wydajności, które mogą wpłynąć na czas odpowiedzi aplikacji, zwłaszcza w przypadku dużych systemów lub systemów, które przetwarzają dużą ilość danych.</span><span class="sxs-lookup"><span data-stu-id="f230a-315">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="f230a-316">Typowe sprawcami obejmują pakującej, działań na ciągach, LINQ i lambda, buforowanie w metodach asynchronicznych buforowanie bez rozmiar limit lub usuwania zasad, nieodpowiednie użycie słowniki i przekazywanie wokół struktury.</span><span class="sxs-lookup"><span data-stu-id="f230a-316">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span>  <span data-ttu-id="f230a-317">Należy pamiętać, cztery faktów dostrojenia aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f230a-317">Keep in mind the four facts for tuning your apps:</span></span>  
  
-   <span data-ttu-id="f230a-318">Nie przedwcześnie Optymalizacja — produktywności i dostrajania aplikacji, gdy dodatkowe problemy.</span><span class="sxs-lookup"><span data-stu-id="f230a-318">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>  
  
-   <span data-ttu-id="f230a-319">Profile nie znajdują się — w przypadku odgadnięcie, jeśli użytkownik nie notuje.</span><span class="sxs-lookup"><span data-stu-id="f230a-319">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>  
  
-   <span data-ttu-id="f230a-320">Dobrym narzędzi zależy od — Pobierz narzędzia PerfView i wypróbować jej możliwości.</span><span class="sxs-lookup"><span data-stu-id="f230a-320">Good tools make all the difference – download PerfView and try it out.</span></span>  
  
-   <span data-ttu-id="f230a-321">Jest wszystkie o alokacji — czyli gdzie zespołu platformy kompilatora poświęconego większość czasu zwiększanie wydajności kompilatory nowe.</span><span class="sxs-lookup"><span data-stu-id="f230a-321">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f230a-322">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f230a-322">See Also</span></span>  
 [<span data-ttu-id="f230a-323">Wideo prezentacji w tym temacie</span><span class="sxs-lookup"><span data-stu-id="f230a-323">Video of presentation of this topic</span></span>](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
 [<span data-ttu-id="f230a-324">Profilowanie wydajności — przewodnik dla początkujących</span><span class="sxs-lookup"><span data-stu-id="f230a-324">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
 [<span data-ttu-id="f230a-325">Wydajność</span><span class="sxs-lookup"><span data-stu-id="f230a-325">Performance</span></span>](../../../docs/framework/performance/index.md)  
 [<span data-ttu-id="f230a-326">Porady dotyczące wydajności .NET</span><span class="sxs-lookup"><span data-stu-id="f230a-326">.NET Performance Tips</span></span>](http://msdn.microsoft.com/library/ms973839.aspx)  
 [<span data-ttu-id="f230a-327">Narzędzie do analizy wydajności Windows Phone</span><span class="sxs-lookup"><span data-stu-id="f230a-327">Windows Phone Performance Analysis Tool</span></span>](http://msdn.microsoft.com/magazine/hh781024.aspx)  
 [<span data-ttu-id="f230a-328">Znajdź wąskich gardeł aplikacji z profilera Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f230a-328">Find Application Bottlenecks with Visual Studio Profiler</span></span>](http://msdn.microsoft.com/magazine/cc337887.aspx)  
 [<span data-ttu-id="f230a-329">Kanał 9 samouczki narzędzia PerfView</span><span class="sxs-lookup"><span data-stu-id="f230a-329">Channel 9 PerfView tutorials</span></span>](http://channel9.msdn.com/Series/PerfView-Tutorial)  
 [<span data-ttu-id="f230a-330">Porady dotyczące wydajności wysokiego poziomu</span><span class="sxs-lookup"><span data-stu-id="f230a-330">High-level Performance Tips</span></span>](http://curah.microsoft.com/4604/improving-your-net-apps-startup-performance)  
 [<span data-ttu-id="f230a-331">repozytorium DotNet/roslyn w witrynie GitHub</span><span class="sxs-lookup"><span data-stu-id="f230a-331">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
