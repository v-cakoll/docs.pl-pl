---
title: 'Atrybuty zastrzeżone języka C#: nullowa analiza statyczna'
ms.date: 04/14/2020
description: Te atrybuty są interpretowane przez kompilator, aby zapewnić lepszą analizę statyczną dla typów odwołań nullable i non-null.
ms.openlocfilehash: 0315d78db7517541efe578d8675c0f2fe45f5aea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389864"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a><span data-ttu-id="8afa2-103">Atrybuty zastrzeżone przyczyniają się do analizy statycznej stanu zerowego kompilatora</span><span class="sxs-lookup"><span data-stu-id="8afa2-103">Reserved attributes contribute to the compiler's null state static analysis</span></span>

<span data-ttu-id="8afa2-104">W kontekście nullable kompilator wykonuje statyczną analizę kodu w celu określenia stanu null wszystkich zmiennych typu odwołania:</span><span class="sxs-lookup"><span data-stu-id="8afa2-104">In a nullable context, the compiler performs static analysis of code to determine the null state of all reference type variables:</span></span>

- <span data-ttu-id="8afa2-105">*nie null*: Analiza statyczna ustaliła, że zmienna jest przypisana do wartości innej niż null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-105">*not null*: Static analysis determined that the variable is assigned to a non-null value.</span></span>
- <span data-ttu-id="8afa2-106">*może null*: Analiza statyczna nie może ustalić, że zmiennej jest przypisana wartość niekrajowa.</span><span class="sxs-lookup"><span data-stu-id="8afa2-106">*maybe null*: Static analysis cannot determine that a variable is assigned a non-null value.</span></span>

<span data-ttu-id="8afa2-107">Można zastosować szereg atrybutów, które dostarczają informacji do kompilatora o semantyki interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="8afa2-107">You can apply a number of attributes that provide information to the compiler about the semantics of your APIs.</span></span> <span data-ttu-id="8afa2-108">Te informacje pomagają kompilatorowi wykonać analizę statyczną i określić, kiedy zmienna nie jest null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-108">That information helps the compiler perform static analysis and determine when a variable is not null.</span></span> <span data-ttu-id="8afa2-109">Ten artykuł zawiera krótki opis każdego z tych atrybutów i jak z nich korzystać.</span><span class="sxs-lookup"><span data-stu-id="8afa2-109">This article provides a brief description of each of those attributes and how to use them.</span></span> <span data-ttu-id="8afa2-110">Wszystkie przykłady zakładają C# 8.0 lub nowsze, a kod jest w kontekście nullable.</span><span class="sxs-lookup"><span data-stu-id="8afa2-110">All the examples assume C# 8.0 or newer, and the code is in a nullable context.</span></span>

