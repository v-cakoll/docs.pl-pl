---
title: Podpisy (F#)
description: "Dowiedz się, jak używać plik sygnatury języka F # do przechowywania informacji o publiczne podpisów zestawu F # program elementów, takich jak typy, obszary nazw i modułów."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 76c84a62-b2f6-44ec-8238-e687e2f7d18e
ms.openlocfilehash: d0f71c6472852268303a2d3af2e4b0a3c256704e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="signatures"></a><span data-ttu-id="db7e0-104">Podpisy</span><span class="sxs-lookup"><span data-stu-id="db7e0-104">Signatures</span></span>

<span data-ttu-id="db7e0-105">Plik sygnatury zawiera informacje o publiczne podpisów zestawu F # program elementów, takich jak typy, obszary nazw i modułów.</span><span class="sxs-lookup"><span data-stu-id="db7e0-105">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="db7e0-106">Może służyć do określenia dostępność tych elementów programu.</span><span class="sxs-lookup"><span data-stu-id="db7e0-106">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="db7e0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db7e0-107">Remarks</span></span>
<span data-ttu-id="db7e0-108">Dla każdego języka F # pliku kod, mogą mieć *plik sygnatury*, czyli plik, który ma taką samą nazwę jak plik kodu, ale .fsi rozszerzenia zamiast języka.</span><span class="sxs-lookup"><span data-stu-id="db7e0-108">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="db7e0-109">Pliki sygnatur można również dodać do kompilacji wiersza polecenia, korzystając z wiersza polecenia bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="db7e0-109">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="db7e0-110">Aby odróżnić pliki kodu i pliki podpisów, pliki kodu są czasami określane jako *plików implementacji*.</span><span class="sxs-lookup"><span data-stu-id="db7e0-110">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="db7e0-111">W projekcie plik podpisu należy poprzedzać pliku skojarzonego kodu.</span><span class="sxs-lookup"><span data-stu-id="db7e0-111">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="db7e0-112">Plik sygnatury opisuje obszary nazw, modułów, typy i elementy członkowskie w odpowiedniego pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-112">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="db7e0-113">Możesz skorzystać z informacji w pliku podpisu do określenia części kodu w odpowiedniej implementacji plików są dostępne z kodu poza pliku implementacji, i jakie elementy są wewnętrzne pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-113">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="db7e0-114">Przestrzenie nazw, moduły i typy, które zostaną uwzględnione w pliku podpis musi być podzbiór przestrzeni nazw, moduły i typy, które znajdują się w pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-114">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="db7e0-115">Z pewnymi wyjątkami zauważyć w dalszej części tego tematu te elementy języka, które nie są wymienione w pliku podpisu są uznawane za prywatne do pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-115">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="db7e0-116">Jeśli plik podpisu nie zostanie znaleziony w projekcie lub wiersza polecenia, dostępność domyślny jest używany.</span><span class="sxs-lookup"><span data-stu-id="db7e0-116">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="db7e0-117">Aby uzyskać więcej informacji o ułatwieniach dostępu domyślnego, zobacz [kontroli dostępu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="db7e0-117">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="db7e0-118">W pliku podpisu nie powtarzaj definicji typów i implementacje każdej metody lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-118">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="db7e0-119">W zamian użyj podpis dla każdej metody i funkcji, która działa jako pełną specyfikację funkcji, które jest implementowany przez fragment modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="db7e0-119">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="db7e0-120">Składnia podpis typu jest taka sama, jak używać w deklaracjach metoda abstrakcyjna w abstrakcyjnej klasy i interfejsy i jest również wyświetlany za pomocą funkcji IntelliSense i fsi.exe interpreter języka F # wyświetlanych poprawnie skompilowanych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="db7e0-120">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="db7e0-121">Jeśli nie ma wystarczającej ilości informacji w podpisie typu, aby wskazać, czy typ jest zapieczętowany lub czy jest to typ interfejsu, należy dodać atrybut wskazujący rodzaj typu w kompilatorze.</span><span class="sxs-lookup"><span data-stu-id="db7e0-121">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="db7e0-122">W poniższej tabeli opisano atrybuty, które używają do tego celu.</span><span class="sxs-lookup"><span data-stu-id="db7e0-122">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="db7e0-123">Atrybut</span><span class="sxs-lookup"><span data-stu-id="db7e0-123">Attribute</span></span>|<span data-ttu-id="db7e0-124">Opis</span><span class="sxs-lookup"><span data-stu-id="db7e0-124">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="db7e0-125">Dla typu, który nie ma abstrakcyjnych elementów członkowskich lub który nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="db7e0-125">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="db7e0-126">Dla typu, który jest interfejsem.</span><span class="sxs-lookup"><span data-stu-id="db7e0-126">For a type that is an interface.</span></span>|
<span data-ttu-id="db7e0-127">Kompilator generuje błąd, jeśli atrybuty nie są spójne podpisu i deklaracji w pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-127">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="db7e0-128">Użyj słowa kluczowego `val` do tworzenia podpisu wartość lub wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-128">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="db7e0-129">Słowo kluczowe `type` wprowadza podpis typu.</span><span class="sxs-lookup"><span data-stu-id="db7e0-129">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="db7e0-130">Plik sygnatury można wygenerować za pomocą `--sig` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="db7e0-130">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="db7e0-131">Ogólnie rzecz biorąc możesz nie zapisuj .fsi pliki ręcznie.</span><span class="sxs-lookup"><span data-stu-id="db7e0-131">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="db7e0-132">Zamiast tego należy wygenerować .fsi plików przy użyciu kompilatora, dodaj je do projektu, jeśli istnieje i edytować je przez usunięcie metod i funkcje, które nie mają być dostępne.</span><span class="sxs-lookup"><span data-stu-id="db7e0-132">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="db7e0-133">Istnieje kilka reguł sygnatur typu:</span><span class="sxs-lookup"><span data-stu-id="db7e0-133">There are several rules for type signatures:</span></span>


- <span data-ttu-id="db7e0-134">Skróty typów w pliku z implementacją nie musi odpowiadać typu bez skrót w pliku podpisu.</span><span class="sxs-lookup"><span data-stu-id="db7e0-134">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="db7e0-135">Rekordów i rozłączne musi ujawniać wszystkie lub żadne swoich pól i konstruktory i kolejności w sygnaturze musi odpowiadać kolejności w pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-135">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="db7e0-136">Klasy może ujawnić niektóre, wszystkie lub żadne swoich pól i metod w podpisie.</span><span class="sxs-lookup"><span data-stu-id="db7e0-136">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="db7e0-137">Klasy i struktury, które mają konstruktorów musi ujawniać deklaracji ich klas podstawowych ( `inherits` deklaracji).</span><span class="sxs-lookup"><span data-stu-id="db7e0-137">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="db7e0-138">Ponadto klas i struktur, które mają konstruktorów musi ujawniać wszystkie metody abstrakcyjne i deklaracjami interfejs.</span><span class="sxs-lookup"><span data-stu-id="db7e0-138">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="db7e0-139">Typy interfejsów muszą ujawnić, wszystkie metody i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="db7e0-139">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="db7e0-140">Zasady na wartość podpisy są następujące:</span><span class="sxs-lookup"><span data-stu-id="db7e0-140">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="db7e0-141">Modyfikatory dostępu (`public`, `internal`i tak dalej) i `inline` i `mutable` Modyfikatory w sygnaturze musi odpowiadają implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-141">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="db7e0-142">Musi być zgodna z liczbą parametrów typu ogólnego, (lub niejawnie wywnioskować jawnie deklarować) i typy i ograniczenia parametrów typu ogólnego typu muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="db7e0-142">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="db7e0-143">Jeśli `Literal` atrybut jest używany, musi znajdować się w sygnaturze i implementacji i dla obu należy użyć tej samej wartości literału.</span><span class="sxs-lookup"><span data-stu-id="db7e0-143">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="db7e0-144">Wzorzec parametrów (znanej także jako *argumentów*) sygnatury i implementacji muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="db7e0-144">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


<span data-ttu-id="db7e0-145">W poniższym przykładzie kodu przedstawiono przykład pliku podpisu z przestrzeni nazw, modułu wartość funkcji i podpisy typu wraz z odpowiednich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="db7e0-145">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="db7e0-146">Przedstawia on również odpowiedniego pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-146">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="db7e0-147">Poniższy kod przedstawia plik implementacji.</span><span class="sxs-lookup"><span data-stu-id="db7e0-147">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="db7e0-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db7e0-148">See Also</span></span>
[<span data-ttu-id="db7e0-149">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="db7e0-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="db7e0-150">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="db7e0-150">Access Control</span></span>](access-control.md)

[<span data-ttu-id="db7e0-151">Opcje kompilatora</span><span class="sxs-lookup"><span data-stu-id="db7e0-151">Compiler Options</span></span>](compiler-options.md)
