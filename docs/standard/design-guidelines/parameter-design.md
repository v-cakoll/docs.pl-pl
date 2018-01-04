---
title: Parametr projektu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f95301bab57e8bdb6b22c54140a4c02ed208b8d3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="parameter-design"></a><span data-ttu-id="f94be-102">Parametr projektu</span><span class="sxs-lookup"><span data-stu-id="f94be-102">Parameter Design</span></span>
<span data-ttu-id="f94be-103">Ta sekcja zawiera ogólnych wytycznych w projekcie parametru, w tym sekcje z wytycznymi dotyczącymi sprawdzanie argumentów.</span><span class="sxs-lookup"><span data-stu-id="f94be-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="f94be-104">Ponadto należy zapoznać się z wytycznymi opisanego w [nazw parametrów](../../../docs/standard/design-guidelines/naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f94be-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="f94be-105">**CZY ✓** używany najmniej pochodnej typ parametru, który udostępnia funkcje wymagane przez element członkowski.</span><span class="sxs-lookup"><span data-stu-id="f94be-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="f94be-106">Na przykład załóżmy, że chcesz projektowania metodę, która wylicza kolekcji i drukuje każdego elementu w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f94be-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="f94be-107">Taka metoda powinno zająć <xref:System.Collections.IEnumerable> jako parametr, nie <xref:System.Collections.ArrayList> lub <xref:System.Collections.IList>, np.</span><span class="sxs-lookup"><span data-stu-id="f94be-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="f94be-108">**X nie** parametry zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="f94be-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="f94be-109">Jeśli wymagane jest więcej danych wejściowych do elementu członkowskiego w niektórych przyszłych wersji, można dodać nowego przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="f94be-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="f94be-110">**X nie** zostały publicznie udostępnione metod, które przyjmują wskaźników, tablic wskaźników lub wielowymiarowych tablic jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="f94be-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="f94be-111">Wskaźników oraz tablic wielowymiarowych są stosunkowo trudny do wykorzystania poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f94be-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="f94be-112">W większości przypadków interfejsy API można przeprojektowany tak, aby uniknąć wykonywania tych typów jako parametry.</span><span class="sxs-lookup"><span data-stu-id="f94be-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="f94be-113">**CZY ✓** Umieść wszystkie `out` po całej przez wartości parametrów i `ref` parametrów (z wyłączeniem tablice parametrów), nawet jeśli powoduje niespójność w parametrze kolejności między przeciążenia (zobacz [elementu członkowskiego Przeciążanie](../../../docs/standard/design-guidelines/member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="f94be-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="f94be-114">`out` Parametry są widoczne jako wartości zwracane bardzo i zgrupowanie ułatwia zrozumienie podpis metody.</span><span class="sxs-lookup"><span data-stu-id="f94be-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="f94be-115">**CZY ✓** zachować spójność nazw parametrów, gdy zastępowanie elementów członkowskich lub wykonania członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f94be-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="f94be-116">To lepiej komunikuje się relacji między metodami.</span><span class="sxs-lookup"><span data-stu-id="f94be-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="f94be-117">Wybór między logiczna parametry i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f94be-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="f94be-118">**CZY ✓** Użyj wyliczenia, jeśli element członkowski w przeciwnym razie byłyby dwóch lub więcej parametrów Boolean.</span><span class="sxs-lookup"><span data-stu-id="f94be-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="f94be-119">**X nie** Użyj wartości logiczne, jeśli nie masz pewności absolutnie nigdy nie będą potrzeba więcej niż dwóch wartości.</span><span class="sxs-lookup"><span data-stu-id="f94be-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="f94be-120">Typy wyliczeniowe zapewniają niektóre miejsca dla przyszłych dodanie wartości, ale należy zwrócić uwagę wszystkie efekty dodawania wartości do wyliczenia, które zostały opisane w [projektu wyliczenia](../../../docs/standard/design-guidelines/enum.md).</span><span class="sxs-lookup"><span data-stu-id="f94be-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="f94be-121">**ROZWAŻ ✓** przy użyciu wartości logiczne są naprawdę dwustanowy wartości, które są używane do zainicjowania właściwości logicznych parametrów konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f94be-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="f94be-122">Sprawdzanie poprawności argumentów</span><span class="sxs-lookup"><span data-stu-id="f94be-122">Validating Arguments</span></span>  
 <span data-ttu-id="f94be-123">**CZY ✓** Waliduj Argumenty przekazane do publicznych, chronionych lub jawnie implementowane elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="f94be-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="f94be-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, lub jeden z jego podklas, w przypadku niepowodzenia weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="f94be-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="f94be-125">Należy pamiętać, że rzeczywista weryfikacja nie musi być w public lub protected członkowski.</span><span class="sxs-lookup"><span data-stu-id="f94be-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="f94be-126">Może się zdarzyć na niższym poziomie w niektórych procedury prywatny lub wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="f94be-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="f94be-127">Główny punkt znajduje się sprawdza, czy cały powierzchni, która jest widoczna dla użytkowników końcowych argumentów.</span><span class="sxs-lookup"><span data-stu-id="f94be-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="f94be-128">**CZY ✓** throw <xref:System.ArgumentNullException> Jeśli argument o wartości null została przekazana i element członkowski nie obsługuje wartości null argumentów.</span><span class="sxs-lookup"><span data-stu-id="f94be-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="f94be-129">**CZY ✓** sprawdza poprawność parametrów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f94be-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="f94be-130">Nie przyjęto założenie, że będzie argumenty wyliczenia w zakresie zdefiniowanych przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="f94be-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="f94be-131">Środowisko CLR umożliwia rzutowania dowolną liczbą całkowitą w wartości wyliczenia, nawet jeśli wartość nie jest zdefiniowany w elemencie enum.</span><span class="sxs-lookup"><span data-stu-id="f94be-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="f94be-132">**X nie** użyj <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> dla wyliczenia zakresu kontroli.</span><span class="sxs-lookup"><span data-stu-id="f94be-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="f94be-133">**CZY ✓** należy pamiętać, że argumenty modyfikowalną mogła ulec zmianie po ich została sprawdzona.</span><span class="sxs-lookup"><span data-stu-id="f94be-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="f94be-134">Jeśli element członkowski jest bezpieczeństwa poufnych, zachęca się do skopiowania, a następnie sprawdź poprawność i przetwarzać argumentu.</span><span class="sxs-lookup"><span data-stu-id="f94be-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="f94be-135">Przekazywanie parametru</span><span class="sxs-lookup"><span data-stu-id="f94be-135">Parameter Passing</span></span>  
 <span data-ttu-id="f94be-136">Z punktu widzenia projektanta framework, istnieją trzy główne grupy parametrów: parametry, przez wartość `ref` parametry, i `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="f94be-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="f94be-137">Gdy argument jest przekazywany za pomocą parametru-wartość, element członkowski wysyłana kopia rzeczywisty argument przekazany.</span><span class="sxs-lookup"><span data-stu-id="f94be-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="f94be-138">Jeśli argument ma typ wartości, kopię argumentu jest umieszczany na stosie.</span><span class="sxs-lookup"><span data-stu-id="f94be-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="f94be-139">Jeśli argument ma typ referencyjny, kopię odwołanie jest umieszczany na stosie.</span><span class="sxs-lookup"><span data-stu-id="f94be-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="f94be-140">Najbardziej popularnych języków CLR, takich jak C#, VB.NET i C++, domyślnie przekazywanie parametrów przez wartość.</span><span class="sxs-lookup"><span data-stu-id="f94be-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="f94be-141">Gdy argument jest przekazywany za pośrednictwem `ref` parametru odbiera element członkowski odwołania do rzeczywistego przekazany argument.</span><span class="sxs-lookup"><span data-stu-id="f94be-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="f94be-142">Jeśli argument ma typ wartości, odwołanie do argumentu jest umieszczany na stosie.</span><span class="sxs-lookup"><span data-stu-id="f94be-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="f94be-143">Jeśli argument ma typ referencyjny, odwołanie do odwołania jest umieszczany na stosie.</span><span class="sxs-lookup"><span data-stu-id="f94be-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="f94be-144">`Ref`Aby umożliwić elementu członkowskiego do argumenty przekazany przez wywołującego można użyć parametrów.</span><span class="sxs-lookup"><span data-stu-id="f94be-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="f94be-145">`Out`Parametry są podobne do `ref` parametrów, z niektórych niewielkie różnice.</span><span class="sxs-lookup"><span data-stu-id="f94be-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="f94be-146">Parametr uważa się początkowo nieprzypisane i nie można odczytać treści elementu członkowskiego, przed przypisaniem niektóre wartości.</span><span class="sxs-lookup"><span data-stu-id="f94be-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="f94be-147">Ponadto parametr musi zostać przypisany niektóre wartości, zanim zwraca element członkowski.</span><span class="sxs-lookup"><span data-stu-id="f94be-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="f94be-148">**X należy UNIKAĆ** przy użyciu `out` lub `ref` parametrów.</span><span class="sxs-lookup"><span data-stu-id="f94be-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="f94be-149">Przy użyciu `out` lub `ref` środowisko z wskaźników, zrozumienie, jak są różne typy wartości i typy referencyjne i obsługi metod zawierających wiele wartości zwrotnych wymaga parametrów.</span><span class="sxs-lookup"><span data-stu-id="f94be-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="f94be-150">Ponadto to różnica między `out` i `ref` parametry powszechnie jest niezrozumiały.</span><span class="sxs-lookup"><span data-stu-id="f94be-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="f94be-151">Architektów Framework projektowania dla wszystkich użytkowników nie oczekiwać użytkownikom pracy wzorca z `out` lub `ref` parametrów.</span><span class="sxs-lookup"><span data-stu-id="f94be-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="f94be-152">**X nie** przekazuj typów referencyjnych przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f94be-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="f94be-153">Brak niektórych ograniczone wyjątki w regule, na przykład metodę, która może służyć do wymiany odwołań.</span><span class="sxs-lookup"><span data-stu-id="f94be-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="f94be-154">Elementy członkowskie o zmiennej liczbie parametrów</span><span class="sxs-lookup"><span data-stu-id="f94be-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="f94be-155">Elementy członkowskie, które można wykonać zmienna liczba argumentów są wyrażane podając parametr tablicy.</span><span class="sxs-lookup"><span data-stu-id="f94be-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="f94be-156">Na przykład <xref:System.String> udostępnia następujące metody:</span><span class="sxs-lookup"><span data-stu-id="f94be-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="f94be-157">Użytkownik może wywoływać <xref:System.String.Format%2A?displayProperty=nameWithType> metody, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f94be-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="f94be-158">Dodawanie słowa kluczowego params C# do parametru tablicy zmiany parametru parametru params tak zwane tablicy i zapewnia skrót do utworzenia tablicy tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="f94be-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="f94be-159">W ten sposób umożliwia użytkownikowi Wywołaj metodę przez przekazanie elementów tablicy bezpośrednio na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="f94be-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="f94be-160">Należy pamiętać, że słowa kluczowego params można dodać tylko do ostatniego parametru na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="f94be-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="f94be-161">**ROZWAŻ ✓** Dodawanie params — słowo kluczowe do tablicy parametrów, Jeśli przypuszczasz, użytkownikom końcowym przekazać tablice o niewielkiej liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="f94be-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="f94be-162">Jeśli oczekuje się, że wiele elementów zostaną przekazane wspólnych scenariuszy, użytkownicy mimo to prawdopodobnie nie przejdą wbudowanego tych elementów, a więc params — słowo kluczowe nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="f94be-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="f94be-163">**X należy UNIKAĆ** przy użyciu tablic parametrów, jeśli element wywołujący prawie zawsze musi danych wejściowych już w tablicy.</span><span class="sxs-lookup"><span data-stu-id="f94be-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="f94be-164">Na przykład elementy członkowskie z parametrami tablicy bajtów prawie nigdy nie będzie można wywołać przez przekazanie poszczególnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="f94be-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="f94be-165">Z tego powodu parametrów tablicy bajtów w programie .NET Framework nie należy używać słowa kluczowego params.</span><span class="sxs-lookup"><span data-stu-id="f94be-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="f94be-166">**X nie** Użycie tablic parametrów, jeśli tablica jest modyfikowany przez element członkowski, biorąc parametru params tablicy.</span><span class="sxs-lookup"><span data-stu-id="f94be-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="f94be-167">Ze względu na fakt, że wiele kompilatorów Włącz argumenty do elementu członkowskiego do tablicy w witrynie wywołanie tablicy może być obiektem tymczasowym, a zatem wszelkie modyfikacje tablicy zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="f94be-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="f94be-168">**ROZWAŻ ✓** przy użyciu słowa kluczowego params w prosty przeciążenia, nawet w przypadku bardziej złożonych przeciążenia nie można użyć.</span><span class="sxs-lookup"><span data-stu-id="f94be-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="f94be-169">Zadaj sobie, jeśli użytkownicy będą wartości o tablicy parametrów w przeciążeniami, nawet jeśli nie był w wszystkie przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="f94be-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="f94be-170">**CZY ✓** próby kolejność parametrów umożliwiają użyj słowa kluczowego params.</span><span class="sxs-lookup"><span data-stu-id="f94be-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="f94be-171">**ROZWAŻ ✓** zapewnienie przeciążeń szczególne i ścieżki kodu dla wywołania z niewielką liczbę argumentów w bardzo ważnych wydajności interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="f94be-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="f94be-172">Dzięki temu można uniknąć tworzenia tablicy obiektów po wywołaniu interfejsu API z mniejszą liczbą argumentów.</span><span class="sxs-lookup"><span data-stu-id="f94be-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="f94be-173">Formularz nazwy parametrów przez pobranie pojedynczej formę parametr tablicy i dodanie sufiksu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="f94be-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="f94be-174">Tylko należy to zrobić, jeśli ma specjalne przypadku ścieżkę całego kodu, nie wystarczy utworzyć tablicy i wywołaj metodę bardziej ogólne.</span><span class="sxs-lookup"><span data-stu-id="f94be-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="f94be-175">**CZY ✓** należy pamiętać, że null można przekazany jako argument tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="f94be-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="f94be-176">Należy sprawdzić, czy tablica nie jest pusta, przed rozpoczęciem przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f94be-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="f94be-177">**X nie** użyj `varargs` metod, znanej także jako wielokropka.</span><span class="sxs-lookup"><span data-stu-id="f94be-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="f94be-178">Niektórych języków CLR, takich jak C++, obsługa alternatywnych Konwencji przekazywanie listy parametrów zmiennej o nazwie `varargs` metody.</span><span class="sxs-lookup"><span data-stu-id="f94be-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="f94be-179">Konwencji nie stosuje się w struktur, ponieważ nie jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="f94be-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="f94be-180">Parametry wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f94be-180">Pointer Parameters</span></span>  
 <span data-ttu-id="f94be-181">Ogólnie rzecz biorąc wskaźniki nie mogą występować w publicznej powierzchni framework dobrze zaprojektowanego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f94be-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="f94be-182">W większości przypadków należy hermetyzowany wskaźników.</span><span class="sxs-lookup"><span data-stu-id="f94be-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="f94be-183">Jednak w niektórych przypadkach wskaźniki są wymagane współdziałanie ze względu na i przy użyciu wskaźniki w takich przypadkach jest.</span><span class="sxs-lookup"><span data-stu-id="f94be-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="f94be-184">**CZY ✓** alternatywą dla żadnego członka, który przyjmuje argument wskaźnika, ponieważ wskaźniki nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="f94be-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="f94be-185">**X należy UNIKAĆ** ten argument kosztowne sprawdzanie argumentów wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f94be-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="f94be-186">**CZY ✓** zgodne z konwencjami typowe powiązane wskaźnika podczas projektowania elementy członkowskie ze wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="f94be-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="f94be-187">Ponieważ arytmetyka wskaźnika prostego mogą zostać użyte do wykonania takiego samego wyniku istnieje na przykład, nie trzeba przekazać indeks początkowy.</span><span class="sxs-lookup"><span data-stu-id="f94be-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="f94be-188">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="f94be-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f94be-189">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="f94be-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94be-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f94be-190">See Also</span></span>  
 [<span data-ttu-id="f94be-191">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="f94be-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="f94be-192">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="f94be-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