<span data-ttu-id="8afa2-111">Zacznijmy od znanego przykładu.</span><span class="sxs-lookup"><span data-stu-id="8afa2-111">Let's start with a familiar example.</span></span> <span data-ttu-id="8afa2-112">Wyobraź sobie, że biblioteka ma następujący interfejs API do pobierania ciągu zasobu:</span><span class="sxs-lookup"><span data-stu-id="8afa2-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="8afa2-113">W poprzednim przykładzie `Try*` następuje znane wzorzec w .NET.</span><span class="sxs-lookup"><span data-stu-id="8afa2-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="8afa2-114">Istnieją dwa argumenty odwołania dla `key` tego `message` interfejsu API: i parametr.</span><span class="sxs-lookup"><span data-stu-id="8afa2-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="8afa2-115">Ten interfejs API ma następujące reguły odnoszące się do nieważności tych argumentów:</span><span class="sxs-lookup"><span data-stu-id="8afa2-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="8afa2-116">Dzwoniący nie powinni `null` przechodzić `key`jako argument dla .</span><span class="sxs-lookup"><span data-stu-id="8afa2-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="8afa2-117">Osoby dzwoniące mogą przekazać `null` zmienną, `message`której wartość jest argumentem dla .</span><span class="sxs-lookup"><span data-stu-id="8afa2-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="8afa2-118">Jeśli `TryGetMessage` metoda `true`zwraca , `message` wartość nie jest null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="8afa2-119">Jeśli zwracana `false,` wartość jest `message` wartością (a jej stan zerowy) jest null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="8afa2-120">Reguła `key` dla może być wyrażona `key` przez typ zmiennej: powinien być typem odwołania nienastępującym wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-120">The rule for `key` can be expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="8afa2-121">Parametr `message` jest bardziej złożony.</span><span class="sxs-lookup"><span data-stu-id="8afa2-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="8afa2-122">Pozwala `null` jako argument, ale gwarantuje, że `out` na sukces, że argument nie jest null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="8afa2-123">W przypadku tych scenariuszy potrzebujesz bogatszego słownictwa, aby opisać oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8afa2-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="8afa2-124">Dodano kilka atrybutów, aby wyrazić dodatkowe informacje o stanie null zmiennych.</span><span class="sxs-lookup"><span data-stu-id="8afa2-124">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="8afa2-125">Cały kod, który napisałeś przed C# 8 wprowadzone nullable typy odwołań był *null oblivious*.</span><span class="sxs-lookup"><span data-stu-id="8afa2-125">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="8afa2-126">Oznacza to, że każda zmienna typu odwołania może mieć wartość null, ale nie są wymagane kontrole wartości null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-126">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="8afa2-127">Gdy kod jest *nullable aware*, te reguły zmienić.</span><span class="sxs-lookup"><span data-stu-id="8afa2-127">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="8afa2-128">Typy odwołań `null` nigdy nie powinny być wartością, `null` a typy odwołań do wartości null muszą być sprawdzane przed odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="8afa2-128">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="8afa2-129">Reguły interfejsów API są prawdopodobnie bardziej skomplikowane, `TryGetValue` jak widać w scenariuszu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="8afa2-129">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="8afa2-130">Wiele interfejsów API ma bardziej złożone reguły, gdy zmienne mogą lub nie mogą być `null`.</span><span class="sxs-lookup"><span data-stu-id="8afa2-130">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="8afa2-131">W takich przypadkach do wyrażenia tych reguł użyjesz jednego z następujących atrybutów:</span><span class="sxs-lookup"><span data-stu-id="8afa2-131">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="8afa2-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy nienastępny do wartości null może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="8afa2-133">[NieuprawnionyNull:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Nullable argument wejściowy nigdy nie powinien być null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="8afa2-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana bez wartości null może być wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="8afa2-135">[NotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)Nullable wartość zwracana nigdy nie będzie null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="8afa2-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy nienastępny do wartości `bool` null może mieć wartość null, gdy metoda zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8afa2-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="8afa2-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do null nie będzie `bool` null, gdy metoda zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8afa2-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="8afa2-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Zwracana wartość nie jest zerowa, jeśli argument dla określonego parametru nie jest null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="8afa2-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Metoda nigdy nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="8afa2-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="8afa2-140">Innymi słowy zawsze zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8afa2-140">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="8afa2-141">[DoesNotReturnIf:](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute)Ta metoda nigdy nie `bool` zwraca, jeśli skojarzony parametr ma określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8afa2-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>

