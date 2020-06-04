---
title: Zmienna obiektu lub zmienna bloku With nie jest ustawiona
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: d1778e2bb58d32e976f10b3fba1637918278d36e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409286"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="fdfda-102">Zmienna obiektu lub zmienna bloku With nie jest ustawiona</span><span class="sxs-lookup"><span data-stu-id="fdfda-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="fdfda-103">Odwołuje się do nieprawidłowej zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="fdfda-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="fdfda-104">Ten błąd może wystąpić z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="fdfda-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="fdfda-105">Zmienna została zadeklarowana bez określenia typu.</span><span class="sxs-lookup"><span data-stu-id="fdfda-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="fdfda-106">Jeśli zmienna jest zadeklarowana bez określenia typu, wartość domyślna to Type `Object` .</span><span class="sxs-lookup"><span data-stu-id="fdfda-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="fdfda-107">Na przykład zmienna zadeklarowana jako `Dim x` powinna być typu `Object;` Zmienna zadeklarowana z `Dim x As String` być typu `String` .</span><span class="sxs-lookup"><span data-stu-id="fdfda-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="fdfda-108">`Option Strict`Instrukcja nie zezwala na niejawne wpisanie, które powoduje wystąpienie `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="fdfda-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="fdfda-109">Jeśli pominięto typ, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fdfda-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="fdfda-110">Zobacz [Option Strict, instrukcja](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdfda-110">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="fdfda-111">Próbujesz odwołać się do obiektu, który został ustawiony na `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="fdfda-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="fdfda-112">Próbujesz uzyskać dostęp do elementu zmiennej tablicowej, która nie została prawidłowo zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="fdfda-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="fdfda-113">Na przykład tablica zadeklarowana jako `products() As String` spowoduje wyzwolenie błędu w przypadku próby odwołania się do elementu tablicy `products(3) = "Widget"` .</span><span class="sxs-lookup"><span data-stu-id="fdfda-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="fdfda-114">Tablica nie ma elementów i jest traktowana jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="fdfda-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="fdfda-115">Próbujesz uzyskać dostęp do kodu w `With...End With` bloku przed zainicjowaniem bloku.</span><span class="sxs-lookup"><span data-stu-id="fdfda-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="fdfda-116">`With...End With`Blok musi być zainicjowany przez wykonanie `With` punktu wejścia instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fdfda-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="fdfda-117">We wcześniejszych wersjach Visual Basic lub VBA ten błąd został również wyzwolony przez przypisanie wartości do zmiennej bez użycia `Set` słowa kluczowego ( `x = "name"` zamiast `Set x = "name"` ).</span><span class="sxs-lookup"><span data-stu-id="fdfda-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="fdfda-118">`Set`Słowo kluczowe nie jest już prawidłowe w Visual Basic .NET.</span><span class="sxs-lookup"><span data-stu-id="fdfda-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fdfda-119">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fdfda-119">To correct this error</span></span>

1. <span data-ttu-id="fdfda-120">Ustaw `Option Strict` na `On` , dodając następujący kod na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="fdfda-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="fdfda-121">Po uruchomieniu projektu, w **Lista błędów** dla każdej zmiennej, która została określona bez typu, pojawi się błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fdfda-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="fdfda-122">Jeśli nie chcesz włączać `Option Strict` , przeszukaj kod pod kątem zmiennych, które zostały określone bez typu ( `Dim x` zamiast `Dim x As String` ) i Dodaj odpowiedni typ do deklaracji.</span><span class="sxs-lookup"><span data-stu-id="fdfda-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="fdfda-123">Upewnij się, że nie odwołujesz się do zmiennej obiektu, która została ustawiona na `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="fdfda-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="fdfda-124">Przeszukaj kod słowa kluczowego `Nothing` i popraw kod, tak aby obiekt nie był ustawiony na wartość `Nothing` until po odwołaniu się do niego.</span><span class="sxs-lookup"><span data-stu-id="fdfda-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="fdfda-125">Przed uzyskaniem dostępu należy się upewnić, że wszystkie zmienne tablic są wymiarami.</span><span class="sxs-lookup"><span data-stu-id="fdfda-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="fdfda-126">Można przypisać wymiar, gdy najpierw utworzysz tablicę ( `Dim x(5) As String` zamiast `Dim x() As String` ) lub użyć `ReDim` słowa kluczowego, aby ustawić Wymiary tablicy przed pierwszym uzyskaniem do niej dostępu.</span><span class="sxs-lookup"><span data-stu-id="fdfda-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="fdfda-127">Upewnij się `With` , że blok jest zainicjowany przez wykonanie `With` punktu wejścia instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fdfda-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdfda-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdfda-128">See also</span></span>

- [<span data-ttu-id="fdfda-129">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="fdfda-129">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="fdfda-130">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fdfda-130">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="fdfda-131">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fdfda-131">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
