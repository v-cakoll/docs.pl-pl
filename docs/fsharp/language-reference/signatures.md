---
title: Podpisy (F#)
description: 'Dowiedz się, jak używać plik sygnatury języka F # do przechowywania informacji o publiczne podpisów zestawu F # program elementów, takich jak typy, obszary nazw i modułów.'
ms.date: 05/16/2016
ms.openlocfilehash: 6e182a1a0ac7f3f9fab27026e582d83ee737822e
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2018
ms.locfileid: "34149026"
---
# <a name="signatures"></a><span data-ttu-id="6fe09-103">Podpisy</span><span class="sxs-lookup"><span data-stu-id="6fe09-103">Signatures</span></span>

<span data-ttu-id="6fe09-104">Plik sygnatury zawiera informacje o publiczne podpisów zestawu F # program elementów, takich jak typy, obszary nazw i modułów.</span><span class="sxs-lookup"><span data-stu-id="6fe09-104">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="6fe09-105">Może służyć do określenia dostępność tych elementów programu.</span><span class="sxs-lookup"><span data-stu-id="6fe09-105">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="6fe09-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fe09-106">Remarks</span></span>
<span data-ttu-id="6fe09-107">Dla każdego języka F # pliku kod, mogą mieć *plik sygnatury*, czyli plik, który ma taką samą nazwę jak plik kodu, ale .fsi rozszerzenia zamiast języka.</span><span class="sxs-lookup"><span data-stu-id="6fe09-107">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="6fe09-108">Pliki sygnatur można również dodać do kompilacji wiersza polecenia, korzystając z wiersza polecenia bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="6fe09-108">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="6fe09-109">Aby odróżnić pliki kodu i pliki podpisów, pliki kodu są czasami określane jako *plików implementacji*.</span><span class="sxs-lookup"><span data-stu-id="6fe09-109">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="6fe09-110">W projekcie plik podpisu należy poprzedzać pliku skojarzonego kodu.</span><span class="sxs-lookup"><span data-stu-id="6fe09-110">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="6fe09-111">Plik sygnatury opisuje obszary nazw, modułów, typy i elementy członkowskie w odpowiedniego pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-111">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="6fe09-112">Możesz skorzystać z informacji w pliku podpisu do określenia części kodu w odpowiedniej implementacji plików są dostępne z kodu poza pliku implementacji, i jakie elementy są wewnętrzne pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-112">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="6fe09-113">Przestrzenie nazw, moduły i typy, które zostaną uwzględnione w pliku podpis musi być podzbiór przestrzeni nazw, moduły i typy, które znajdują się w pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-113">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="6fe09-114">Z pewnymi wyjątkami zauważyć w dalszej części tego tematu te elementy języka, które nie są wymienione w pliku podpisu są uznawane za prywatne do pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-114">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="6fe09-115">Jeśli plik podpisu nie zostanie znaleziony w projekcie lub wiersza polecenia, dostępność domyślny jest używany.</span><span class="sxs-lookup"><span data-stu-id="6fe09-115">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="6fe09-116">Aby uzyskać więcej informacji o ułatwieniach dostępu domyślnego, zobacz [kontroli dostępu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="6fe09-116">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="6fe09-117">W pliku podpisu nie powtarzaj definicji typów i implementacje każdej metody lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-117">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="6fe09-118">W zamian użyj podpis dla każdej metody i funkcji, która działa jako pełną specyfikację funkcji, które jest implementowany przez fragment modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6fe09-118">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="6fe09-119">Składnia podpis typu jest taka sama, jak używać w deklaracjach metoda abstrakcyjna w abstrakcyjnej klasy i interfejsy i jest również wyświetlany za pomocą funkcji IntelliSense i fsi.exe interpreter języka F # wyświetlanych poprawnie skompilowanych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6fe09-119">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="6fe09-120">Jeśli nie ma wystarczającej ilości informacji w podpisie typu, aby wskazać, czy typ jest zapieczętowany lub czy jest to typ interfejsu, należy dodać atrybut wskazujący rodzaj typu w kompilatorze.</span><span class="sxs-lookup"><span data-stu-id="6fe09-120">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="6fe09-121">W poniższej tabeli opisano atrybuty, które używają do tego celu.</span><span class="sxs-lookup"><span data-stu-id="6fe09-121">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="6fe09-122">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6fe09-122">Attribute</span></span>|<span data-ttu-id="6fe09-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6fe09-123">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="6fe09-124">Dla typu, który nie ma abstrakcyjnych elementów członkowskich lub który nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="6fe09-124">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="6fe09-125">Dla typu, który jest interfejsem.</span><span class="sxs-lookup"><span data-stu-id="6fe09-125">For a type that is an interface.</span></span>|
<span data-ttu-id="6fe09-126">Kompilator generuje błąd, jeśli atrybuty nie są spójne podpisu i deklaracji w pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-126">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="6fe09-127">Użyj słowa kluczowego `val` do tworzenia podpisu wartość lub wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-127">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="6fe09-128">Słowo kluczowe `type` wprowadza podpis typu.</span><span class="sxs-lookup"><span data-stu-id="6fe09-128">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="6fe09-129">Plik sygnatury można wygenerować za pomocą `--sig` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6fe09-129">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="6fe09-130">Ogólnie rzecz biorąc możesz nie zapisuj .fsi pliki ręcznie.</span><span class="sxs-lookup"><span data-stu-id="6fe09-130">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="6fe09-131">Zamiast tego należy wygenerować .fsi plików przy użyciu kompilatora, dodaj je do projektu, jeśli istnieje i edytować je przez usunięcie metod i funkcje, które nie mają być dostępne.</span><span class="sxs-lookup"><span data-stu-id="6fe09-131">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="6fe09-132">Istnieje kilka reguł sygnatur typu:</span><span class="sxs-lookup"><span data-stu-id="6fe09-132">There are several rules for type signatures:</span></span>


- <span data-ttu-id="6fe09-133">Skróty typów w pliku z implementacją nie musi odpowiadać typu bez skrót w pliku podpisu.</span><span class="sxs-lookup"><span data-stu-id="6fe09-133">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="6fe09-134">Rekordów i rozłączne musi ujawniać wszystkie lub żadne swoich pól i konstruktory i kolejności w sygnaturze musi odpowiadać kolejności w pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-134">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="6fe09-135">Klasy może ujawnić niektóre, wszystkie lub żadne swoich pól i metod w podpisie.</span><span class="sxs-lookup"><span data-stu-id="6fe09-135">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="6fe09-136">Klasy i struktury, które mają konstruktorów musi ujawniać deklaracji ich klas podstawowych ( `inherits` deklaracji).</span><span class="sxs-lookup"><span data-stu-id="6fe09-136">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="6fe09-137">Ponadto klas i struktur, które mają konstruktorów musi ujawniać wszystkie metody abstrakcyjne i deklaracjami interfejs.</span><span class="sxs-lookup"><span data-stu-id="6fe09-137">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="6fe09-138">Typy interfejsów muszą ujawnić, wszystkie metody i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="6fe09-138">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="6fe09-139">Zasady na wartość podpisy są następujące:</span><span class="sxs-lookup"><span data-stu-id="6fe09-139">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="6fe09-140">Modyfikatory dostępu (`public`, `internal`i tak dalej) i `inline` i `mutable` Modyfikatory w sygnaturze musi odpowiadają implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-140">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="6fe09-141">Musi być zgodna z liczbą parametrów typu ogólnego, (lub niejawnie wywnioskować jawnie deklarować) i typy i ograniczenia parametrów typu ogólnego typu muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="6fe09-141">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="6fe09-142">Jeśli `Literal` atrybut jest używany, musi znajdować się w sygnaturze i implementacji i dla obu należy użyć tej samej wartości literału.</span><span class="sxs-lookup"><span data-stu-id="6fe09-142">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="6fe09-143">Wzorzec parametrów (znanej także jako *argumentów*) sygnatury i implementacji muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="6fe09-143">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


- <span data-ttu-id="6fe09-144">Jeśli nazwy parametrów w pliku podpisu różnią się od odpowiedniego pliku implementacji, z nazwą w pliku podpisu zostanie użyty, co może spowodować problemy podczas debugowania lub profilowania.</span><span class="sxs-lookup"><span data-stu-id="6fe09-144">If parameter names in a signature file differ from the corresponding implementation file, the name in the signature file will be used instead, which may cause issues when debugging or profiling.</span></span> <span data-ttu-id="6fe09-145">Jeśli chcesz otrzymywać powiadomienia o takich niezgodności, Włącz ostrzeżenie 3218 w pliku projektu lub podczas wywoływania kompilator (zobacz `--warnon` w obszarze [— opcje kompilatora](compiler-options.md)).</span><span class="sxs-lookup"><span data-stu-id="6fe09-145">If you wish to be notified of such mismatches, enable warning 3218 in your project file or when invoking the compiler (see `--warnon` under [Compiler Options](compiler-options.md)).</span></span>


<span data-ttu-id="6fe09-146">W poniższym przykładzie kodu przedstawiono przykład pliku podpisu z przestrzeni nazw, modułu wartość funkcji i podpisy typu wraz z odpowiednich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6fe09-146">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="6fe09-147">Przedstawia on również odpowiedniego pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-147">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="6fe09-148">Poniższy kod przedstawia plik implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fe09-148">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="6fe09-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fe09-149">See Also</span></span>
[<span data-ttu-id="6fe09-150">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="6fe09-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="6fe09-151">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="6fe09-151">Access Control</span></span>](access-control.md)

[<span data-ttu-id="6fe09-152">Opcje kompilatora</span><span class="sxs-lookup"><span data-stu-id="6fe09-152">Compiler Options</span></span>](compiler-options.md)