<span data-ttu-id="8afa2-142">Powyższe opisy są szybkie odwołanie do tego, co każdy atrybut nie.</span><span class="sxs-lookup"><span data-stu-id="8afa2-142">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="8afa2-143">W każdej poniższej sekcji opisano zachowanie i znaczenie dokładniej.</span><span class="sxs-lookup"><span data-stu-id="8afa2-143">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="8afa2-144">Dodanie tych atrybutów daje kompilatorowi więcej informacji na temat reguł dla interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="8afa2-144">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="8afa2-145">Podczas wywoływania kodu jest kompilowany w kontekście z obsługą nullable włączone, kompilator będzie ostrzegać wywoływaczy, gdy naruszają te reguły.</span><span class="sxs-lookup"><span data-stu-id="8afa2-145">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="8afa2-146">Te atrybuty nie umożliwiają dodatkowych kontroli implementacji.</span><span class="sxs-lookup"><span data-stu-id="8afa2-146">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="8afa2-147">Określ warunki wstępne: `AllowNull` i`DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="8afa2-147">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="8afa2-148">Należy wziąć pod uwagę właściwość odczytu/zapisu, która nigdy nie zwraca, `null` ponieważ ma rozsądną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="8afa2-148">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="8afa2-149">Wywołujący `null` przechodzą do zestawu akcesora podczas ustawiania go do tej wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="8afa2-149">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="8afa2-150">Rozważmy na przykład system obsługi wiadomości, który prosi o nazwę ekranu w pokoju rozmów.</span><span class="sxs-lookup"><span data-stu-id="8afa2-150">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="8afa2-151">Jeśli nie podano, system generuje losową nazwę:</span><span class="sxs-lookup"><span data-stu-id="8afa2-151">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

<span data-ttu-id="8afa2-152">Podczas kompilowania poprzedniego kodu w kontekście nullable nieświadomy, wszystko jest w porządku.</span><span class="sxs-lookup"><span data-stu-id="8afa2-152">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="8afa2-153">Po włączeniu typów odwołań `ScreenName` nullable, właściwość staje się odwołanie nie nullable.</span><span class="sxs-lookup"><span data-stu-id="8afa2-153">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="8afa2-154">To jest poprawne `get` dla akcesora: nigdy nie zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="8afa2-154">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="8afa2-155">Dzwoniący nie muszą sprawdzać zwracane `null`właściwość dla .</span><span class="sxs-lookup"><span data-stu-id="8afa2-155">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="8afa2-156">Ale teraz ustawienie `null` właściwości, aby wygenerować ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="8afa2-156">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="8afa2-157">Aby nadal obsługiwać ten typ kodu, <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> należy dodać atrybut do właściwości, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="8afa2-157">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

<span data-ttu-id="8afa2-158">Może być konieczne `using` dodanie <xref:System.Diagnostics.CodeAnalysis> dyrektywy, aby użyć tego i innych atrybutów omówionych w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="8afa2-158">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="8afa2-159">Atrybut jest stosowany do właściwości, a `set` nie akcesora.</span><span class="sxs-lookup"><span data-stu-id="8afa2-159">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="8afa2-160">Atrybut `AllowNull` określa *warunki wstępne*i ma zastosowanie tylko do danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8afa2-160">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="8afa2-161">Akcesor `get` ma wartość zwracaną, ale nie ma argumentów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8afa2-161">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="8afa2-162">W związku `AllowNull` z tym atrybut dotyczy `set` tylko akcesora.</span><span class="sxs-lookup"><span data-stu-id="8afa2-162">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="8afa2-163">W poprzednim przykładzie pokazano, na co `AllowNull` zwrócić uwagę podczas dodawania atrybutu w argurze:</span><span class="sxs-lookup"><span data-stu-id="8afa2-163">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="8afa2-164">Ogólna umowa dla tej zmiennej jest, że nie powinno być `null`, więc chcesz typu odwołania nie nullable.</span><span class="sxs-lookup"><span data-stu-id="8afa2-164">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="8afa2-165">Istnieją scenariusze dla zmiennej `null`wejściowej, które mają być, choć nie są one najczęściej użycia.</span><span class="sxs-lookup"><span data-stu-id="8afa2-165">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="8afa2-166">Najczęściej ten atrybut jest potrzebny dla właściwości `in`lub `out`, `ref` i argumentów.</span><span class="sxs-lookup"><span data-stu-id="8afa2-166">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="8afa2-167">Atrybut `AllowNull` jest najlepszym wyborem, gdy zmienna jest zazwyczaj nie null, ale należy zezwolić `null` jako warunek wstępny.</span><span class="sxs-lookup"><span data-stu-id="8afa2-167">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="8afa2-168">Kontrast, który ze `DisallowNull`scenariuszami użycia: Ten atrybut służy do określania, że zmienną `null`wejściową typu odwołania z dopuszczalną wartością null nie powinna być .</span><span class="sxs-lookup"><span data-stu-id="8afa2-168">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="8afa2-169">Należy wziąć `null` pod uwagę właściwość, gdzie jest wartością domyślną, ale klienci mogą tylko ustawić ją na wartość nietrwałą.</span><span class="sxs-lookup"><span data-stu-id="8afa2-169">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="8afa2-170">Spójrzmy na poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="8afa2-170">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="8afa2-171">Powyższy kod jest najlepszym sposobem wyrażenia projektu, który `ReviewComment` może być, `null`ale `null`nie można ustawić na .</span><span class="sxs-lookup"><span data-stu-id="8afa2-171">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="8afa2-172">Gdy ten kod jest nullable pamiętać, można wyrazić tę <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>koncepcję jaśniej do rozmówców za pomocą:</span><span class="sxs-lookup"><span data-stu-id="8afa2-172">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="8afa2-173">W kontekście `ReviewComment` `get` możliwego do anulowania akcesor może zwrócić wartość domyślną `null`programu .</span><span class="sxs-lookup"><span data-stu-id="8afa2-173">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="8afa2-174">Kompilator ostrzega, że należy sprawdzić przed dostępem.</span><span class="sxs-lookup"><span data-stu-id="8afa2-174">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="8afa2-175">Co więcej, ostrzega dzwoniących, że nawet `null`jeśli może to być , `null`dzwoniący nie powinni wyraźnie ustawić go na .</span><span class="sxs-lookup"><span data-stu-id="8afa2-175">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="8afa2-176">Atrybut `DisallowNull` określa również *warunek wstępny*, nie wpływa `get` na akcesor.</span><span class="sxs-lookup"><span data-stu-id="8afa2-176">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="8afa2-177">Atrybutu `DisallowNull` należy używać, gdy obserwujesz następujące cechy dotyczące:</span><span class="sxs-lookup"><span data-stu-id="8afa2-177">You use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="8afa2-178">Zmienna może `null` znajdować się w podstawowych scenariuszach, często podczas pierwszego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8afa2-178">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="8afa2-179">Zmienna nie powinna być jawnie ustawiona na `null`.</span><span class="sxs-lookup"><span data-stu-id="8afa2-179">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="8afa2-180">Te sytuacje są powszechne w kodzie, który pierwotnie *null oblivious*.</span><span class="sxs-lookup"><span data-stu-id="8afa2-180">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="8afa2-181">Może się okazać, że właściwości obiektu są ustawione w dwóch różnych operacji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="8afa2-181">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="8afa2-182">Może się okazać, że niektóre właściwości są ustawiane tylko po zakończeniu niektórych prac asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="8afa2-182">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="8afa2-183">`AllowNull` Atrybuty `DisallowNull` i umożliwiają określenie, że warunki wstępne dla zmiennych mogą nie odpowiadać adnotacjami nullable dla tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="8afa2-183">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="8afa2-184">Zapewniają one więcej szczegółów na temat cech interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="8afa2-184">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="8afa2-185">Te dodatkowe informacje pomagają wywołującym poprawnie używać interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="8afa2-185">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="8afa2-186">Pamiętaj, że określono warunki wstępne przy użyciu następujących atrybutów:</span><span class="sxs-lookup"><span data-stu-id="8afa2-186">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="8afa2-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy nienastępny do wartości null może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="8afa2-188">[NieuprawnionyNull:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Nullable argument wejściowy nigdy nie powinien być null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="8afa2-189">Określ warunki `MaybeNull` post: i`NotNull`</span><span class="sxs-lookup"><span data-stu-id="8afa2-189">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="8afa2-190">Załóżmy, że masz metodę z następującym podpisem:</span><span class="sxs-lookup"><span data-stu-id="8afa2-190">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="8afa2-191">Prawdopodobnie napisałeś taką metodę, aby `null` powrócić, gdy poszukiwana nazwa nie została znaleziona.</span><span class="sxs-lookup"><span data-stu-id="8afa2-191">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="8afa2-192">Wyraźnie `null` wskazuje, że rekord nie został znaleziony.</span><span class="sxs-lookup"><span data-stu-id="8afa2-192">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="8afa2-193">W tym przykładzie prawdopodobnie zmienisz typ `Customer` `Customer?`zwracany z na .</span><span class="sxs-lookup"><span data-stu-id="8afa2-193">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="8afa2-194">Deklarowanie wartości zwracanej jako typu odwołania powodującego wartość null określa intencję tego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="8afa2-194">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="8afa2-195">Z przyczyn objętych [definicjami rodzajowymi i niemożnością użycia](../../nullable-attributes.md#generic-definitions-and-nullability) ta technika nie działa z metodami ogólnymi.</span><span class="sxs-lookup"><span data-stu-id="8afa2-195">For reasons covered under [Generic definitions and nullability](../../nullable-attributes.md#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="8afa2-196">Może być metoda rodzajowa, która następuje podobny wzorzec:</span><span class="sxs-lookup"><span data-stu-id="8afa2-196">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="8afa2-197">Nie można określić, że `T?`zwracana jest wartość .</span><span class="sxs-lookup"><span data-stu-id="8afa2-197">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="8afa2-198">Metoda zwraca, `null` gdy nie znaleziono poszukiwanego elementu.</span><span class="sxs-lookup"><span data-stu-id="8afa2-198">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="8afa2-199">Ponieważ nie można zadeklarować typu zwracanego, `T?` należy dodać `MaybeNull` adnotację do zwracania metody:</span><span class="sxs-lookup"><span data-stu-id="8afa2-199">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="8afa2-200">Powyższy kod informuje wywołujących, że umowa implikuje typ nienależyte do null, ale wartość *zwracana może* być rzeczywiście null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-200">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="8afa2-201">Użyj `MaybeNull` atrybutu, gdy interfejs API powinien być typem nienastępnym do wartości null, `null` zazwyczaj parametrem typu ogólnego, ale mogą występować wystąpienia, w których zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="8afa2-201">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="8afa2-202">Można również określić, że `out` wartość `ref` zwracana lub argument lub nie jest null, nawet jeśli typ jest typem odwołania z dopuszczalną wartością null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-202">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="8afa2-203">Należy wziąć pod uwagę metodę, która zapewnia tablicy jest wystarczająco duży, aby pomieścić wiele elementów.</span><span class="sxs-lookup"><span data-stu-id="8afa2-203">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="8afa2-204">Jeśli argument wejściowy nie ma pojemności, procedura będzie przydzielić nową tablicę i skopiować wszystkie istniejące elementy do niego.</span><span class="sxs-lookup"><span data-stu-id="8afa2-204">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="8afa2-205">Jeśli argument input `null`jest , procedura będzie przydzielić nowy magazyn.</span><span class="sxs-lookup"><span data-stu-id="8afa2-205">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="8afa2-206">Jeśli istnieje wystarczająca pojemność, procedura nie robi nic:</span><span class="sxs-lookup"><span data-stu-id="8afa2-206">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="8afa2-207">Tę procedurę można wywołać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8afa2-207">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="8afa2-208">Po włączeniu typów odwołań null, chcesz upewnić się, że poprzedni kod kompiluje się bez ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="8afa2-208">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="8afa2-209">Gdy metoda zwraca, `storage` argument jest gwarantowane nie null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-209">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="8afa2-210">Jednak jest dopuszczalne, `EnsureCapacity` aby wywołać z odwołaniem null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-210">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="8afa2-211">Można wprowadzić `storage` typ odwołania z dopuszczalną `NotNull` wartością null i dodać warunek post do deklaracji parametrów:</span><span class="sxs-lookup"><span data-stu-id="8afa2-211">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

<span data-ttu-id="8afa2-212">Powyższy kod wyraźnie wyraża istniejącą umowę: wywołujący mogą `null` przekazać zmienną z wartością, ale wartość zwracana jest gwarantowana, aby nigdy nie była null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-212">The preceding code expresses the existing contract clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="8afa2-213">Atrybut `NotNull` jest najbardziej przydatne `ref` `out` dla `null` i argumenty, gdzie mogą być przekazywane jako argument, ale ten argument jest gwarantowane nie jest null, gdy zwraca metodę.</span><span class="sxs-lookup"><span data-stu-id="8afa2-213">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="8afa2-214">Bezwarunkowe warunki postwarunkowe można określić przy użyciu następujących atrybutów:</span><span class="sxs-lookup"><span data-stu-id="8afa2-214">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="8afa2-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana bez wartości null może być wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="8afa2-216">[NotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)Nullable wartość zwracana nigdy nie będzie null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="8afa2-217">Określ warunkowe warunki `NotNullWhen` `MaybeNullWhen`post:, , i`NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="8afa2-217">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="8afa2-218">Prawdopodobnie znasz `string` metodę <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8afa2-218">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="8afa2-219">Ta metoda `true` zwraca, gdy argument ma wartość null lub pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="8afa2-219">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="8afa2-220">Jest to forma sprawdzania wartości null: osoby dzwoniące nie muszą sprawdzać wartości `false`null, jeśli metoda zwraca .</span><span class="sxs-lookup"><span data-stu-id="8afa2-220">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="8afa2-221">Aby metoda taka jak ta nullable świadomość, należy ustawić argument do typu `NotNullWhen` odwołania nullable i dodać atrybut:</span><span class="sxs-lookup"><span data-stu-id="8afa2-221">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

