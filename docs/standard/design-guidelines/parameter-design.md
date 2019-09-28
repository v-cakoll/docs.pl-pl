---
title: Projekt parametrów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: KrzysztofCwalina
ms.openlocfilehash: 28b00f5911bb47536ec44b96f284e47b6c671149
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353742"
---
# <a name="parameter-design"></a><span data-ttu-id="75e02-102">Projekt parametrów</span><span class="sxs-lookup"><span data-stu-id="75e02-102">Parameter Design</span></span>
<span data-ttu-id="75e02-103">Ta sekcja zawiera szczegółowe wskazówki dotyczące projektowania parametrów, w tym sekcje z instrukcjami dotyczącymi sprawdzania argumentów.</span><span class="sxs-lookup"><span data-stu-id="75e02-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="75e02-104">Ponadto należy zapoznać się z wytycznymi opisanymi w temacie [Parametry nazewnictwa](../../../docs/standard/design-guidelines/naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="75e02-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="75e02-105">**✓ DO** używany najmniej pochodnej typ parametru, który udostępnia funkcje wymagane przez element członkowski.</span><span class="sxs-lookup"><span data-stu-id="75e02-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="75e02-106">Załóżmy na przykład, że chcesz zaprojektować metodę, która wylicza kolekcję i drukuje każdy element do konsoli.</span><span class="sxs-lookup"><span data-stu-id="75e02-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="75e02-107">Taka metoda powinna przyjmować <xref:System.Collections.IEnumerable> jako parametr, a nie <xref:System.Collections.ArrayList> lub <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="75e02-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="75e02-108">**X DO NOT** parametry zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="75e02-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="75e02-109">Jeśli w przyszłych wersjach jest wymaganych więcej danych wejściowych, można dodać nowe Przeciążenie.</span><span class="sxs-lookup"><span data-stu-id="75e02-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="75e02-110">**X DO NOT** zostały publicznie udostępnione metod, które przyjmują wskaźników, tablic wskaźników lub wielowymiarowych tablic jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="75e02-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="75e02-111">Wskaźniki i tablice wielowymiarowe są stosunkowo trudne do użycia.</span><span class="sxs-lookup"><span data-stu-id="75e02-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="75e02-112">W prawie wszystkich przypadkach interfejsy API można przeprojektować, aby uniknąć wykonywania tych typów jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="75e02-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="75e02-113">**✓ DO** Umieść wszystkie `out` po całej przez wartości parametrów i `ref` parametrów (z wyłączeniem tablice parametrów), nawet jeśli powoduje niespójność w parametrze kolejności między przeciążenia (zobacz [elementu członkowskiego Przeciążanie](../../../docs/standard/design-guidelines/member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="75e02-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="75e02-114">Parametry `out` mogą być widoczne jako dodatkowe zwracane wartości i zgrupowanie ich razem sprawia, że podpis metody jest łatwiejszy do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="75e02-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="75e02-115">**✓ DO** zachować spójność nazw parametrów, gdy zastępowanie elementów członkowskich lub wykonania członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="75e02-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="75e02-116">To lepiej komunikuje się relacją między metodami.</span><span class="sxs-lookup"><span data-stu-id="75e02-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="75e02-117">Wybór między parametrami enum i Boolean</span><span class="sxs-lookup"><span data-stu-id="75e02-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="75e02-118">**✓ DO** Użyj wyliczenia, jeśli element członkowski w przeciwnym razie byłyby dwóch lub więcej parametrów Boolean.</span><span class="sxs-lookup"><span data-stu-id="75e02-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="75e02-119">**X DO NOT** Użyj wartości logiczne, jeśli nie masz pewności absolutnie nigdy nie będą potrzeba więcej niż dwóch wartości.</span><span class="sxs-lookup"><span data-stu-id="75e02-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="75e02-120">Wyliczenia dają miejsce na przyszłe Dodawanie wartości, ale należy zwrócić uwagę na wszystkie implikacje dodawania wartości do typów wyliczeniowych, które są opisane w [projekcie wyliczenia](../../../docs/standard/design-guidelines/enum.md).</span><span class="sxs-lookup"><span data-stu-id="75e02-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="75e02-121">**✓ CONSIDER** przy użyciu wartości logiczne są naprawdę dwustanowy wartości, które są używane do zainicjowania właściwości logicznych parametrów konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75e02-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="75e02-122">Sprawdzanie poprawności argumentów</span><span class="sxs-lookup"><span data-stu-id="75e02-122">Validating Arguments</span></span>  
 <span data-ttu-id="75e02-123">**✓ DO** Waliduj Argumenty przekazane do publicznych, chronionych lub jawnie implementowane elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="75e02-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="75e02-124">Zgłoś <xref:System.ArgumentException?displayProperty=nameWithType> lub jedną z jej podklas, jeśli sprawdzanie poprawności zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="75e02-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="75e02-125">Należy zauważyć, że rzeczywista weryfikacja nie musi występować w publicznej lub chronionej składowej.</span><span class="sxs-lookup"><span data-stu-id="75e02-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="75e02-126">Może się to zdarzyć na niższym poziomie w pewnej prywatnej lub wewnętrznej procedurze.</span><span class="sxs-lookup"><span data-stu-id="75e02-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="75e02-127">Głównym punktem jest to, że cały obszar powierzchni, który jest widoczny dla użytkowników końcowych, sprawdza argumenty.</span><span class="sxs-lookup"><span data-stu-id="75e02-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="75e02-128">**✓ DO** throw <xref:System.ArgumentNullException> Jeśli argument o wartości null została przekazana i element członkowski nie obsługuje wartości null argumentów.</span><span class="sxs-lookup"><span data-stu-id="75e02-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="75e02-129">**✓ DO** sprawdza poprawność parametrów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="75e02-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="75e02-130">Nie należy przyjmować argumentów wyliczenia w zakresie zdefiniowanym przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="75e02-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="75e02-131">Środowisko CLR umożliwia rzutowanie dowolnej wartości całkowitej na wartość enum, nawet jeśli wartość nie jest zdefiniowana w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="75e02-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="75e02-132">**X DO NOT** użyj <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> dla wyliczenia zakresu kontroli.</span><span class="sxs-lookup"><span data-stu-id="75e02-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="75e02-133">**✓ DO** należy pamiętać, że argumenty modyfikowalną mogła ulec zmianie po ich została sprawdzona.</span><span class="sxs-lookup"><span data-stu-id="75e02-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="75e02-134">Jeśli składowa jest wrażliwa na zabezpieczenia, zachęca się do tworzenia kopii, a następnie weryfikacji i przetwarzania argumentu.</span><span class="sxs-lookup"><span data-stu-id="75e02-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="75e02-135">Przekazywanie parametru</span><span class="sxs-lookup"><span data-stu-id="75e02-135">Parameter Passing</span></span>  
 <span data-ttu-id="75e02-136">Z perspektywy projektanta struktury istnieją trzy główne grupy parametrów: według wartości parametrów, parametrów `ref` i parametrów `out`.</span><span class="sxs-lookup"><span data-stu-id="75e02-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="75e02-137">Gdy argument jest przenoszona przez parametr przez wartość, element członkowski otrzymuje kopię rzeczywistego argumentu przekazywane.</span><span class="sxs-lookup"><span data-stu-id="75e02-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="75e02-138">Jeśli argument jest typem wartości, kopia argumentu jest umieszczana na stosie.</span><span class="sxs-lookup"><span data-stu-id="75e02-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="75e02-139">Jeśli argument jest typem referencyjnym, kopia odwołania jest umieszczana na stosie.</span><span class="sxs-lookup"><span data-stu-id="75e02-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="75e02-140">Najpopularniejsze języki CLR, takie jak C#VB.NET, i C++domyślne do przekazywania parametrów według wartości.</span><span class="sxs-lookup"><span data-stu-id="75e02-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="75e02-141">Gdy argument jest przenoszona przez @no__t parametru, element członkowski otrzymuje odwołanie do rzeczywistego argumentu przekazywane.</span><span class="sxs-lookup"><span data-stu-id="75e02-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="75e02-142">Jeśli argument jest typem wartości, odwołanie do argumentu jest umieszczane na stosie.</span><span class="sxs-lookup"><span data-stu-id="75e02-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="75e02-143">Jeśli argument jest typem referencyjnym, odwołanie do odwołania jest umieszczane na stosie.</span><span class="sxs-lookup"><span data-stu-id="75e02-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="75e02-144">parametrów `Ref` można użyć, aby zezwolić elementowi członkowskiemu na modyfikowanie argumentów przekazaną przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="75e02-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="75e02-145">parametry `Out` są podobne do parametrów `ref`, z niewielkimi różnicami.</span><span class="sxs-lookup"><span data-stu-id="75e02-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="75e02-146">Parametr jest początkowo uznawany za nieprzypisany i nie może zostać odczytany w treści elementu członkowskiego przed przypisaniem pewnej wartości.</span><span class="sxs-lookup"><span data-stu-id="75e02-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="75e02-147">Ponadto parametr musi mieć przypisaną pewną wartość przed zwróceniem elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="75e02-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="75e02-148">**X AVOID** przy użyciu `out` lub `ref` parametrów.</span><span class="sxs-lookup"><span data-stu-id="75e02-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="75e02-149">Użycie parametrów `out` lub `ref` wymaga środowiska ze wskaźnikami, zrozumienie, jak typy wartości i typy odwołań różnią się i obsługują metody z wieloma zwracanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="75e02-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="75e02-150">Ponadto różnice między `out` i `ref` parametrów nie są szeroko zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="75e02-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="75e02-151">Architekty architektury przeznaczone dla ogólnych odbiorców nie powinny oczekiwać, aby użytkownicy korzystali z parametrów `out` lub `ref`.</span><span class="sxs-lookup"><span data-stu-id="75e02-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="75e02-152">**X DO NOT** przekazuj typów referencyjnych przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="75e02-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="75e02-153">Istnieją pewne ograniczone wyjątki dla reguły, takie jak metoda, która może służyć do wymiany odwołań.</span><span class="sxs-lookup"><span data-stu-id="75e02-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="75e02-154">Elementy członkowskie ze zmienną liczbą parametrów</span><span class="sxs-lookup"><span data-stu-id="75e02-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="75e02-155">Elementy członkowskie, które mogą przyjmować zmienną liczbę argumentów, są wyrażane przez podanie parametru array.</span><span class="sxs-lookup"><span data-stu-id="75e02-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="75e02-156">Na przykład <xref:System.String> zapewnia następującą metodę:</span><span class="sxs-lookup"><span data-stu-id="75e02-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```csharp  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="75e02-157">Użytkownik może następnie wywołać metodę <xref:System.String.Format%2A?displayProperty=nameWithType> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="75e02-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="75e02-158">Dodanie słowa C# kluczowego params do parametru array powoduje zmianę parametru na parametr Array "so-calld" i udostępnia skrót do tworzenia tablicy tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="75e02-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```csharp  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="75e02-159">Dzięki temu użytkownik może wywołać metodę przez przekazanie elementów tablicy bezpośrednio na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="75e02-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="75e02-160">Należy zauważyć, że słowo kluczowe params można dodać tylko do ostatniego parametru na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="75e02-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="75e02-161">**✓ CONSIDER** Dodawanie params — słowo kluczowe do tablicy parametrów, Jeśli przypuszczasz, użytkownikom końcowym przekazać tablice o niewielkiej liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="75e02-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="75e02-162">Jeśli spodziewasz się, że wiele elementów zostanie przekazanych w typowych scenariuszach, użytkownicy prawdopodobnie nie przekazują tych elementów wewnętrznie, a więc słowo kluczowe params nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="75e02-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="75e02-163">**X AVOID** przy użyciu tablic parametrów, jeśli element wywołujący prawie zawsze musi danych wejściowych już w tablicy.</span><span class="sxs-lookup"><span data-stu-id="75e02-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="75e02-164">Na przykład elementy członkowskie z parametrami tablicy bajtów niemal nigdy nie będą wywoływane przez przekazanie pojedynczych bajtów.</span><span class="sxs-lookup"><span data-stu-id="75e02-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="75e02-165">Z tego powodu parametry tablicy bajtowej w .NET Framework nie używają słowa kluczowego params.</span><span class="sxs-lookup"><span data-stu-id="75e02-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="75e02-166">**X DO NOT** Użycie tablic parametrów, jeśli tablica jest modyfikowany przez element członkowski, biorąc parametru params tablicy.</span><span class="sxs-lookup"><span data-stu-id="75e02-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="75e02-167">Ze względu na fakt, że wiele kompilatorów przeniesie argumenty do elementu członkowskiego do tablicy tymczasowej w miejscu wywołania, tablica może być obiektem tymczasowym i w związku z tym wszelkie modyfikacje tablicy zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="75e02-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="75e02-168">**✓ CONSIDER** przy użyciu słowa kluczowego params w prosty przeciążenia, nawet w przypadku bardziej złożonych przeciążenia nie można użyć.</span><span class="sxs-lookup"><span data-stu-id="75e02-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="75e02-169">Zwróć się do siebie, jeśli użytkownicy będą mieli wartość tablica parametrów w jednym przeciążeniu, nawet jeśli nie była we wszystkich przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="75e02-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="75e02-170">**✓ DO** próby kolejność parametrów umożliwiają użyj słowa kluczowego params.</span><span class="sxs-lookup"><span data-stu-id="75e02-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="75e02-171">**✓ CONSIDER** zapewnienie przeciążeń szczególne i ścieżki kodu dla wywołania z niewielką liczbę argumentów w bardzo ważnych wydajności interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="75e02-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="75e02-172">Dzięki temu można uniknąć tworzenia obiektów tablicowych, gdy interfejs API jest wywoływany z niewielką liczbą argumentów.</span><span class="sxs-lookup"><span data-stu-id="75e02-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="75e02-173">Nazwy parametrów należy tworzyć za pomocą pojedynczej formy parametru array i dodawania sufiksu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="75e02-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="75e02-174">Tę czynność należy wykonać tylko wtedy, gdy w przypadku przechodzenia do specjalnego przypadku należy utworzyć tablicę i wywołać bardziej ogólną metodę.</span><span class="sxs-lookup"><span data-stu-id="75e02-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="75e02-175">**✓ DO** należy pamiętać, że null można przekazany jako argument tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="75e02-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="75e02-176">Przed przetworzeniem należy sprawdzić, czy tablica nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="75e02-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="75e02-177">**X DO NOT** użyj `varargs` metod, znanej także jako wielokropka.</span><span class="sxs-lookup"><span data-stu-id="75e02-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="75e02-178">Niektóre języki CLR, takie jak C++, obsługują alternatywną Konwencję do przekazywania list parametrów zmiennych o nazwie `varargs` metod.</span><span class="sxs-lookup"><span data-stu-id="75e02-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="75e02-179">Konwencji nie należy używać w strukturach, ponieważ nie jest ona zgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="75e02-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="75e02-180">Parametry wskaźnika</span><span class="sxs-lookup"><span data-stu-id="75e02-180">Pointer Parameters</span></span>  
 <span data-ttu-id="75e02-181">Ogólnie rzecz biorąc wskaźniki nie powinny znajdować się w obszarze publicznej powierzchni dobrze zaprojektowanej struktury kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="75e02-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="75e02-182">W większości przypadków wskaźniki powinny być hermetyzowane.</span><span class="sxs-lookup"><span data-stu-id="75e02-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="75e02-183">Jednak w niektórych przypadkach wskaźniki są wymagane ze względu na współdziałanie, a w takich przypadkach są odpowiednie wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="75e02-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="75e02-184">**✓ DO** alternatywą dla żadnego członka, który przyjmuje argument wskaźnika, ponieważ wskaźniki nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="75e02-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="75e02-185">**X AVOID** ten argument kosztowne sprawdzanie argumentów wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="75e02-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="75e02-186">**✓ DO** zgodne z konwencjami typowe powiązane wskaźnika podczas projektowania elementy członkowskie ze wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="75e02-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="75e02-187">Na przykład nie ma potrzeby przekazywania indeksu początkowego, ponieważ można użyć prostej arytmetycznej wskaźnika, aby osiągnąć ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="75e02-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="75e02-188">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="75e02-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="75e02-189">*Reprinted przez uprawnienie Pearson Education, Inc. od [Framework — wytyczne dotyczące projektowania: Konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, druga wersja @ no__t-0 przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="75e02-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e02-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75e02-190">See also</span></span>

- [<span data-ttu-id="75e02-191">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="75e02-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="75e02-192">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="75e02-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
