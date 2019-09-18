---
title: Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e4b5822306fa8f4e6b4437f4a1bef92b53a86b9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046135"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="b153d-102">Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b153d-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="b153d-103">Ten artykuł zawiera wskazówki dotyczące poprawy wydajności dużych .NET Framework aplikacji lub aplikacji, które przetwarzają duże ilości danych, takich jak pliki lub bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b153d-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="b153d-104">Te porady pochodzą z ponownego zapisywania kompilatorów C# i Visual Basic w kodzie zarządzanym, a ten artykuł zawiera kilka rzeczywistych przykładów z C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b153d-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="b153d-105">.NET Framework jest wysoce wydajny w przypadku kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b153d-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="b153d-106">Zaawansowane i bezpieczne języki oraz bogate kolekcje bibliotek sprawiają, że tworzenie aplikacji jest wysoce rozwijającemu.</span><span class="sxs-lookup"><span data-stu-id="b153d-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="b153d-107">Jednak dzięki doskonałej produktywności spoczywa odpowiedzialność.</span><span class="sxs-lookup"><span data-stu-id="b153d-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="b153d-108">Należy używać wszystkich możliwości .NET Framework, ale należy przygotować się do dostrajania wydajności kodu, jeśli jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="b153d-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span> 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="b153d-109">Dlaczego Nowa wydajność kompilatora ma zastosowanie do aplikacji</span><span class="sxs-lookup"><span data-stu-id="b153d-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="b153d-110">Zespół .NET Compiler Platform ("Roslyn") zapisał w kodzie C# zarządzanym i Visual Basic kompilatory w celu udostępnienia nowych interfejsów API do modelowania i analizowania kodu, tworzenia narzędzi i włączania znacznie bogatszych rozwiązań obsługujących kod w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b153d-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="b153d-111">Przepisanie kompilatorów i Tworzenie środowiska programu Visual Studio na nowych kompilatorach ujawniło przydatny wgląd w dane dotyczące wydajności, które mają zastosowanie do dowolnej dużej aplikacji .NET Framework lub dowolnej aplikacji, która przetwarza dużą ilość danych.</span><span class="sxs-lookup"><span data-stu-id="b153d-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="b153d-112">Nie musisz wiedzieć o kompilatorach, aby skorzystać z szczegółowych informacji i przykładów z C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b153d-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="b153d-113">Program Visual Studio korzysta z interfejsów API kompilatora do kompilowania wszystkich funkcji IntelliSense, które są miłość przez użytkowników, takich jak kolorowanie identyfikatorów i słów kluczowych, listy uzupełniania składni, zygzaki dla błędów, wskazówki dotyczące parametrów, problemy z kodem i akcje związane z kodem.</span><span class="sxs-lookup"><span data-stu-id="b153d-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="b153d-114">Program Visual Studio udostępnia tę pomoc podczas wpisywania i zmieniania kodu przez deweloperów, a program Visual Studio musi przestać odpowiadać, gdy kompilator ciągle modeluje deweloperów kodu.</span><span class="sxs-lookup"><span data-stu-id="b153d-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span> 
  
 <span data-ttu-id="b153d-115">Gdy użytkownicy końcowi współpracują z aplikacją, spodziewają się, że odpowiadają.</span><span class="sxs-lookup"><span data-stu-id="b153d-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="b153d-116">Wpisywanie lub obsługa poleceń nie powinna być nigdy blokowana.</span><span class="sxs-lookup"><span data-stu-id="b153d-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="b153d-117">Pomoc powinna być wyświetlona szybko lub w przypadku, gdy użytkownik kontynuuje wpisywanie.</span><span class="sxs-lookup"><span data-stu-id="b153d-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="b153d-118">Aplikacja powinna unikać blokowania wątku interfejsu użytkownika z długimi obliczeniami, które sprawiają, że aplikacja jest powolna.</span><span class="sxs-lookup"><span data-stu-id="b153d-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span> 
  
 <span data-ttu-id="b153d-119">Aby uzyskać więcej informacji na temat kompilatorów Roslyn, zobacz [zestaw SDK .NET compiler platform](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="b153d-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="b153d-120">Tylko fakty</span><span class="sxs-lookup"><span data-stu-id="b153d-120">Just the Facts</span></span>  
 <span data-ttu-id="b153d-121">Te fakty należy wziąć pod uwagę podczas dostrajania wydajności i tworzenia odpowiedzi .NET Framework aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b153d-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span> 
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="b153d-122">Fakt 1: Nie Optymalizuj przedwcześnie</span><span class="sxs-lookup"><span data-stu-id="b153d-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="b153d-123">Pisanie kodu, który jest bardziej skomplikowany niż musi być związane z konserwacją, debugowaniem i polerowaniem.</span><span class="sxs-lookup"><span data-stu-id="b153d-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="b153d-124">Doświadczeni programiści mają intuicyjny opanujesz sposobu rozwiązywania problemów z kodowaniem i pisania bardziej wydajnego kodu.</span><span class="sxs-lookup"><span data-stu-id="b153d-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="b153d-125">Jednak czasami w sposób przedwcześnie optymalizuje swój kod.</span><span class="sxs-lookup"><span data-stu-id="b153d-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="b153d-126">Na przykład korzystają one z tabeli skrótów, gdy prosta tablica wystarcza, lub użyj skomplikowanej pamięci podręcznej, która może wyciekać pamięć, a nie po prostu reobliczaniu wartości.</span><span class="sxs-lookup"><span data-stu-id="b153d-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="b153d-127">Nawet jeśli jesteś programistą, należy przetestować wydajność i analizować kod, gdy znajdziesz problemy.</span><span class="sxs-lookup"><span data-stu-id="b153d-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span> 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="b153d-128">Fakt 2: Jeśli nie mierzy się, nastąpi odgadnięcie</span><span class="sxs-lookup"><span data-stu-id="b153d-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="b153d-129">Profile i pomiary nie znajdują się.</span><span class="sxs-lookup"><span data-stu-id="b153d-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="b153d-130">Profile pokazują, czy procesor CPU jest w pełni załadowany, czy też jest blokowany na dyskach we/wy.</span><span class="sxs-lookup"><span data-stu-id="b153d-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="b153d-131">Profile informują o rodzaju i ilości pamięci, która jest przydzielana, oraz o tym, czy procesor CPU poświęca dużo czasu na [wyrzucanie elementów bezużytecznych](../../standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="b153d-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span> 
  
 <span data-ttu-id="b153d-132">Należy ustawić cele wydajnościowe najważniejszych środowisk klienta lub scenariuszy w aplikacji oraz testy zapisu w celu mierzenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="b153d-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="b153d-133">Zbadaj nieudane testy, stosując metodę naukową: Użyj profilów, aby Ci pomóc, hypothesize się, co może być problemem, i przetestuj hipotezę przy użyciu eksperymentu lub zmiany kodu.</span><span class="sxs-lookup"><span data-stu-id="b153d-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="b153d-134">Ustalaj bazowe pomiary wydajności w czasie z regularnym testowaniem, dzięki czemu można izolować zmiany powodujące wydajność regresji.</span><span class="sxs-lookup"><span data-stu-id="b153d-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="b153d-135">Dzięki podejściu wydajności w rygorystyczny sposób można uniknąć marnowania czasu z niepotrzebnymi aktualizacjami kodu.</span><span class="sxs-lookup"><span data-stu-id="b153d-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span> 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="b153d-136">Fakt 3: Dobre narzędzia sprawiają, że wszystkie różnice</span><span class="sxs-lookup"><span data-stu-id="b153d-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="b153d-137">Dobre narzędzia pozwalają szybko przechodzić do największych problemów z wydajnością (procesor CPU, pamięć lub dysk) i pomóc w znalezieniu kodu, który powoduje te wąskie gardła.</span><span class="sxs-lookup"><span data-stu-id="b153d-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="b153d-138">Firma Microsoft dostarcza różnorodne narzędzia do oceny wydajności, takie jak [program Visual Studio profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) i [Narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="b153d-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span> 
  
 <span data-ttu-id="b153d-139">Narzędzia PerfView to bezpłatne i wszechstronne narzędzie, które ułatwia skoncentrowanie się na szczegółowych problemach, takich jak we/wy dysku, zdarzenia GC i pamięć.</span><span class="sxs-lookup"><span data-stu-id="b153d-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="b153d-140">Można przechwytywać zdarzenia [śledzenia zdarzeń dotyczące wydajności dla systemu Windows](../wcf/samples/etw-tracing.md) (ETW) i łatwo przeglądać dla każdej aplikacji, na jeden proces, na stos i informacje o wątkach.</span><span class="sxs-lookup"><span data-stu-id="b153d-140">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="b153d-141">Narzędzia PerfView pokazuje, jak dużo i jakiego rodzaju pamięci przydziela aplikacja oraz które funkcje lub stosy wywołań przyczyniają się do przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="b153d-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="b153d-142">Aby uzyskać szczegółowe informacje, zobacz temat rozbudowane tematy pomocy, pokazy i filmy wideo dołączone do narzędzia (na przykład [samouczki narzędzia PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) w witrynie Channel 9).</span><span class="sxs-lookup"><span data-stu-id="b153d-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span> 
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="b153d-143">Fakt 4: Wszystkie przydziały</span><span class="sxs-lookup"><span data-stu-id="b153d-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="b153d-144">Możesz zastanowić się nad tworzeniem aplikacji, która odpowiada .NET Framework wszystkim algorytmom, na przykład przy użyciu szybkiego sortowania zamiast sortowania bąbelkowego, ale nie jest to przypadek.</span><span class="sxs-lookup"><span data-stu-id="b153d-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="b153d-145">Największym czynnikiem podczas tworzenia aplikacji, która odpowiada, jest przydzielanie pamięci, zwłaszcza gdy aplikacja jest bardzo duża lub przetwarza duże ilości danych.</span><span class="sxs-lookup"><span data-stu-id="b153d-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span> 
  
 <span data-ttu-id="b153d-146">Prawie wszystkie prace do tworzenia odpowiedzi na środowisko IDE dzięki nowym interfejsom API kompilatora, które mają na celu uniknięcie alokacji i zarządzania strategiami buforowania.</span><span class="sxs-lookup"><span data-stu-id="b153d-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="b153d-147">Ślady narzędzia PerfView pokazują, że wydajność nowych C# i kompilatorów Visual Basic jest rzadko związana z procesorem CPU.</span><span class="sxs-lookup"><span data-stu-id="b153d-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="b153d-148">Kompilatory mogą być powiązane we/wy w przypadku odczytywania setek tysięcy lub milionów wierszy kodu, odczytywania metadanych lub emitowania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="b153d-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="b153d-149">Opóźnienia wątku interfejsu użytkownika są niemal wszystkie ze względu na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b153d-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="b153d-150">.NET Framework GC jest wysoce dostrojony do wydajności i wykonuje wiele zadań jednocześnie podczas wykonywania kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b153d-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="b153d-151">Jednak pojedyncze alokacje mogą wyzwalać kosztowną kolekcję [Gen2](../../standard/garbage-collection/fundamentals.md) , zatrzymując wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="b153d-151">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span> 
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="b153d-152">Typowe alokacje i przykłady</span><span class="sxs-lookup"><span data-stu-id="b153d-152">Common allocations and examples</span></span>  
 <span data-ttu-id="b153d-153">W przykładowych wyrażeniach w tej sekcji znajdują się ukryte przydziały, które są wyświetlane jako małe.</span><span class="sxs-lookup"><span data-stu-id="b153d-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="b153d-154">Jeśli jednak duża aplikacja wykonuje wyrażenia wystarczająco długo, może to spowodować setki megabajtów, nawet gigabajtów przydziałów.</span><span class="sxs-lookup"><span data-stu-id="b153d-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="b153d-155">Na przykład testy jednominutowe, które symulują wpisywanie przez dewelopera w edytorze przydzieloną gigabajty pamięci i doprowadziły do skoncentrowania się zespołu wydajności w przypadku wpisywania scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="b153d-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span> 
  
### <a name="boxing"></a><span data-ttu-id="b153d-156">Boxing</span><span class="sxs-lookup"><span data-stu-id="b153d-156">Boxing</span></span>  
 <span data-ttu-id="b153d-157">[Opakowanie](../../csharp/programming-guide/types/boxing-and-unboxing.md) występuje, gdy typy wartości, które zwykle znajdują się na stosie lub w strukturach danych, są zawijane w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="b153d-157">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="b153d-158">Oznacza to, że przydzielasz obiekt do przechowywania danych, a następnie zwracasz wskaźnik do obiektu.</span><span class="sxs-lookup"><span data-stu-id="b153d-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="b153d-159">.NET Framework czasami pola wartości ze względu na podpis metody lub typu lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="b153d-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="b153d-160">Otoka typu wartości w obiekcie powoduje alokację pamięci.</span><span class="sxs-lookup"><span data-stu-id="b153d-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="b153d-161">Wiele operacji pakowania może współtworzyć megabajty lub gigabajty alokacji dla aplikacji, co oznacza, że aplikacja spowoduje więcej operacje odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="b153d-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="b153d-162">.NET Framework i kompilatory języka unikają pakowania, gdy jest to możliwe, ale czasami zdarza się, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="b153d-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span> 
  
 <span data-ttu-id="b153d-163">Aby zobaczyć opakowanie w narzędzia PerfView, Otwórz ślad i sprawdź stosy alokacji sterty GC pod nazwą procesu aplikacji (Pamiętaj, narzędzia PerfView raporty dotyczące wszystkich procesów).</span><span class="sxs-lookup"><span data-stu-id="b153d-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="b153d-164">Jeśli widzisz typy takie <xref:System.Int32?displayProperty=nameWithType> jak <xref:System.Char?displayProperty=nameWithType> i w obszarze alokacje, nastąpi wypakowywanie typów wartości.</span><span class="sxs-lookup"><span data-stu-id="b153d-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="b153d-165">Wybranie jednego z tych typów spowoduje wyświetlenie stosów i funkcji, w których są one opakowane.</span><span class="sxs-lookup"><span data-stu-id="b153d-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span> 
  
 <span data-ttu-id="b153d-166">**Przykład 1: metody ciągów i argumenty typu wartości**</span><span class="sxs-lookup"><span data-stu-id="b153d-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="b153d-167">Ten przykładowy kod ilustruje potencjalnie niepotrzebne i nadmierne opakowanie:</span><span class="sxs-lookup"><span data-stu-id="b153d-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="b153d-168">Ten kod udostępnia funkcje rejestrowania, dzięki czemu aplikacja może często wywoływać `Log` funkcję, co może być miliony razy.</span><span class="sxs-lookup"><span data-stu-id="b153d-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="b153d-169">Problem polega na tym, że wywołanie `string.Format` jest rozpoznawane <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> jako Przeciążenie.</span><span class="sxs-lookup"><span data-stu-id="b153d-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span> 
  
 <span data-ttu-id="b153d-170">To Przeciążenie wymaga .NET Framework do `int` umieszczania wartości w obiektach, aby przekazać je do tego wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="b153d-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="b153d-171">Częściowa poprawka polega na wywołaniu `id.ToString()` i `size.ToString()` przejściu wszystkich ciągów (które `string.Format` są obiektami) do wywołania.</span><span class="sxs-lookup"><span data-stu-id="b153d-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="b153d-172">Wywołanie `ToString()` przydzieli ciąg, ale ta alokacja będzie nadal w `string.Format`obrębie.</span><span class="sxs-lookup"><span data-stu-id="b153d-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span> 
  
 <span data-ttu-id="b153d-173">Można wziąć pod uwagę, że to podstawowe `string.Format` wywołanie jest tylko ciąg łączenia, więc można napisać ten kod zamiast:</span><span class="sxs-lookup"><span data-stu-id="b153d-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="b153d-174">Jednak ten wiersz kodu wprowadza alokację opakowania, ponieważ kompiluje się do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="b153d-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="b153d-175">.NET Framework musi mieć pole literału znakowego do wywołania`Concat`</span><span class="sxs-lookup"><span data-stu-id="b153d-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="b153d-176">**Poprawka na przykład 1**</span><span class="sxs-lookup"><span data-stu-id="b153d-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="b153d-177">Pełna poprawka jest prosta.</span><span class="sxs-lookup"><span data-stu-id="b153d-177">The complete fix is simple.</span></span> <span data-ttu-id="b153d-178">Po prostu Zastąp literał znakowy literałem ciągu, który nie jest używany, ponieważ ciągi są już obiektami:</span><span class="sxs-lookup"><span data-stu-id="b153d-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="b153d-179">**Przykład 2: opakowanie enum**</span><span class="sxs-lookup"><span data-stu-id="b153d-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="b153d-180">Ten przykład był odpowiedzialny za ogromną ilość przydziału w nowych C# i Visual Basic kompilatorach ze względu na częste korzystanie z typów wyliczeniowych, szczególnie w operacjach wyszukiwania słownika.</span><span class="sxs-lookup"><span data-stu-id="b153d-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span> 
  
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
  
 <span data-ttu-id="b153d-181">Ten problem jest bardzo delikatny.</span><span class="sxs-lookup"><span data-stu-id="b153d-181">This problem is very subtle.</span></span> <span data-ttu-id="b153d-182">Narzędzia PerfView mógłby zgłosić ten fakt <xref:System.Enum.GetHashCode> jako opakowanie, ponieważ metoda pola przedstawia podstawową reprezentację typu wyliczenia, ze względów związanych z implementacją.</span><span class="sxs-lookup"><span data-stu-id="b153d-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="b153d-183">Jeśli szukasz blisko w narzędzia PerfView, mogą zostać wyświetlone dwa przydziały dla każdego wywołania <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="b153d-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="b153d-184">Kompilator wstawia jeden, a .NET Framework wstawia pozostałe.</span><span class="sxs-lookup"><span data-stu-id="b153d-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span> 
  
 <span data-ttu-id="b153d-185">**Poprawka na przykład 2**</span><span class="sxs-lookup"><span data-stu-id="b153d-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="b153d-186">Można łatwo uniknąć obydwu przydziałów przez rzutowanie na podstawową reprezentację przed wywołaniem <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="b153d-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="b153d-187">Innym wspólnym źródłem opakowania w typach wyliczeniowych jest <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="b153d-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b153d-188">Argument przeszedł do <xref:System.Enum.HasFlag%28System.Enum%29> musi być opakowany.</span><span class="sxs-lookup"><span data-stu-id="b153d-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="b153d-189">W większości przypadków zastępowanie wywołań <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> z testem bitowym jest prostsze i bezpłatne.</span><span class="sxs-lookup"><span data-stu-id="b153d-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span> 
  
 <span data-ttu-id="b153d-190">Zachowaj pierwszy fakt wydajności (to oznacza, że nie jest przedwcześnie zoptymalizowany) i nie rozpoczynaj ponownego zapisywania całego kodu w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="b153d-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="b153d-191">Zapoznaj się z tymi kosztami opakowania, ale Zmień kod tylko po przeprowadzeniu profilowania aplikacji i znalezieniu aktywnych miejsc.</span><span class="sxs-lookup"><span data-stu-id="b153d-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span> 
  
### <a name="strings"></a><span data-ttu-id="b153d-192">Ciągi</span><span class="sxs-lookup"><span data-stu-id="b153d-192">Strings</span></span>  
 <span data-ttu-id="b153d-193">Manipulowanie ciągami to niektóre największe culprits dla przydziałów i często są one wyświetlane w narzędzia PerfView w pierwszych pięciu alokacjach.</span><span class="sxs-lookup"><span data-stu-id="b153d-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="b153d-194">Programy używają ciągów do serializacji, JSON i interfejsów API REST.</span><span class="sxs-lookup"><span data-stu-id="b153d-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="b153d-195">Można używać ciągów jako stałych programistycznych do współdziałania z systemami, gdy nie można używać typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="b153d-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="b153d-196">Gdy profilowanie pokazuje <xref:System.String> , że ciągi mają wysoce wpływ na wydajność, należy poszukać wywołań metod, takich jak <xref:System.String.Join%2A> <xref:System.String.Format%2A>, <xref:System.String.Substring%2A> <xref:System.String.Concat%2A> <xref:System.String.Split%2A>,,, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b153d-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="b153d-197">Użycie <xref:System.Text.StringBuilder> usługi pozwala uniknąć ponoszenia kosztów tworzenia jednego ciągu z wielu kawałków, ale nawet przydzielenie <xref:System.Text.StringBuilder> obiektu może stać się wąskim gardłem, który trzeba zarządzać.</span><span class="sxs-lookup"><span data-stu-id="b153d-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span> 
  
 <span data-ttu-id="b153d-198">**Przykład 3: operacje na ciągach**</span><span class="sxs-lookup"><span data-stu-id="b153d-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="b153d-199">C# Kompilator miał ten kod, który zapisuje tekst sformatowanego komentarza dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="b153d-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="b153d-200">Można zobaczyć, że ten kod wykonuje wiele operacji manipulowania ciągiem.</span><span class="sxs-lookup"><span data-stu-id="b153d-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="b153d-201">Kod używa metod biblioteki do dzielenia wierszy na osobne ciągi, do przycinania białego znaku, aby sprawdzić, czy `text` argument jest komentarzem dokumentacji XML i wyodrębnić podciągi z wierszy.</span><span class="sxs-lookup"><span data-stu-id="b153d-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span> 
  
 <span data-ttu-id="b153d-202">W pierwszym wierszu wewnątrz `WriteFormattedDocComment` `text.Split` , wywołanie przydziela nową tablicę trzech elementów jako argument przy każdym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="b153d-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="b153d-203">Kompilator musi emitować kod, aby przydzielić tę tablicę za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="b153d-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="b153d-204">Dzieje się tak, ponieważ kompilator nie wie <xref:System.String.Split%2A> , czy przechowuje tablicę w miejscu, w którym tablica może być modyfikowana przez inny kod, co `WriteFormattedDocComment`wpłynie na późniejsze wywołania do.</span><span class="sxs-lookup"><span data-stu-id="b153d-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="b153d-205">Wywołanie w celu <xref:System.String.Split%2A> przydzielania również ciągu dla każdego wiersza w `text` i przydziela inne pamięci do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="b153d-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span> 
  
 <span data-ttu-id="b153d-206">`WriteFormattedDocComment`ma trzy wywołania <xref:System.String.TrimStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b153d-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="b153d-207">Dwa znajdują się w wewnętrznych pętlach, które duplikują zadania i przydziały.</span><span class="sxs-lookup"><span data-stu-id="b153d-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="b153d-208">Aby przyczynić się do gorszenia <xref:System.String.TrimStart%2A> , wywołanie metody bez argumentów przypisuje pustą tablicę ( `params` dla parametru) oprócz wyniku ciągu.</span><span class="sxs-lookup"><span data-stu-id="b153d-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span> 
  
 <span data-ttu-id="b153d-209">Na koniec istnieje wywołanie <xref:System.String.Substring%2A> metody, która zwykle przypisuje nowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="b153d-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span> 
  
 <span data-ttu-id="b153d-210">**Poprawka na przykład 3**</span><span class="sxs-lookup"><span data-stu-id="b153d-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="b153d-211">W przeciwieństwie do wcześniejszych przykładów, małe edycje nie mogą naprawić tych przydziałów.</span><span class="sxs-lookup"><span data-stu-id="b153d-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="b153d-212">Należy wykonać krok po kroku, przyjrzeć się problemowi i zastosować go inaczej.</span><span class="sxs-lookup"><span data-stu-id="b153d-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="b153d-213">Na przykład można zauważyć, że argument `WriteFormattedDocComment()` jest ciągiem, który zawiera wszystkie informacje, których potrzebuje Metoda, więc kod może przetworzyć więcej indeksowania zamiast alokowania wiele ciągów częściowych.</span><span class="sxs-lookup"><span data-stu-id="b153d-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span> 
  
 <span data-ttu-id="b153d-214">Zespół wydajności kompilatora wszystkie te przydziały z kodem podobnym do poniższego:</span><span class="sxs-lookup"><span data-stu-id="b153d-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="b153d-215">Pierwsza wersja `WriteFormattedDocComment()` przydzieloną tablicę, kilka podciągów i przycięty podciąg wraz z pustą `params` tablicą.</span><span class="sxs-lookup"><span data-stu-id="b153d-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="b153d-216">Sprawdzana jest również wartość "///".</span><span class="sxs-lookup"><span data-stu-id="b153d-216">It also checked for "///".</span></span> <span data-ttu-id="b153d-217">Poprawiony kod używa tylko indeksowania i alokuje Nothing.</span><span class="sxs-lookup"><span data-stu-id="b153d-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="b153d-218">Znajduje pierwszy znak, który nie jest biały, a następnie sprawdza znak według znaku, aby zobaczyć, czy ciąg rozpoczyna się od "///".</span><span class="sxs-lookup"><span data-stu-id="b153d-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="b153d-219">Nowy kod używa `IndexOfFirstNonWhiteSpaceChar` <xref:System.String.TrimStart%2A> zamiast nie zwracać pierwszego indeksu (po określonym indeksie początkowym), w którym występuje znak niebędący odstępem.</span><span class="sxs-lookup"><span data-stu-id="b153d-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="b153d-220">Naprawa nie została ukończona, ale możesz zobaczyć, jak zastosować podobne poprawki do kompletnego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b153d-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="b153d-221">Stosując to podejście w całym kodzie, można usunąć wszystkie alokacje w `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="b153d-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span> 
  
 <span data-ttu-id="b153d-222">**Przykład 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="b153d-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="b153d-223">W <xref:System.Text.StringBuilder> tym przykładzie używa obiektu.</span><span class="sxs-lookup"><span data-stu-id="b153d-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="b153d-224">Następująca funkcja generuje pełną nazwę typu dla typów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="b153d-224">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="b153d-225">Fokus znajduje się w wierszu, który tworzy nowe <xref:System.Text.StringBuilder> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b153d-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="b153d-226">Kod powoduje alokację `sb.ToString()` i wewnętrzne przydziały <xref:System.Text.StringBuilder> w ramach implementacji, ale nie można kontrolować tych alokacji, jeśli chcesz uzyskać wynik ciągu.</span><span class="sxs-lookup"><span data-stu-id="b153d-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span> 
  
 <span data-ttu-id="b153d-227">**Poprawka na przykład 4**</span><span class="sxs-lookup"><span data-stu-id="b153d-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="b153d-228">Aby naprawić `StringBuilder` alokację obiektu, przebuforuj obiekt.</span><span class="sxs-lookup"><span data-stu-id="b153d-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="b153d-229">Nawet buforowanie pojedynczego wystąpienia, które może zostać wywołane, może znacząco poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="b153d-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="b153d-230">Jest to nowa implementacja funkcji, pomijając cały kod z wyjątkiem nowych i ostatnich wierszy:</span><span class="sxs-lookup"><span data-stu-id="b153d-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="b153d-231">Najważniejsze części to nowe `AcquireBuilder()` i `GetStringAndReleaseBuilder()` funkcje:</span><span class="sxs-lookup"><span data-stu-id="b153d-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="b153d-232">Ponieważ nowe kompilatory używają wątków, te implementacje używają pola statycznego wątku (<xref:System.ThreadStaticAttribute> atrybutu) do <xref:System.Text.StringBuilder>buforowania i prawdopodobnie można forgo `ThreadStatic` deklarację.</span><span class="sxs-lookup"><span data-stu-id="b153d-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="b153d-233">Pole statyczne wątku przechowuje unikatową wartość dla każdego wątku, który wykonuje ten kod.</span><span class="sxs-lookup"><span data-stu-id="b153d-233">The thread-static field holds a unique value for each thread that executes this code.</span></span> 
  
 <span data-ttu-id="b153d-234">`AcquireBuilder()`Zwraca buforowane <xref:System.Text.StringBuilder> wystąpienie, jeśli istnieje, po jego wyczyszczeniu i ustawieniu pola lub pamięci podręcznej na wartość null.</span><span class="sxs-lookup"><span data-stu-id="b153d-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="b153d-235">W przeciwnym razie tworzy nowe wystąpienie i zwraca je, pozostawiając pole lub pamięć podręczną ustawioną na wartość null. `AcquireBuilder()`</span><span class="sxs-lookup"><span data-stu-id="b153d-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span> 
  
 <span data-ttu-id="b153d-236">Gdy wszystko będzie gotowe <xref:System.Text.StringBuilder> , należy wywołać `GetStringAndReleaseBuilder()` , aby uzyskać wynik <xref:System.Text.StringBuilder> ciągu, zapisać wystąpienie w polu lub w pamięci podręcznej, a następnie zwrócić wynik.</span><span class="sxs-lookup"><span data-stu-id="b153d-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="b153d-237">Można wykonać ponowne wprowadzenie tego kodu i utworzyć wiele <xref:System.Text.StringBuilder> obiektów (chociaż zdarza się to rzadko).</span><span class="sxs-lookup"><span data-stu-id="b153d-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="b153d-238">Kod zapisuje tylko ostatnio wydane <xref:System.Text.StringBuilder> wystąpienie do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="b153d-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="b153d-239">Ta prosta strategia buforowania znacznie zmniejsza alokacje w nowych kompilatorach.</span><span class="sxs-lookup"><span data-stu-id="b153d-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="b153d-240">Części .NET Framework i MSBuild ("MSBuild") używają podobnej metody w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="b153d-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span> 
  
 <span data-ttu-id="b153d-241">Ta prosta strategia buforowania jest zgodna z dobrym projektem pamięci podręcznej, ponieważ ma limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="b153d-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="b153d-242">Jednak więcej kodu jest teraz niż w oryginalnym, co oznacza więcej kosztów konserwacji.</span><span class="sxs-lookup"><span data-stu-id="b153d-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="b153d-243">Strategię buforowania należy zastosować tylko wtedy, gdy znaleziono problem z wydajnością, a narzędzia PerfView wykazało, <xref:System.Text.StringBuilder> że alokacje są istotnym współautorem.</span><span class="sxs-lookup"><span data-stu-id="b153d-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span> 
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="b153d-244">LINQ i lambda</span><span class="sxs-lookup"><span data-stu-id="b153d-244">LINQ and lambdas</span></span>  
<span data-ttu-id="b153d-245">W połączeniu z wyrażeniami lambda jest przykładem funkcji produktywności (LINQ, Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="b153d-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="b153d-246">Jednak jego użycie może mieć znaczny wpływ na wydajność w miarę upływu czasu i może być konieczne ponowne napisanie kodu.</span><span class="sxs-lookup"><span data-stu-id="b153d-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="b153d-247">**Przykład 5: Wyrażenia lambda, listy\<T > i IEnumerable\<t >**</span><span class="sxs-lookup"><span data-stu-id="b153d-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="b153d-248">W tym przykładzie używa [kodu LINQ i języka stylu funkcjonalności](https://blogs.msdn.microsoft.com/charlie/2007/01/27/anders-hejlsberg-on-linq-and-functional-programming/) , aby znaleźć symbol w modelu kompilatora, przy użyciu ciągu nazwy:</span><span class="sxs-lookup"><span data-stu-id="b153d-248">This example uses [LINQ and functional style code](https://blogs.msdn.microsoft.com/charlie/2007/01/27/anders-hejlsberg-on-linq-and-functional-programming/) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="b153d-249">Nowy kompilator i środowiska IDE, które są oparte na wywołaniu `FindMatchingSymbol()` IT bardzo często, i istnieje kilka ukrytych alokacji w jednym wierszu kodu tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b153d-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="b153d-250">Aby przejrzeć te przydziały, najpierw Podziel pojedynczy wiersz kodu funkcji na dwa wiersze:</span><span class="sxs-lookup"><span data-stu-id="b153d-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="b153d-251">W pierwszym wierszu [wyrażenie](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` lambda jest [zamykane](https://blogs.msdn.microsoft.com/ericlippert/2003/09/17/what-are-closures/) na zmiennej `name`lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b153d-251">In the first line, the [lambda expression](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://blogs.msdn.microsoft.com/ericlippert/2003/09/17/what-are-closures/) the local variable `name`.</span></span> <span data-ttu-id="b153d-252">Oznacza to, że oprócz przydzielenia obiektu [delegata](../../csharp/language-reference/keywords/delegate.md) , który `predicate` przechowuje, kod przydziela klasę statyczną do przechowywania środowiska, które `name`przechwytuje wartość.</span><span class="sxs-lookup"><span data-stu-id="b153d-252">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="b153d-253">Kompilator generuje kod podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="b153d-253">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="b153d-254">Dwa `new` alokacje (jeden dla klasy środowiska i jeden dla delegata) są teraz jawne.</span><span class="sxs-lookup"><span data-stu-id="b153d-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span> 
  
 <span data-ttu-id="b153d-255">Teraz przyjrzyj się `FirstOrDefault`wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="b153d-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="b153d-256">Ta metoda <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozszerzania typu powoduje również alokację.</span><span class="sxs-lookup"><span data-stu-id="b153d-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="b153d-257">`FirstOrDefault` Ponieważ<xref:System.Collections.Generic.IEnumerable%601> przyjmuje obiekt jako pierwszy argument, można rozszerzyć wywołanie do następującego kodu (uproszczony bit na potrzeby dyskusji):</span><span class="sxs-lookup"><span data-stu-id="b153d-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="b153d-258">Zmienna ma typ <xref:System.Collections.Generic.List%601>. `symbols`</span><span class="sxs-lookup"><span data-stu-id="b153d-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="b153d-259"><xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerator%601> `struct`Typ kolekcji implementuje i Cleverly definiuje<xref:System.Collections.Generic.List%601> moduł wyliczający (interfejs) implementujący za pomocą. <xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="b153d-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="b153d-260">Użycie struktury zamiast klasy oznacza zwykle uniknięcie przydziałów sterty, co z kolei może wpłynąć na wydajność odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="b153d-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="b153d-261">Moduły wyliczające są zwykle używane z `foreach` pętlą języka, która używa struktury modułu wyliczającego, gdy zostanie zwrócona na stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="b153d-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="b153d-262">Zwiększenie wskaźnika stosu wywołań w celu zapewnienia pokoju dla obiektu nie ma wpływu na sposób alokacji sterty.</span><span class="sxs-lookup"><span data-stu-id="b153d-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span> 
  
 <span data-ttu-id="b153d-263">W przypadku wywołania rozszerzonego `FirstOrDefault` kod musi wywołać `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b153d-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b153d-264">Przypisanie `symbols` <xref:System.Collections.Generic.List%601>do zmiennej typu `IEnumerable<Symbol>` powoduje utratę informacji, które są rzeczywistym obiektem. `enumerable`</span><span class="sxs-lookup"><span data-stu-id="b153d-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="b153d-265">Oznacza to, że gdy kod pobiera moduł wyliczający z `enumerable.GetEnumerator()`, .NET Framework musi mieć pole zwróconej struktury, aby przypisać go `enumerator` do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b153d-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span> 
  
 <span data-ttu-id="b153d-266">**Poprawka na przykład 5**</span><span class="sxs-lookup"><span data-stu-id="b153d-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="b153d-267">Poprawkę należy wykonać `FindMatchingSymbol` w następujący sposób, zamieniając swój pojedynczy wiersz kodu na sześć wierszy kodu, które są nadal zwięzłe, czytelne i zrozumiałe oraz łatwe w obsłudze:</span><span class="sxs-lookup"><span data-stu-id="b153d-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="b153d-268">Ten kod nie używa metod rozszerzeń LINQ, wyrażeń lambda ani modułów wyliczających i nie ma żadnych przydziałów.</span><span class="sxs-lookup"><span data-stu-id="b153d-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="b153d-269">Nie ma żadnych alokacji, ponieważ kompilator może zobaczyć, że `symbols` kolekcja <xref:System.Collections.Generic.List%601> jest i może powiązać powstający moduł wyliczający (strukturę) ze zmienną lokalną z właściwym typem, aby uniknąć napakowywania.</span><span class="sxs-lookup"><span data-stu-id="b153d-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="b153d-270">Oryginalną wersją tej funkcji była doskonały Przykładowa moc C# i produktywność .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b153d-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="b153d-271">Ta nowa i wydajniejsza wersja zachowuje te cechy bez dodawania kodu złożonego do obsługi.</span><span class="sxs-lookup"><span data-stu-id="b153d-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span> 
  
### <a name="async-method-caching"></a><span data-ttu-id="b153d-272">Buforowanie metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="b153d-272">Async method caching</span></span>  

<span data-ttu-id="b153d-273">W następnym przykładzie przedstawiono typowy problem występujący podczas próby użycia zbuforowanych wyników w metodzie [asynchronicznej](../../csharp/programming-guide/concepts/async/index.md) .</span><span class="sxs-lookup"><span data-stu-id="b153d-273">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="b153d-274">**Przykład 6: buforowanie w metodach asynchronicznych**</span><span class="sxs-lookup"><span data-stu-id="b153d-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="b153d-275">Funkcje środowiska IDE programu Visual Studio oparte na nowych C# i Visual Basic kompilatorach często pobierają drzewa składniowe, a kompilatory używają Async w celu zapewnienia, że program Visual Studio reaguje.</span><span class="sxs-lookup"><span data-stu-id="b153d-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="b153d-276">Oto pierwsza wersja kodu, którą można napisać, aby uzyskać drzewo składni:</span><span class="sxs-lookup"><span data-stu-id="b153d-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="b153d-277">Można zobaczyć, że wywoływanie `GetSyntaxTreeAsync()` tworzy wystąpienia a `Parser`, analizuje kod <xref:System.Threading.Tasks.Task> , a następnie zwraca obiekt, `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="b153d-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="b153d-278">Kosztowna część przydziela `Parser` wystąpienie i analizuje kod.</span><span class="sxs-lookup"><span data-stu-id="b153d-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="b153d-279">Funkcja zwraca obiekt <xref:System.Threading.Tasks.Task> , aby wywołujący mogą oczekiwać na przeanalizowanie i zwolnić wątek interfejsu użytkownika, aby odpowiadał na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b153d-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span> 
  
 <span data-ttu-id="b153d-280">Kilka funkcji programu Visual Studio może próbować uzyskać to samo drzewo składni, więc można napisać następujący kod w celu przetworzenia pamięci podręcznej wynik analizy w celu zaoszczędzenia czasu i alokacji.</span><span class="sxs-lookup"><span data-stu-id="b153d-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="b153d-281">Jednak ten kod wiąże się z alokacją:</span><span class="sxs-lookup"><span data-stu-id="b153d-281">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="b153d-282">Zobaczysz, że nowy kod z buforowaniem ma `SyntaxTree` pole o `cachedResult`nazwie.</span><span class="sxs-lookup"><span data-stu-id="b153d-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="b153d-283">Gdy to pole ma wartość null `GetSyntaxTreeAsync()` , program wykonuje i zapisuje wynik w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b153d-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="b153d-284">`GetSyntaxTreeAsync()``SyntaxTree` zwraca obiekt.</span><span class="sxs-lookup"><span data-stu-id="b153d-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="b153d-285">Problem polega na `async` tym, że jeśli masz funkcję typu `Task<SyntaxTree>`i zwracasz wartość typu `SyntaxTree`, kompilator emituje kod w celu przydzielenia zadania do przechowywania wyniku (przy użyciu `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="b153d-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="b153d-286">Zadanie jest oznaczane jako ukończone, a wynik jest natychmiast dostępny.</span><span class="sxs-lookup"><span data-stu-id="b153d-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="b153d-287">W kodzie dla nowych kompilatorów obiekty, które <xref:System.Threading.Tasks.Task> zostały już wykonane, były tak często, że te przydziały znacznie poprawiają czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="b153d-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span> 
  
 <span data-ttu-id="b153d-288">**Poprawka na przykład 6**</span><span class="sxs-lookup"><span data-stu-id="b153d-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="b153d-289">Aby usunąć kompletną <xref:System.Threading.Tasks.Task> alokację, można buforować obiekt zadania z wynikiem ukończenia:</span><span class="sxs-lookup"><span data-stu-id="b153d-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="b153d-290">Ten kod zmienia `cachedResult` typ do `Task<SyntaxTree>` i `async` korzysta z funkcji pomocnika, która zawiera oryginalny kod z `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="b153d-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="b153d-291">`GetSyntaxTreeAsync()`teraz używa [operatora łączenia wartości null](../../csharp/language-reference/operators/null-coalescing-operator.md) do zwrócenia `cachedResult` , jeśli nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="b153d-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="b153d-292">Jeśli `cachedResult` ma wartość null `GetSyntaxTreeAsync()` , wywołuje `GetSyntaxTreeUncachedAsync()` i buforuje wynik.</span><span class="sxs-lookup"><span data-stu-id="b153d-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="b153d-293">Zwróć uwagę `GetSyntaxTreeAsync()` , że nie oczekujemy `GetSyntaxTreeUncachedAsync()` , że wywołanie jako kod normalnie będzie się powtarzać.</span><span class="sxs-lookup"><span data-stu-id="b153d-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="b153d-294">Nie przy użyciu oczekiwania oznacza, `GetSyntaxTreeUncachedAsync()` że gdy <xref:System.Threading.Tasks.Task> zwraca swój `GetSyntaxTreeAsync()` <xref:System.Threading.Tasks.Task>obiekt, natychmiast zwraca.</span><span class="sxs-lookup"><span data-stu-id="b153d-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="b153d-295">Teraz buforowany wynik to a <xref:System.Threading.Tasks.Task>, więc nie ma żadnych alokacji, aby zwrócić zbuforowany wynik.</span><span class="sxs-lookup"><span data-stu-id="b153d-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span> 
  
### <a name="additional-considerations"></a><span data-ttu-id="b153d-296">Dodatkowe zagadnienia</span><span class="sxs-lookup"><span data-stu-id="b153d-296">Additional considerations</span></span>  
 <span data-ttu-id="b153d-297">Poniżej przedstawiono kilka dodatkowych kwestii dotyczących potencjalnych problemów z dużymi aplikacjami lub aplikacjami, które przetwarzają wiele danych.</span><span class="sxs-lookup"><span data-stu-id="b153d-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span> 
  
 <span data-ttu-id="b153d-298">**Słownik**</span><span class="sxs-lookup"><span data-stu-id="b153d-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="b153d-299">Słowniki są powszechnie używane w wielu programach, a słowniki są bardzo wygodne i najbardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="b153d-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="b153d-300">Jednak są one często używane w sposób niewłaściwy.</span><span class="sxs-lookup"><span data-stu-id="b153d-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="b153d-301">W programie Visual Studio i w nowych kompilatorach analiza pokazuje, że wiele słowników zawiera pojedynczy element lub był pusty.</span><span class="sxs-lookup"><span data-stu-id="b153d-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="b153d-302">Pusta <xref:System.Collections.Generic.Dictionary%602> ma dziesięć pól i zajmuje 48 bajtów na stercie na komputerze z procesorem x86.</span><span class="sxs-lookup"><span data-stu-id="b153d-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="b153d-303">Słowniki są doskonałe, gdy potrzebne jest mapowanie lub kojarzenie struktury danych z wyszukiwaniem w czasie stałym.</span><span class="sxs-lookup"><span data-stu-id="b153d-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="b153d-304">Niemniej jednak, jeśli masz tylko kilka elementów, możesz użyć słownika.</span><span class="sxs-lookup"><span data-stu-id="b153d-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="b153d-305">Zamiast tego można na przykład zajrzeć przez `List<KeyValuePair\<K,V>>`, tak jak szybko.</span><span class="sxs-lookup"><span data-stu-id="b153d-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="b153d-306">Jeśli używasz słownika tylko do ładowania danych z danymi, a następnie od niego odczytasz (bardzo powszechny wzorzec), za pomocą posortowanej tablicy z wyszukiwaniem N (log (N)) może być niemal równie szybka, w zależności od liczby używanych elementów.</span><span class="sxs-lookup"><span data-stu-id="b153d-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span> 
  
 <span data-ttu-id="b153d-307">**Klasy a struktury**</span><span class="sxs-lookup"><span data-stu-id="b153d-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="b153d-308">W ten sposób klasy i struktury zapewniają klasyczną przestrzeń czasową/kompromis do dostrajania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b153d-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="b153d-309">Klasy składają się z 12 bajtów na komputerze z procesorem x86, nawet jeśli nie mają żadnych pól, ale są niedrogi do obejścia, ponieważ przyjmuje tylko wskaźnik odwołujący się do wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="b153d-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="b153d-310">Struktury nie ponoszą żadnych alokacji sterty, jeśli nie są opakowane, ale w przypadku przekazywania dużych struktur jako argumentów funkcji lub wartości zwracanych przez procesor czas procesora w celu niepodzielnego kopiowania wszystkich elementów członkowskich danych struktur.</span><span class="sxs-lookup"><span data-stu-id="b153d-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="b153d-311">Obejrzyj powtarzające się wywołania właściwości, które zwracają struktury, i Buforuj wartość właściwości w zmiennej lokalnej, aby uniknąć nadmiernego kopiowania danych.</span><span class="sxs-lookup"><span data-stu-id="b153d-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span> 
  
 <span data-ttu-id="b153d-312">**Pamięci podręcznych**</span><span class="sxs-lookup"><span data-stu-id="b153d-312">**Caches**</span></span>  
  
 <span data-ttu-id="b153d-313">Częstą lewę z wydajnością jest buforowanie wyników.</span><span class="sxs-lookup"><span data-stu-id="b153d-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="b153d-314">Jednak pamięć podręczna bez zasad limitu rozmiaru lub usuwania może być przeciekiem pamięci.</span><span class="sxs-lookup"><span data-stu-id="b153d-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="b153d-315">W przypadku przetwarzania dużych ilości danych, jeśli w pamięci podręcznej znajduje się dużo pamięci, można spowodować wyrzucanie elementów bezużytecznych w celu zastąpienia korzyści z buforowanych wyszukiwań.</span><span class="sxs-lookup"><span data-stu-id="b153d-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span> 
  
 <span data-ttu-id="b153d-316">W tym artykule omówiono, jak należy wiedzieć, jak należy pamiętać o problemach z wąskim gardła wydajności, które mogą wpływać na czas odpowiedzi aplikacji, szczególnie w przypadku dużych systemów i systemów, które przetwarzają duże ilości danych.</span><span class="sxs-lookup"><span data-stu-id="b153d-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="b153d-317">Typowe culprits obejmują pakowanie, manipulowanie ciągami, LINQ i lambda, buforowanie w metodach asynchronicznych, buforowanie bez limitu rozmiaru lub zasad usuwania, nieodpowiednie użycie słowników i przekazywanie wokół struktur.</span><span class="sxs-lookup"><span data-stu-id="b153d-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="b153d-318">Weź pod uwagę cztery fakty dotyczące dostrajania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b153d-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="b153d-319">Nie przeprowadzaj przedwcześnie optymalizacji — Zwiększ produktywność i Dostosuj swoją aplikację w przypadku problemów.</span><span class="sxs-lookup"><span data-stu-id="b153d-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span> 
  
- <span data-ttu-id="b153d-320">Profile nie znajdują się — nastąpi odpuszczenie, że nie są mierzone pomiary.</span><span class="sxs-lookup"><span data-stu-id="b153d-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span> 
  
- <span data-ttu-id="b153d-321">Dobre narzędzia sprawiają, że wszystkie różnice — Pobieranie narzędzia PerfView i wypróbowanie.</span><span class="sxs-lookup"><span data-stu-id="b153d-321">Good tools make all the difference – download PerfView and try it out.</span></span> 
  
- <span data-ttu-id="b153d-322">Wszystkie przydziały — w przypadku, gdy zespół platform kompilator poświęca większość czasu na zwiększenie wydajności nowych kompilatorów.</span><span class="sxs-lookup"><span data-stu-id="b153d-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="b153d-323">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b153d-323">See also</span></span>

- [<span data-ttu-id="b153d-324">Wideo przedstawiające prezentację tego tematu</span><span class="sxs-lookup"><span data-stu-id="b153d-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="b153d-325">Profilowanie wydajności — przewodnik dla początkujących</span><span class="sxs-lookup"><span data-stu-id="b153d-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="b153d-326">Wydajność</span><span class="sxs-lookup"><span data-stu-id="b153d-326">Performance</span></span>](index.md)
- <span data-ttu-id="b153d-327">[Porady dotyczące wydajności .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="b153d-327">[.NET Performance Tips](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span></span>
- [<span data-ttu-id="b153d-328">Samouczki narzędzia PerfView kanału 9</span><span class="sxs-lookup"><span data-stu-id="b153d-328">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="b153d-329">Zestaw SDK .NET Compiler Platform</span><span class="sxs-lookup"><span data-stu-id="b153d-329">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="b153d-330">repozytorium dotnet/Roslyn w witrynie GitHub</span><span class="sxs-lookup"><span data-stu-id="b153d-330">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