<span data-ttu-id="8afa2-222">Informuje kompilator, że każdy kod, `false` w którym jest wartość zwracana, nie musi być sprawdzany z wartością null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-222">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="8afa2-223">Dodanie atrybutu informuje analizę statyczną kompilatora, `IsNullOrEmpty` która wykonuje niezbędne sprawdzanie wartości `false`null: po `null`powrocie argument input nie jest .</span><span class="sxs-lookup"><span data-stu-id="8afa2-223">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="8afa2-224">Metoda <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> zostanie oznaczona jako pokazano powyżej dla .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8afa2-224">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="8afa2-225">Może mieć podobne metody w bazie kodu, które sprawdzają stan obiektów dla wartości null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-225">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="8afa2-226">Kompilator nie rozpoznaje niestandardowych metod sprawdzania wartości null i musisz samodzielnie dodać adnotacje.</span><span class="sxs-lookup"><span data-stu-id="8afa2-226">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="8afa2-227">Po dodaniu atrybutu, analiza statyczna kompilatora wie, kiedy testowana zmienna została sprawdzona wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-227">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="8afa2-228">Innym zastosowaniem `Try*` dla tych atrybutów jest wzorzec.</span><span class="sxs-lookup"><span data-stu-id="8afa2-228">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="8afa2-229">Warunki powarunkowe `ref` `out` i zmienne są przekazywane za pośrednictwem wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="8afa2-229">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="8afa2-230">Należy wziąć pod uwagę tę metodę pokazano wcześniej:</span><span class="sxs-lookup"><span data-stu-id="8afa2-230">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="8afa2-231">Poprzednia metoda jest zgodna z typowym idiomem `message` .NET: zwracana wartość wskazuje, czy została ustawiona na znalezioną wartość lub, jeśli nie zostanie znaleziony żaden komunikat, do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="8afa2-231">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="8afa2-232">Jeśli metoda `true`zwraca , `message` wartość nie jest null; w przeciwnym razie `message` metoda ustawia wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-232">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="8afa2-233">Można przekazać, że idiom przy użyciu atrybutu. `NotNullWhen`</span><span class="sxs-lookup"><span data-stu-id="8afa2-233">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="8afa2-234">Podczas aktualizowania podpisu dla typów `message` odwołań, których można unieważnić, należy wykonać `string?` i dodać atrybut:</span><span class="sxs-lookup"><span data-stu-id="8afa2-234">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="8afa2-235">W poprzednim przykładzie wartość `message` jest znana jako nie `TryGetMessage` `true`null podczas zwraca .</span><span class="sxs-lookup"><span data-stu-id="8afa2-235">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="8afa2-236">Podobne metody w bazie kodu należy dodawać adnotacje w `null`taki sam sposób: argumenty mogą `true`być i są znane jako nie null, gdy metoda zwraca .</span><span class="sxs-lookup"><span data-stu-id="8afa2-236">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="8afa2-237">Istnieje jeden atrybut końcowy, który może być również potrzebny.</span><span class="sxs-lookup"><span data-stu-id="8afa2-237">There's one final attribute you may also need.</span></span> <span data-ttu-id="8afa2-238">Czasami stan zerowy wartości zwracanej zależy od stanu zerowego jednego lub więcej argumentów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8afa2-238">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="8afa2-239">Metody te zwracają wartość nie null, gdy pewne `null`argumenty wejściowe nie są .</span><span class="sxs-lookup"><span data-stu-id="8afa2-239">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="8afa2-240">Aby poprawnie dodawać adnotacje `NotNullIfNotNull` do tych metod, należy użyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8afa2-240">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="8afa2-241">Należy wziąć pod uwagę następującą metodę:</span><span class="sxs-lookup"><span data-stu-id="8afa2-241">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="8afa2-242">Jeśli `url` argument nie jest null, dane `null`wyjściowe nie jest .</span><span class="sxs-lookup"><span data-stu-id="8afa2-242">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="8afa2-243">Po włączeniu odwołań nullable, że podpis działa poprawnie, pod warunkiem, że interfejs API nigdy nie akceptuje null danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8afa2-243">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="8afa2-244">Jednak jeśli dane wejściowe może być null, a następnie zwraca wartość może być również null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-244">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="8afa2-245">W związku z tym można zmienić podpis na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="8afa2-245">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="8afa2-246">To również działa, ale często zmusza `null` dzwoniących do wdrożenia dodatkowych kontroli.</span><span class="sxs-lookup"><span data-stu-id="8afa2-246">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="8afa2-247">Umowa jest taka, że `null` wartość zwracana `url` będzie `null`tylko wtedy, gdy argument wejściowy jest .</span><span class="sxs-lookup"><span data-stu-id="8afa2-247">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="8afa2-248">Aby wyrazić tę umowę, należy opisać tę metodę, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="8afa2-248">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="8afa2-249">Wartość zwracana i argument zostały oś `?` tym adnotacje ze `null`wskazaniem, że albo może być .</span><span class="sxs-lookup"><span data-stu-id="8afa2-249">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="8afa2-250">Atrybut dalej wyjaśnia, że wartość zwracana nie będzie `url` null, `null`gdy argument nie jest .</span><span class="sxs-lookup"><span data-stu-id="8afa2-250">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="8afa2-251">Warunkowe warunki postconditions przy użyciu tych atrybutów:</span><span class="sxs-lookup"><span data-stu-id="8afa2-251">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="8afa2-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy nienastępny do wartości `bool` null może mieć wartość null, gdy metoda zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8afa2-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="8afa2-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do null nie będzie `bool` null, gdy metoda zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8afa2-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="8afa2-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Zwracana wartość nie jest zerowa, jeśli argument wejściowy dla określonego parametru nie jest null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="verify-unreachable-code"></a><span data-ttu-id="8afa2-255">Weryfikowanie nieosiągalnego kodu</span><span class="sxs-lookup"><span data-stu-id="8afa2-255">Verify unreachable code</span></span>

