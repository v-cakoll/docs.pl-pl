---
title: Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 57f65feff5260cb83df5354f5d7ee1bad0babb3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180579"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="b262e-102">Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b262e-102">Writing Large, Responsive .NET Framework Apps</span></span>

<span data-ttu-id="b262e-103">Ten artykuł zawiera wskazówki dotyczące poprawy wydajności dużych aplikacji programu .NET Framework lub aplikacji przetwarzanych przez dużą ilość danych, takich jak pliki lub bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b262e-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="b262e-104">Te wskazówki pochodzą z przepisywania kompilatorów języka C# i Visual Basic w kodzie zarządzanym, a ten artykuł zawiera kilka rzeczywistych przykładów z kompilatora języka C#.</span><span class="sxs-lookup"><span data-stu-id="b262e-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>
  
<span data-ttu-id="b262e-105">.NET Framework jest wysoce wydajne do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="b262e-106">Potężne i bezpieczne języki i bogata kolekcja bibliotek sprawiają, że tworzenie aplikacji jest bardzo owocne.</span><span class="sxs-lookup"><span data-stu-id="b262e-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="b262e-107">Jednak z dużą wydajnością przychodzi odpowiedzialność.</span><span class="sxs-lookup"><span data-stu-id="b262e-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="b262e-108">Należy użyć wszystkich uprawnień .NET Framework, ale należy przygotować się do dostrojenia wydajności kodu w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="b262e-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="b262e-109">Dlaczego nowa wydajność kompilatora ma zastosowanie do aplikacji</span><span class="sxs-lookup"><span data-stu-id="b262e-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="b262e-110">Zespół platformy kompilatora platformy .NET ("Roslyn") przepisał kompilatory języka C# i Visual Basic w kodzie zarządzanym, aby zapewnić nowe interfejsy API do modelowania i analizowania kodu, narzędzi do tworzenia i włączania znacznie bogatszych, świadomych kodu środowisk w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b262e-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="b262e-111">Przepisywanie kompilatorów i tworzenie środowiska programu Visual Studio na nowych kompilatorach ujawniło przydatne szczegółowe informacje o wydajności, które mają zastosowanie do dowolnej dużej aplikacji .NET Framework lub dowolnej aplikacji, która przetwarza dużo danych.</span><span class="sxs-lookup"><span data-stu-id="b262e-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="b262e-112">Nie musisz wiedzieć o kompilatorów, aby skorzystać z szczegółowych informacji i przykładów z kompilatora języka C#.</span><span class="sxs-lookup"><span data-stu-id="b262e-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>
  
 <span data-ttu-id="b262e-113">Visual Studio używa interfejsów API kompilatora do tworzenia wszystkich funkcji IntelliSense, które użytkownicy kochają, takich jak kolorowanie identyfikatorów i słów kluczowych, listy uzupełnień składni, squiggles dla błędów, porady parametrów, problemy z kodem i akcje kodu.</span><span class="sxs-lookup"><span data-stu-id="b262e-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="b262e-114">Visual Studio zapewnia tę pomoc, podczas gdy deweloperzy wpisują i zmieniają swój kod, a program Visual Studio musi pozostać responsywny, podczas gdy kompilator stale modeluje edycję kodu przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="b262e-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>
  
 <span data-ttu-id="b262e-115">Gdy użytkownicy końcowi wchodzą w interakcję z aplikacją, oczekują, że będzie responsywna.</span><span class="sxs-lookup"><span data-stu-id="b262e-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="b262e-116">Pisanie lub obsługa poleceń nigdy nie powinny być blokowane.</span><span class="sxs-lookup"><span data-stu-id="b262e-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="b262e-117">Pomoc powinna szybko wyskoczyć lub zrezygnować, jeśli użytkownik kontynuuje wpisywanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="b262e-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="b262e-118">Aplikacja powinna unikać blokowania wątku interfejsu użytkownika z długimi obliczeniami, które sprawiają, że aplikacja czuje się powolna.</span><span class="sxs-lookup"><span data-stu-id="b262e-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>
  
 <span data-ttu-id="b262e-119">Aby uzyskać więcej informacji na temat kompilatorów Roslyn, zobacz [zestaw SDK platformy kompilatora .NET](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="b262e-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="b262e-120">Tylko fakty</span><span class="sxs-lookup"><span data-stu-id="b262e-120">Just the Facts</span></span>  
 <span data-ttu-id="b262e-121">Należy wziąć pod uwagę te fakty podczas dostrajania wydajności i tworzenia elastycznych aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b262e-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="b262e-122">Fakt 1: Nie przedwcześnie optymalizuj</span><span class="sxs-lookup"><span data-stu-id="b262e-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="b262e-123">Pisanie kodu, który jest bardziej złożony niż musi być poniesie koszty konserwacji, debugowania i polerowania.</span><span class="sxs-lookup"><span data-stu-id="b262e-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="b262e-124">Doświadczeni programiści mają intuicyjne zrozumienie, jak rozwiązywać problemy z kodowaniem i pisać bardziej wydajny kod.</span><span class="sxs-lookup"><span data-stu-id="b262e-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="b262e-125">Jednak czasami przedwcześnie optymalizują swój kod.</span><span class="sxs-lookup"><span data-stu-id="b262e-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="b262e-126">Na przykład używają tabeli mieszania, gdy wystarczy prosta tablica, lub używają skomplikowanego buforowania, które może przeciekać pamięci zamiast po prostu ponownie obliczać wartości.</span><span class="sxs-lookup"><span data-stu-id="b262e-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="b262e-127">Nawet jeśli jesteś programistą środowiska, należy przetestować pod kątem wydajności i analizować kod, gdy znajdziesz problemy.</span><span class="sxs-lookup"><span data-stu-id="b262e-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="b262e-128">Fakt 2: Jeśli nie mierzysz, zgadujesz</span><span class="sxs-lookup"><span data-stu-id="b262e-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="b262e-129">Profile i pomiary nie kłamią.</span><span class="sxs-lookup"><span data-stu-id="b262e-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="b262e-130">Profile pokazują, czy procesor jest w pełni załadowany, czy też jesteś zablokowany na we/wy dysku.</span><span class="sxs-lookup"><span data-stu-id="b262e-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="b262e-131">Profile informują, jakiego rodzaju i ile pamięci przydzielasz i czy procesor cpu spędza dużo czasu w [wyrzucaniu elementów bezużytecznych](../../standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="b262e-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span>
  
 <span data-ttu-id="b262e-132">Należy ustawić cele wydajności dla kluczowych środowisk klienta lub scenariuszy w aplikacji i napisać testy do pomiaru wydajności.</span><span class="sxs-lookup"><span data-stu-id="b262e-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="b262e-133">Zbadaj nieudane testy, stosując metodę naukową: użyj profili, aby cię poprowadzić, hipotezę, co może być problemem, i przetestuj swoją hipotezę za pomocą eksperymentu lub zmiany kodu.</span><span class="sxs-lookup"><span data-stu-id="b262e-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="b262e-134">Ustal podstawowe pomiary wydajności w czasie za pomocą regularnych testów, dzięki czemu można wyizolować zmiany, które powodują regresji w wydajności.</span><span class="sxs-lookup"><span data-stu-id="b262e-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="b262e-135">Zbliżając się do pracy wydajności w sposób rygorystyczny, można uniknąć marnowania czasu z aktualizacji kodu, które nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b262e-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="b262e-136">Fakt 3: Dobre narzędzia robią różnicę</span><span class="sxs-lookup"><span data-stu-id="b262e-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="b262e-137">Dobre narzędzia pozwalają szybko drążyć największe problemy z wydajnością (procesora, pamięci lub dysku) i pomóc zlokalizować kod, który powoduje te wąskie gardła.</span><span class="sxs-lookup"><span data-stu-id="b262e-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="b262e-138">Firma Microsoft dostarcza wiele narzędzi wydajności, takich jak [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) i [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="b262e-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span>
  
 <span data-ttu-id="b262e-139">PerfView to bezpłatne i niezwykle potężne narzędzie, które pomaga skupić się na głębokich problemach, takich jak we/wy dysku, zdarzenia GC i pamięć.</span><span class="sxs-lookup"><span data-stu-id="b262e-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="b262e-140">Śledzenie zdarzeń związanych z wydajnością [dla systemu Windows](../wcf/samples/etw-tracing.md) (ETW) można łatwo przeglądać na aplikację, na proces, na stos i informacje na wątek.</span><span class="sxs-lookup"><span data-stu-id="b262e-140">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="b262e-141">PerfView pokazuje, ile i jakiego rodzaju pamięci przydziela aplikacja i które funkcje lub stosy wywołań przyczyniają się ile do alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="b262e-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="b262e-142">Aby uzyskać szczegółowe informacje, zobacz zaawansowane tematy pomocy, wersje demonstracyjne i klipy wideo dołączone do narzędzia (takie jak [samouczki PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) w kanale 9).</span><span class="sxs-lookup"><span data-stu-id="b262e-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="b262e-143">Fakt 4: Chodzi o przydziały</span><span class="sxs-lookup"><span data-stu-id="b262e-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="b262e-144">Można pomyśleć, że tworzenie elastycznej aplikacji .NET Framework jest o algorytmy, takie jak przy użyciu szybkiego sortowania zamiast sortowania bąbelków, ale to nie jest przypadek.</span><span class="sxs-lookup"><span data-stu-id="b262e-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="b262e-145">Największym czynnikiem w tworzeniu aplikacji responsywnej jest przydzielanie pamięci, zwłaszcza gdy aplikacja jest bardzo duża lub przetwarza duże ilości danych.</span><span class="sxs-lookup"><span data-stu-id="b262e-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>
  
 <span data-ttu-id="b262e-146">Prawie cała praca nad tworzeniem elastycznych środowisk IDE za pomocą nowych interfejsów API kompilatora obejmowała unikanie alokacji i zarządzanie strategiami buforowania.</span><span class="sxs-lookup"><span data-stu-id="b262e-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="b262e-147">Ślady PerfView pokazują, że wydajność nowych kompilatorów Języka C# i Visual Basic rzadko jest powiązana z procesorem CPU.</span><span class="sxs-lookup"><span data-stu-id="b262e-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="b262e-148">Kompilatory mogą być powiązane we/wy podczas odczytywania setek tysięcy lub milionów wierszy kodu, odczytywania metadanych lub emitowania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="b262e-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="b262e-149">Opóźnienia wątku interfejsu użytkownika są prawie wszystkie z powodu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b262e-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="b262e-150">.NET Framework GC jest wysoce dostrojony pod kątem wydajności i wykonuje wiele swojej pracy jednocześnie podczas wykonywania kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="b262e-151">Jednak pojedyncza alokacja może wyzwolić kosztowną [kolekcję gen2,](../../standard/garbage-collection/fundamentals.md) zatrzymując wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="b262e-151">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="b262e-152">Wspólne alokacje i przykłady</span><span class="sxs-lookup"><span data-stu-id="b262e-152">Common allocations and examples</span></span>  
 <span data-ttu-id="b262e-153">Przykładowe wyrażenia w tej sekcji mają ukryte alokacje, które wydają się małe.</span><span class="sxs-lookup"><span data-stu-id="b262e-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="b262e-154">Jednak jeśli duża aplikacja wykonuje wyrażenia tyle razy, mogą one powoduje setki megabajtów, nawet gigabajtów alokacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="b262e-155">Na przykład jednominutowe testy, które symulowały wpisywanie przez dewelopera w edytorze, przydzielały gigabajty pamięci i powodowały, że zespół wydajności skupił się na scenariuszach pisania.</span><span class="sxs-lookup"><span data-stu-id="b262e-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>
  
### <a name="boxing"></a><span data-ttu-id="b262e-156">Boxing</span><span class="sxs-lookup"><span data-stu-id="b262e-156">Boxing</span></span>  
 <span data-ttu-id="b262e-157">[Boks](../../csharp/programming-guide/types/boxing-and-unboxing.md) występuje, gdy typy wartości, które zwykle działają na stosie lub w strukturach danych są zawijane w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="b262e-157">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="b262e-158">Oznacza to, że można przydzielić obiekt do przechowywania danych, a następnie zwrócić wskaźnik do obiektu.</span><span class="sxs-lookup"><span data-stu-id="b262e-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="b262e-159">.NET Framework czasami pola wartości ze względu na podpis metody lub typu lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="b262e-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="b262e-160">Zawijanie typu wartości w obiekcie powoduje alokację pamięci.</span><span class="sxs-lookup"><span data-stu-id="b262e-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="b262e-161">Wiele operacji bokserskich może przyczynić się do megabajtów lub gigabajtów alokacji do aplikacji, co oznacza, że aplikacja spowoduje więcej kontrolerów domeny.</span><span class="sxs-lookup"><span data-stu-id="b262e-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="b262e-162">.NET Framework i kompilatory języka uniknąć boksu, gdy jest to możliwe, ale czasami dzieje się, gdy najmniej się tego spodziewać.</span><span class="sxs-lookup"><span data-stu-id="b262e-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>
  
 <span data-ttu-id="b262e-163">Aby zobaczyć boks w PerfView, otwórz śledzenie i spójrz na stosy alloc sterty GC pod nazwą procesu aplikacji (pamiętaj, PerfView raportuje wszystkie procesy).</span><span class="sxs-lookup"><span data-stu-id="b262e-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="b262e-164">Jeśli widzisz typy, takie jak <xref:System.Int32?displayProperty=nameWithType> i <xref:System.Char?displayProperty=nameWithType> w ramach alokacji, są typy wartości boksu.</span><span class="sxs-lookup"><span data-stu-id="b262e-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="b262e-165">Wybranie jednego z tych typów pokaże stosy i funkcje, w których są one zapakowane.</span><span class="sxs-lookup"><span data-stu-id="b262e-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>
  
 <span data-ttu-id="b262e-166">**Przykład 1: metody ciągu i argumenty typu wartości**</span><span class="sxs-lookup"><span data-stu-id="b262e-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="b262e-167">Ten przykładowy kod ilustruje potencjalnie niepotrzebne i nadmierne boks:</span><span class="sxs-lookup"><span data-stu-id="b262e-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="b262e-168">Ten kod zapewnia funkcje rejestrowania, więc `Log` aplikacja może często wywoływać funkcję, może miliony razy.</span><span class="sxs-lookup"><span data-stu-id="b262e-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="b262e-169">Problem polega na tym, że wywołanie `string.Format` rozwiązuje <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="b262e-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>
  
 <span data-ttu-id="b262e-170">To przeciążenie wymaga .NET `int` Framework do pola wartości do obiektów, aby przekazać je do tej metody wywołania.</span><span class="sxs-lookup"><span data-stu-id="b262e-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="b262e-171">Częściowa poprawka jest `id.ToString()` `size.ToString()` wywołanie i przekazać wszystkie ciągi `string.Format` (które są obiektami) do wywołania.</span><span class="sxs-lookup"><span data-stu-id="b262e-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="b262e-172">Wywołanie `ToString()` przydziela ciąg, ale ta alokacja i tak nastąpi w środku `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="b262e-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>
  
 <span data-ttu-id="b262e-173">Można uznać, że to `string.Format` podstawowe wywołanie jest tylko łączenie ciągów, więc można napisać ten kod zamiast:</span><span class="sxs-lookup"><span data-stu-id="b262e-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="b262e-174">Jednak ten wiersz kodu wprowadza alokacji boksu, ponieważ kompiluje do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="b262e-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="b262e-175">Program .NET Framework musi zawierać literał znaku, aby wywołać`Concat`</span><span class="sxs-lookup"><span data-stu-id="b262e-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="b262e-176">**Poprawka na przykład 1**</span><span class="sxs-lookup"><span data-stu-id="b262e-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="b262e-177">Kompletna poprawka jest prosta.</span><span class="sxs-lookup"><span data-stu-id="b262e-177">The complete fix is simple.</span></span> <span data-ttu-id="b262e-178">Wystarczy zastąpić literał znaku literałem, który nie ponosi żadnego boksu, ponieważ ciągi są już obiektami:</span><span class="sxs-lookup"><span data-stu-id="b262e-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="b262e-179">**Przykład 2: boks wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="b262e-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="b262e-180">W tym przykładzie był odpowiedzialny za ogromną ilość alokacji w nowych kompilatorów Języka C# i Visual Basic ze względu na częste używanie typów wyliczenia, szczególnie w operacjach wyszukiwania słownika.</span><span class="sxs-lookup"><span data-stu-id="b262e-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>
  
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
  
 <span data-ttu-id="b262e-181">Ten problem jest bardzo subtelny.</span><span class="sxs-lookup"><span data-stu-id="b262e-181">This problem is very subtle.</span></span> <span data-ttu-id="b262e-182">PerfView będzie raport <xref:System.Enum.GetHashCode> to jako boks, ponieważ pola metody podstawowej reprezentacji typu wyliczenia, ze względu na implementację.</span><span class="sxs-lookup"><span data-stu-id="b262e-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="b262e-183">Jeśli przyjrzysz się uważnie w PerfView, możesz zobaczyć <xref:System.Enum.GetHashCode>dwie alokacje boksu dla każdego wywołania .</span><span class="sxs-lookup"><span data-stu-id="b262e-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="b262e-184">Kompilator wstawia jeden, a program .NET Framework wstawia drugą.</span><span class="sxs-lookup"><span data-stu-id="b262e-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span>
  
 <span data-ttu-id="b262e-185">**Poprawka na przykład 2**</span><span class="sxs-lookup"><span data-stu-id="b262e-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="b262e-186">Można łatwo uniknąć obu alokacji, rzucając <xref:System.Enum.GetHashCode>do podstawowej reprezentacji przed wywołaniem:</span><span class="sxs-lookup"><span data-stu-id="b262e-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="b262e-187">Innym typowym źródłem boksu na <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> typy wyliczenia jest metoda.</span><span class="sxs-lookup"><span data-stu-id="b262e-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b262e-188">Argument przekazany <xref:System.Enum.HasFlag%28System.Enum%29> do musi być zapakowany.</span><span class="sxs-lookup"><span data-stu-id="b262e-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="b262e-189">W większości przypadków zastępowanie wywołań <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> testem bitowym jest prostsze i wolne od alokacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>
  
 <span data-ttu-id="b262e-190">Pamiętaj o pierwszym fakcie wydajności (czyli nie przedwcześnie optymalizuj) i nie uruchamiaj przepisywania całego kodu w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="b262e-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="b262e-191">Należy pamiętać o tych kosztów boksu, ale zmienić kod tylko po profilowaniu aplikacji i znalezienie hot spotów.</span><span class="sxs-lookup"><span data-stu-id="b262e-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>
  
### <a name="strings"></a><span data-ttu-id="b262e-192">Ciągi</span><span class="sxs-lookup"><span data-stu-id="b262e-192">Strings</span></span>  
 <span data-ttu-id="b262e-193">Manipulacje ciągami są jednymi z największych winowajców alokacji i często pojawiają się w PerfView w pierwszej piątce alokacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="b262e-194">Programy używają ciągów do serializacji, JSON i REST INTERFEJSÓW API.</span><span class="sxs-lookup"><span data-stu-id="b262e-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="b262e-195">Ciągów można używać jako stałych programowych do współpracy z systemami, gdy nie można używać typów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b262e-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="b262e-196">Gdy profilowanie pokazuje, że ciągi mają duży <xref:System.String> wpływ na <xref:System.String.Format%2A> <xref:System.String.Concat%2A>wydajność, poszukaj wywołań metod, takich jak , <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b262e-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="b262e-197">Aby <xref:System.Text.StringBuilder> uniknąć kosztów tworzenia jednego ciągu z wielu elementów pomaga, <xref:System.Text.StringBuilder> ale nawet przydzielanie obiektu może stać się wąskim gardłem, które należy zarządzać.</span><span class="sxs-lookup"><span data-stu-id="b262e-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>
  
 <span data-ttu-id="b262e-198">**Przykład 3: operacje ciągu**</span><span class="sxs-lookup"><span data-stu-id="b262e-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="b262e-199">Kompilator języka C# miał ten kod, który zapisuje tekst sformatowanego komentarza doc XML:</span><span class="sxs-lookup"><span data-stu-id="b262e-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="b262e-200">Widać, że ten kod wykonuje wiele manipulacji ciągami.</span><span class="sxs-lookup"><span data-stu-id="b262e-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="b262e-201">Kod używa metod biblioteki do dzielenia wierszy na oddzielne ciągi, `text` do przycinania białych znaków, sprawdzania, czy argument jest komentarzem dokumentacji XML i wyodrębniania podciągów z wierszy.</span><span class="sxs-lookup"><span data-stu-id="b262e-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>
  
 <span data-ttu-id="b262e-202">W pierwszym wierszu `WriteFormattedDocComment` `text.Split` wewnątrz wywołania przydziela nową tablicę trzyelementową jako argument za każdym razem, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b262e-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="b262e-203">Kompilator musi emitować kod, aby przydzielić tę tablicę za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="b262e-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="b262e-204">To dlatego, że kompilator nie <xref:System.String.Split%2A> wie, czy przechowuje tablicę gdzieś, gdzie tablica może `WriteFormattedDocComment`być modyfikowana przez inny kod, co miałoby wpływ na późniejsze wywołania .</span><span class="sxs-lookup"><span data-stu-id="b262e-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="b262e-205">Wywołanie <xref:System.String.Split%2A> również przydziela ciąg dla każdego `text` wiersza i przydziela inną pamięć do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>
  
 <span data-ttu-id="b262e-206">`WriteFormattedDocComment`ma trzy wywołania do <xref:System.String.TrimStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b262e-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="b262e-207">Dwa znajdują się w wewnętrznych pętlach, które powielają pracę i alokacje.</span><span class="sxs-lookup"><span data-stu-id="b262e-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="b262e-208">Co gorsza, wywołanie <xref:System.String.TrimStart%2A> metody bez argumentów przydziela pustą `params` tablicę (dla parametru) oprócz wyniku ciągu.</span><span class="sxs-lookup"><span data-stu-id="b262e-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>
  
 <span data-ttu-id="b262e-209">Wreszcie istnieje wywołanie <xref:System.String.Substring%2A> metody, która zwykle przydziela nowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="b262e-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>
  
 <span data-ttu-id="b262e-210">**Poprawka na przykład 3**</span><span class="sxs-lookup"><span data-stu-id="b262e-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="b262e-211">W przeciwieństwie do wcześniejszych przykładów, małe zmiany nie można naprawić tych alokacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="b262e-212">Musisz cofnąć się, spojrzeć na problem i podejść do niego inaczej.</span><span class="sxs-lookup"><span data-stu-id="b262e-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="b262e-213">Na przykład można zauważyć, że `WriteFormattedDocComment()` argument jest ciągiem, który ma wszystkie informacje, które metoda potrzebuje, więc kod może zrobić więcej indeksowania zamiast przydzielania wielu ciągów częściowych.</span><span class="sxs-lookup"><span data-stu-id="b262e-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>
  
 <span data-ttu-id="b262e-214">Zespół wydajności kompilatora rozwiązał wszystkie te alokacje za pomocą kodu w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="b262e-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="b262e-215">Pierwsza wersja `WriteFormattedDocComment()` przydzielonej tablicy, kilka podciągów i przycięty podciąg wraz z pustą `params` tablicą.</span><span class="sxs-lookup"><span data-stu-id="b262e-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="b262e-216">To również zaznaczone dla "///".</span><span class="sxs-lookup"><span data-stu-id="b262e-216">It also checked for "///".</span></span> <span data-ttu-id="b262e-217">Poprawiony kod używa tylko indeksowania i nic nie przydziela.</span><span class="sxs-lookup"><span data-stu-id="b262e-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="b262e-218">Znajduje pierwszy znak, który nie jest biały znak, a następnie sprawdza znak według znaku, aby sprawdzić, czy ciąg zaczyna się od "///".</span><span class="sxs-lookup"><span data-stu-id="b262e-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="b262e-219">Nowy kod używa `IndexOfFirstNonWhiteSpaceChar` zamiast <xref:System.String.TrimStart%2A> zwracać pierwszy indeks (po indeksie początkowym określony), gdzie występuje znak niebiałki.</span><span class="sxs-lookup"><span data-stu-id="b262e-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="b262e-220">Poprawka nie jest kompletna, ale możesz zobaczyć, jak zastosować podobne poprawki dla kompletnego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b262e-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="b262e-221">Stosując to podejście w całym kodzie, można usunąć `WriteFormattedDocComment()`wszystkie alokacje w .</span><span class="sxs-lookup"><span data-stu-id="b262e-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>
  
 <span data-ttu-id="b262e-222">**Przykład 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="b262e-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="b262e-223">W tym przykładzie użyto <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b262e-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="b262e-224">Następująca funkcja generuje pełną nazwę typu dla typów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="b262e-224">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="b262e-225">Fokus jest na wierszu, który tworzy nowe <xref:System.Text.StringBuilder> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b262e-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="b262e-226">Kod powoduje alokacji `sb.ToString()` i alokacji <xref:System.Text.StringBuilder> wewnętrznej w ramach implementacji, ale nie można kontrolować te alokacje, jeśli chcesz wynik ciągu.</span><span class="sxs-lookup"><span data-stu-id="b262e-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>
  
 <span data-ttu-id="b262e-227">**Poprawka na przykład 4**</span><span class="sxs-lookup"><span data-stu-id="b262e-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="b262e-228">Aby naprawić `StringBuilder` alokację obiektu, buforuj obiekt.</span><span class="sxs-lookup"><span data-stu-id="b262e-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="b262e-229">Nawet buforowanie pojedynczego wystąpienia, które może zostać odrzucone, może znacznie poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="b262e-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="b262e-230">Jest to nowa implementacja funkcji, pomijając cały kod z wyjątkiem nowego pierwszego i ostatniego wiersza:</span><span class="sxs-lookup"><span data-stu-id="b262e-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="b262e-231">Kluczowymi częściami `AcquireBuilder()` są `GetStringAndReleaseBuilder()` nowe i funkcje:</span><span class="sxs-lookup"><span data-stu-id="b262e-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="b262e-232">Ponieważ nowe kompilatory używają wątków, te implementacje<xref:System.ThreadStaticAttribute> używają pola statycznego <xref:System.Text.StringBuilder>wątku (atrybut) `ThreadStatic` do buforowania , i prawdopodobnie można zrezygnować z deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b262e-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="b262e-233">Pole statyczne wątku posiada unikatową wartość dla każdego wątku, który wykonuje ten kod.</span><span class="sxs-lookup"><span data-stu-id="b262e-233">The thread-static field holds a unique value for each thread that executes this code.</span></span>
  
 <span data-ttu-id="b262e-234">`AcquireBuilder()`zwraca buforowane <xref:System.Text.StringBuilder> wystąpienie, jeśli istnieje, po wyczyszczeniu go i ustawieniu pola lub pamięci podręcznej na wartość null.</span><span class="sxs-lookup"><span data-stu-id="b262e-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="b262e-235">W `AcquireBuilder()` przeciwnym razie utworzy nowe wystąpienie i zwróci je, pozostawiając pole lub pamięć podręczną ustawioną na wartość null.</span><span class="sxs-lookup"><span data-stu-id="b262e-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>
  
 <span data-ttu-id="b262e-236">Po zakończeniu z <xref:System.Text.StringBuilder> , wywołać, `GetStringAndReleaseBuilder()` aby uzyskać wynik <xref:System.Text.StringBuilder> ciągu, zapisać wystąpienie w polu lub pamięci podręcznej, a następnie zwrócić wynik.</span><span class="sxs-lookup"><span data-stu-id="b262e-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="b262e-237">Jest możliwe wykonanie, aby ponownie wprowadzić ten <xref:System.Text.StringBuilder> kod i utworzyć wiele obiektów (chociaż rzadko się zdarza).</span><span class="sxs-lookup"><span data-stu-id="b262e-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="b262e-238">Kod zapisuje tylko ostatnie <xref:System.Text.StringBuilder> zwolnione wystąpienie do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="b262e-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="b262e-239">Ta prosta strategia buforowania znacznie zmniejszyła alokacje w nowych kompilatorach.</span><span class="sxs-lookup"><span data-stu-id="b262e-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="b262e-240">Części programu .NET Framework i MSBuild ("MSBuild") używają podobnej techniki w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="b262e-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>
  
 <span data-ttu-id="b262e-241">Ta prosta strategia buforowania jest zgodna z dobrym projektem pamięci podręcznej, ponieważ ma limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="b262e-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="b262e-242">Jednak teraz jest więcej kodu niż w oryginale, co oznacza więcej kosztów konserwacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="b262e-243">Strategię buforowania należy przyjąć tylko wtedy, gdy stwierdzono problem z wydajnością, <xref:System.Text.StringBuilder> a perfView pokazał, że alokacje są znaczącym czynnikiem przyczyniającym się.</span><span class="sxs-lookup"><span data-stu-id="b262e-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="b262e-244">LINQ i lambdas</span><span class="sxs-lookup"><span data-stu-id="b262e-244">LINQ and lambdas</span></span>  
<span data-ttu-id="b262e-245">Zapytanie zintegrowane z językiem (LINQ), w połączeniu z wyrażeniami lambda, jest przykładem funkcji produktywności.</span><span class="sxs-lookup"><span data-stu-id="b262e-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="b262e-246">Jednak jego użycie może mieć znaczący wpływ na wydajność w czasie i może się okazać, że trzeba przepisać kod.</span><span class="sxs-lookup"><span data-stu-id="b262e-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="b262e-247">**Przykład 5: Lambdas, Lista\<T> i IEnumerable\<T>**</span><span class="sxs-lookup"><span data-stu-id="b262e-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="b262e-248">W tym przykładzie użyto [LINQ i kod stylu funkcjonalnego,](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) aby znaleźć symbol w modelu kompilatora, biorąc pod uwagę ciąg nazwy:</span><span class="sxs-lookup"><span data-stu-id="b262e-248">This example uses [LINQ and functional style code](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="b262e-249">Nowy kompilator i środowiska IDE `FindMatchingSymbol()` zbudowany na nim wywołać bardzo często i istnieje kilka ukrytych alokacji w jednej linii tej funkcji kodu.</span><span class="sxs-lookup"><span data-stu-id="b262e-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="b262e-250">Aby zbadać te alokacje, najpierw podziel pojedynczy wiersz kodu funkcji na dwa wiersze:</span><span class="sxs-lookup"><span data-stu-id="b262e-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="b262e-251">W pierwszym wierszu `s => s.Name == name` [wyrażenie lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) zamyka się `name` [nad](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) zmienną lokalną .</span><span class="sxs-lookup"><span data-stu-id="b262e-251">In the first line, the [lambda expression](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) the local variable `name`.</span></span> <span data-ttu-id="b262e-252">Oznacza to, że oprócz przydzielania obiektu dla [delegata,](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) który `predicate` posiada, kod przydziela klasę statyczną do `name`przechowywania środowiska, które przechwytuje wartość .</span><span class="sxs-lookup"><span data-stu-id="b262e-252">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="b262e-253">Kompilator generuje kod, podobnie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="b262e-253">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="b262e-254">Dwie `new` alokacje (jeden dla klasy środowiska i jeden dla delegata) są teraz jawne.</span><span class="sxs-lookup"><span data-stu-id="b262e-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>
  
 <span data-ttu-id="b262e-255">Teraz spójrz na `FirstOrDefault`wezwanie do .</span><span class="sxs-lookup"><span data-stu-id="b262e-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="b262e-256">Ta metoda rozszerzenia <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> na typ wiąże się z alokacji zbyt.</span><span class="sxs-lookup"><span data-stu-id="b262e-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="b262e-257">Ponieważ `FirstOrDefault` przyjmuje <xref:System.Collections.Generic.IEnumerable%601> obiekt jako swój pierwszy argument, można rozwinąć wywołanie do następującego kodu (uproszczony bit do dyskusji):</span><span class="sxs-lookup"><span data-stu-id="b262e-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="b262e-258">Zmienna `symbols` ma <xref:System.Collections.Generic.List%601>typ .</span><span class="sxs-lookup"><span data-stu-id="b262e-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="b262e-259">Typ <xref:System.Collections.Generic.List%601> kolekcji <xref:System.Collections.Generic.IEnumerable%601> implementuje i sprytnie definiuje moduł<xref:System.Collections.Generic.IEnumerator%601> wyliczacza (interfejs), który <xref:System.Collections.Generic.List%601> implementuje z . `struct`</span><span class="sxs-lookup"><span data-stu-id="b262e-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="b262e-260">Przy użyciu struktury zamiast klasy oznacza, że zwykle uniknąć alokacji sterty, co z kolei może mieć wpływ na wydajność wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b262e-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="b262e-261">Wyliczacze są zazwyczaj używane z `foreach` pętli języka, który używa struktury wyliczacza, ponieważ jest zwracany na stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="b262e-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="b262e-262">Zwiększanie wskaźnik stosu wywołań, aby zrobić miejsce dla obiektu nie wpływa na GC sposób alokacji sterty nie.</span><span class="sxs-lookup"><span data-stu-id="b262e-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>
  
 <span data-ttu-id="b262e-263">W przypadku rozszerzonego `FirstOrDefault` połączenia kod musi `GetEnumerator()` wywołać <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b262e-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b262e-264">Przypisanie `symbols` do `enumerable` zmiennej `IEnumerable<Symbol>` typu traci informacje, że <xref:System.Collections.Generic.List%601>rzeczywisty obiekt jest .</span><span class="sxs-lookup"><span data-stu-id="b262e-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="b262e-265">Oznacza to, że gdy kod pobiera wyliczacz z `enumerable.GetEnumerator()`, .NET Framework musi pole `enumerator` zwróconej struktury, aby przypisać go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b262e-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>
  
 <span data-ttu-id="b262e-266">**Poprawka na przykład 5**</span><span class="sxs-lookup"><span data-stu-id="b262e-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="b262e-267">Poprawka jest przepisać w następujący sposób, zastępując jego pojedynczy wiersz kodu z sześciu wierszy kodu, które są nadal zwięzłe, `FindMatchingSymbol` łatwe do odczytania i zrozumienia i łatwe do utrzymania:</span><span class="sxs-lookup"><span data-stu-id="b262e-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="b262e-268">Ten kod nie używa metod rozszerzenia LINQ, lambdas lub wyliczaczy i nie ponosi żadnych alokacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="b262e-269">Nie ma żadnych alokacji, ponieważ kompilator może zobaczyć, że `symbols` kolekcja jest <xref:System.Collections.Generic.List%601> i może powiązać wynikowy wyliczacz (strukturę) ze zmienną lokalną o odpowiednim typie, aby uniknąć boksu.</span><span class="sxs-lookup"><span data-stu-id="b262e-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="b262e-270">Oryginalna wersja tej funkcji był doskonałym przykładem ekspresji moc C# i produktywności .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b262e-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="b262e-271">Ta nowa i bardziej wydajna wersja zachowuje te cechy bez dodawania żadnego złożonego kodu do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="b262e-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>
  
### <a name="async-method-caching"></a><span data-ttu-id="b262e-272">Buforowanie metody asynchronii</span><span class="sxs-lookup"><span data-stu-id="b262e-272">Async method caching</span></span>  

<span data-ttu-id="b262e-273">W następnym przykładzie pokazano typowy problem podczas próby użycia buforowanych wyników w metodzie [asynchronii.](../../csharp/programming-guide/concepts/async/index.md)</span><span class="sxs-lookup"><span data-stu-id="b262e-273">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="b262e-274">**Przykład 6: buforowanie metod asynchronizowych**</span><span class="sxs-lookup"><span data-stu-id="b262e-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="b262e-275">Funkcje IDE programu Visual Studio oparte na nowych kompilatorach Języka C# i Visual Basic często pobierają drzewa składni, a kompilatory używają asynchronacji, aby zachować responsywność programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b262e-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="b262e-276">Oto pierwsza wersja kodu, który można napisać, aby uzyskać drzewo składni:</span><span class="sxs-lookup"><span data-stu-id="b262e-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="b262e-277">Widać, że `GetSyntaxTreeAsync()` wywołanie wywołuje `Parser`wystąpienia , analizuje kod, a <xref:System.Threading.Tasks.Task> następnie `Task<SyntaxTree>`zwraca obiekt, .</span><span class="sxs-lookup"><span data-stu-id="b262e-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="b262e-278">Kosztowna część jest przydzielanie `Parser` wystąpienia i analizowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="b262e-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="b262e-279">Funkcja <xref:System.Threading.Tasks.Task> zwraca, dzięki czemu wywołujący mogą oczekiwać na pracę analizy i zwolnić wątku interfejsu użytkownika, aby reagować na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b262e-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>
  
 <span data-ttu-id="b262e-280">Kilka funkcji programu Visual Studio może próbować uzyskać tego samego drzewa składni, więc można napisać następujący kod do pamięci podręcznej wynik analizy, aby zaoszczędzić czas i alokacje.</span><span class="sxs-lookup"><span data-stu-id="b262e-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="b262e-281">Jednak ten kod ponosi alokacji:</span><span class="sxs-lookup"><span data-stu-id="b262e-281">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="b262e-282">Widzisz, że nowy kod z buforowania ma `SyntaxTree` pole o nazwie `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="b262e-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="b262e-283">Gdy to pole `GetSyntaxTreeAsync()` ma wartość null, wykonuje pracę i zapisuje wynik w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b262e-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="b262e-284">`GetSyntaxTreeAsync()`zwraca `SyntaxTree` obiekt.</span><span class="sxs-lookup"><span data-stu-id="b262e-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="b262e-285">Problem polega na tym, `async` że `Task<SyntaxTree>`gdy masz funkcję typu `SyntaxTree`, a zwracasz wartość typu, kompilator emituje `Task<SyntaxTree>.FromResult()`kod, aby przydzielić zadanie do przechowywania wyniku (za pomocą ).</span><span class="sxs-lookup"><span data-stu-id="b262e-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="b262e-286">Zadanie jest oznaczone jako ukończone, a wynik jest natychmiast dostępny.</span><span class="sxs-lookup"><span data-stu-id="b262e-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="b262e-287">W kodzie dla nowych <xref:System.Threading.Tasks.Task> kompilatorów obiekty, które zostały już ukończone wystąpił tak często, że ustalenie tych alokacji znacznie poprawiła czas reakcji.</span><span class="sxs-lookup"><span data-stu-id="b262e-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>
  
 <span data-ttu-id="b262e-288">**Poprawka na przykład 6**</span><span class="sxs-lookup"><span data-stu-id="b262e-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="b262e-289">Aby usunąć <xref:System.Threading.Tasks.Task> ukończoną alokację, można buforować obiekt Zadanie z ukończonym wynikiem:</span><span class="sxs-lookup"><span data-stu-id="b262e-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="b262e-290">Ten kod zmienia `cachedResult` typ `Task<SyntaxTree>` funkcji `async` pomocnika, która przechowuje oryginalny `GetSyntaxTreeAsync()`kod z .</span><span class="sxs-lookup"><span data-stu-id="b262e-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="b262e-291">`GetSyntaxTreeAsync()`teraz używa [operatora scalania null](../../csharp/language-reference/operators/null-coalescing-operator.md) `cachedResult` do zwrócenia, jeśli nie jest null.</span><span class="sxs-lookup"><span data-stu-id="b262e-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="b262e-292">Jeśli `cachedResult` jest null, a następnie `GetSyntaxTreeAsync()` wywołuje `GetSyntaxTreeUncachedAsync()` i buforuje wynik.</span><span class="sxs-lookup"><span data-stu-id="b262e-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="b262e-293">Należy `GetSyntaxTreeAsync()` zauważyć, że nie `GetSyntaxTreeUncachedAsync()` oczekuje na wywołanie, jak kod normalnie.</span><span class="sxs-lookup"><span data-stu-id="b262e-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="b262e-294">Nieużywany await `GetSyntaxTreeUncachedAsync()` oznacza, `GetSyntaxTreeAsync()` że gdy <xref:System.Threading.Tasks.Task>zwraca jego <xref:System.Threading.Tasks.Task> obiekt, natychmiast zwraca .</span><span class="sxs-lookup"><span data-stu-id="b262e-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="b262e-295">Teraz buforowany wynik jest <xref:System.Threading.Tasks.Task>, więc nie ma żadnych alokacji, aby zwrócić wynik w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b262e-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>
  
### <a name="additional-considerations"></a><span data-ttu-id="b262e-296">Dodatkowe zagadnienia</span><span class="sxs-lookup"><span data-stu-id="b262e-296">Additional considerations</span></span>  
 <span data-ttu-id="b262e-297">Oto kilka punktów dotyczących potencjalnych problemów w dużych aplikacjach lub aplikacjach, które przetwarzają dużo danych.</span><span class="sxs-lookup"><span data-stu-id="b262e-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>
  
 <span data-ttu-id="b262e-298">**Słowniki**</span><span class="sxs-lookup"><span data-stu-id="b262e-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="b262e-299">Słowniki są używane wszechobecne w wielu programach, i choć słowniki są bardzo wygodne i z natury skuteczne.</span><span class="sxs-lookup"><span data-stu-id="b262e-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="b262e-300">Jednak są one często używane niewłaściwie.</span><span class="sxs-lookup"><span data-stu-id="b262e-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="b262e-301">W programie Visual Studio i nowych kompilatorów analizy pokazuje, że wiele słowników zawiera jeden element lub były puste.</span><span class="sxs-lookup"><span data-stu-id="b262e-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="b262e-302">Pusty <xref:System.Collections.Generic.Dictionary%602> ma dziesięć pól i zajmuje 48 bajtów na stercie na komputerze x86.</span><span class="sxs-lookup"><span data-stu-id="b262e-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="b262e-303">Słowniki są świetne, gdy potrzebujesz struktury mapowania lub danych zespolowych z wyszukiwaniem w czasie stałym.</span><span class="sxs-lookup"><span data-stu-id="b262e-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="b262e-304">Jednak, gdy masz tylko kilka elementów, tracisz dużo miejsca za pomocą słownika.</span><span class="sxs-lookup"><span data-stu-id="b262e-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="b262e-305">Zamiast tego, na przykład, można iteratively patrzeć przez `List<KeyValuePair\<K,V>>`, tak szybko.</span><span class="sxs-lookup"><span data-stu-id="b262e-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="b262e-306">Jeśli słownik jest używany tylko do ładowania go z danymi, a następnie odczytać z niego (bardzo często wzorzec), przy użyciu tablicy posortowane z N(log(N)) wyszukiwania może być prawie tak szybko, w zależności od liczby elementów, których używasz.</span><span class="sxs-lookup"><span data-stu-id="b262e-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>
  
 <span data-ttu-id="b262e-307">**Klasy a struktury**</span><span class="sxs-lookup"><span data-stu-id="b262e-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="b262e-308">W pewnym sensie klasy i struktury zapewniają klasyczny kompromis przestrzeni/czasu do strojenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b262e-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="b262e-309">Klasy ponoszą 12 bajtów narzutów na komputerze x86, nawet jeśli nie mają żadnych pól, ale są one niedrogie do przekazania, ponieważ zajmuje tylko wskaźnik do odwoływania się do wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="b262e-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="b262e-310">Struktury nie ponoszą alokacji sterty, jeśli nie są one zapakowane, ale po przeniesieniu dużych struktur jako argumenty funkcji lub zwracanie wartości, zajmuje czas procesora CPU, aby niepodzielnie skopiować wszystkie elementy członkowskie danych struktur.</span><span class="sxs-lookup"><span data-stu-id="b262e-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="b262e-311">Uważaj na powtarzające się wywołania właściwości, które zwracają struktury i buforują wartość właściwości w zmiennej lokalnej, aby uniknąć nadmiernego kopiowania danych.</span><span class="sxs-lookup"><span data-stu-id="b262e-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>
  
 <span data-ttu-id="b262e-312">**Pamięci podręczne**</span><span class="sxs-lookup"><span data-stu-id="b262e-312">**Caches**</span></span>  
  
 <span data-ttu-id="b262e-313">Typowym trikiem wydajności jest buforowanie wyników.</span><span class="sxs-lookup"><span data-stu-id="b262e-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="b262e-314">Jednak pamięć podręczna bez ograniczenia rozmiaru lub zasady usuwania może być przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="b262e-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="b262e-315">Podczas przetwarzania dużych ilości danych, jeśli trzymasz dużo pamięci w pamięci podręcznej, może spowodować wyrzucanie elementów bezużytecznych zastąpić korzyści z wyszukiwania w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b262e-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>
  
 <span data-ttu-id="b262e-316">W tym artykule omówiliśmy, jak należy pamiętać o objawów wąskiego gardła wydajności, które mogą mieć wpływ na szybkość reakcji aplikacji, szczególnie w przypadku dużych systemów lub systemów, które przetwarzają dużą ilość danych.</span><span class="sxs-lookup"><span data-stu-id="b262e-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="b262e-317">Typowe winowajców obejmują boks, manipulacje ciągami, LINQ i lambda, buforowanie metod asynchronizowanych, buforowanie bez limitu rozmiaru lub zasady usuwania, niewłaściwe użycie słowników i przekazywanie struktur.</span><span class="sxs-lookup"><span data-stu-id="b262e-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="b262e-318">Pamiętaj o czterech faktach dotyczących dostrajania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b262e-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="b262e-319">Nie optymalizuj przedwcześnie — bądź produktywny i dostrajaj aplikację, gdy zauważysz problemy.</span><span class="sxs-lookup"><span data-stu-id="b262e-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>
  
- <span data-ttu-id="b262e-320">Profile nie kłamią – zgadujesz, jeśli nie mierzysz.</span><span class="sxs-lookup"><span data-stu-id="b262e-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>
  
- <span data-ttu-id="b262e-321">Dobre narzędzia robią różnicę - pobierz PerfView i wypróbuj.</span><span class="sxs-lookup"><span data-stu-id="b262e-321">Good tools make all the difference – download PerfView and try it out.</span></span>
  
- <span data-ttu-id="b262e-322">Chodzi o alokacje — to jest, gdy zespół platformy kompilator spędził większość czasu na poprawę wydajności nowych kompilatorów.</span><span class="sxs-lookup"><span data-stu-id="b262e-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b262e-323">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b262e-323">See also</span></span>

- [<span data-ttu-id="b262e-324">Film przedstawiający prezentację tego tematu</span><span class="sxs-lookup"><span data-stu-id="b262e-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="b262e-325">Przewodnik dla początkujących do profilowania wydajności</span><span class="sxs-lookup"><span data-stu-id="b262e-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="b262e-326">Wydajność</span><span class="sxs-lookup"><span data-stu-id="b262e-326">Performance</span></span>](index.md)
- <span data-ttu-id="b262e-327">[Wskazówki dotyczące wydajności .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="b262e-327">[.NET Performance Tips](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span></span>
- [<span data-ttu-id="b262e-328">Samouczek Kanału 9 PerfView</span><span class="sxs-lookup"><span data-stu-id="b262e-328">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="b262e-329">Zestaw SDK platformy kompilatora platformy .NET</span><span class="sxs-lookup"><span data-stu-id="b262e-329">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="b262e-330">repozytorium dotnet/roslyn na GitHub</span><span class="sxs-lookup"><span data-stu-id="b262e-330">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