<span data-ttu-id="8afa2-256">Niektóre metody, zazwyczaj pomocników wyjątków lub innych metod narzędzia, zawsze zakończyć, zgłaszając wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8afa2-256">Some methods, typically exception helpers or other utility methods, always exit by throwing an exception.</span></span> <span data-ttu-id="8afa2-257">Lub pomocnika może zgłosić wyjątek na podstawie wartości argumentu logicznego.</span><span class="sxs-lookup"><span data-stu-id="8afa2-257">Or, a helper may throw an exception based on the value of a Boolean argument.</span></span>

<span data-ttu-id="8afa2-258">W pierwszym przypadku można dodać `DoesNotReturn` atrybut do deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="8afa2-258">In the first case, you can add the `DoesNotReturn` attribute to the method declaration.</span></span> <span data-ttu-id="8afa2-259">Kompilator pomaga na trzy sposoby.</span><span class="sxs-lookup"><span data-stu-id="8afa2-259">The compiler helps you in three ways.</span></span> <span data-ttu-id="8afa2-260">Najpierw kompilator generuje ostrzeżenie, jeśli istnieje ścieżka, w której metoda może zakończyć działanie bez zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8afa2-260">First, the compiler issues a warning if there is a path where the method can exit without throwing an exception.</span></span> <span data-ttu-id="8afa2-261">Po drugie kompilator oznacza dowolny kod po wywołaniu tej metody `catch` jako *nieosiągalny*, dopóki nie zostanie napotkana odpowiednia klauzula.</span><span class="sxs-lookup"><span data-stu-id="8afa2-261">Second, the compiler marks any code after a call to that method as *unreachable*, until an appropriate `catch` clause is encountered.</span></span> <span data-ttu-id="8afa2-262">Po trzecie, nieosiągalny kod nie wpłynie na żadne stany null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-262">Third, the unreachable code won't affect any null states.</span></span> <span data-ttu-id="8afa2-263">Należy wziąć pod uwagę tę metodę:</span><span class="sxs-lookup"><span data-stu-id="8afa2-263">Consider this method:</span></span>

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

<span data-ttu-id="8afa2-264">W drugim przypadku należy `DoesNotReturnIf` dodać atrybut do parametru logicznego metody.</span><span class="sxs-lookup"><span data-stu-id="8afa2-264">In the second case, you add the `DoesNotReturnIf` attribute to a Boolean parameter of the method.</span></span> <span data-ttu-id="8afa2-265">Poprzedni przykład można zmodyfikować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8afa2-265">You can modify the previous example as follows:</span></span>

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a><span data-ttu-id="8afa2-266">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="8afa2-266">Summary</span></span>

<span data-ttu-id="8afa2-267">Dodawanie typów odwołań do wartości nullable zapewnia początkowe słownictwo opisujące `null`oczekiwania interfejsów API dla zmiennych, które mogą być .</span><span class="sxs-lookup"><span data-stu-id="8afa2-267">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="8afa2-268">Dodatkowe atrybuty zapewniają bogatsze słownictwo do opisania stanu null zmiennych jako warunków wstępnych i postconditions.</span><span class="sxs-lookup"><span data-stu-id="8afa2-268">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="8afa2-269">Te atrybuty jaśniej opisują twoje oczekiwania i zapewniają lepsze środowisko dla deweloperów korzystających z interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="8afa2-269">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="8afa2-270">Podczas aktualizowania bibliotek dla kontekstu możliwego do podenia, dodaj te atrybuty, aby poprowadzić użytkowników interfejsów API do prawidłowego użycia.</span><span class="sxs-lookup"><span data-stu-id="8afa2-270">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="8afa2-271">Te atrybuty pomagają w pełni opisać zerowy stan argumentów wejściowych i zwracać wartości:</span><span class="sxs-lookup"><span data-stu-id="8afa2-271">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="8afa2-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy nienastępny do wartości null może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="8afa2-273">[NieuprawnionyNull:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Nullable argument wejściowy nigdy nie powinien być null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="8afa2-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana bez wartości null może być wartość null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="8afa2-275">[NotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)Nullable wartość zwracana nigdy nie będzie null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="8afa2-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy nienastępny do wartości `bool` null może mieć wartość null, gdy metoda zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8afa2-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="8afa2-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do null nie będzie `bool` null, gdy metoda zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8afa2-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="8afa2-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Zwracana wartość nie jest zerowa, jeśli argument wejściowy dla określonego parametru nie jest null.</span><span class="sxs-lookup"><span data-stu-id="8afa2-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="8afa2-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Metoda nigdy nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="8afa2-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="8afa2-280">Innymi słowy zawsze zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8afa2-280">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="8afa2-281">[DoesNotReturnIf:](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute)Ta metoda nigdy nie `bool` zwraca, jeśli skojarzony parametr ma określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="8afa2-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>
