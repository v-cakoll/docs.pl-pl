---
title: Zmienna obiektu lub zmienna bloku With nie jest ustawiona
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2bd1be83f57dbdc7a64b407dc1052074e19c74b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597667"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="f1d31-102">Zmienna obiektu lub zmienna bloku With nie jest ustawiona</span><span class="sxs-lookup"><span data-stu-id="f1d31-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="f1d31-103">Odwołuje się do zmiennej nieprawidłowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="f1d31-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="f1d31-104">Ten błąd może wystąpić z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="f1d31-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="f1d31-105">Zmienna została zadeklarowana bez określania typu.</span><span class="sxs-lookup"><span data-stu-id="f1d31-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="f1d31-106">Jeśli zmienna została zadeklarowana bez określania typu, domyślnie na typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="f1d31-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="f1d31-107">Na przykład Zmienna zadeklarowana ze `Dim x` może być typu `Object;` Zmienna zadeklarowana ze `Dim x As String` może być typu `String`.</span><span class="sxs-lookup"><span data-stu-id="f1d31-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="f1d31-108">`Option Strict` Instrukcji nie zezwala na niejawne wpisanie, który daje w `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="f1d31-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="f1d31-109">W przypadku pominięcia tego typu, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f1d31-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="f1d31-110">Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f1d31-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="f1d31-111">Próbujesz się odwołać obiektu, który został ustawiony `Nothing`</span><span class="sxs-lookup"><span data-stu-id="f1d31-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="f1d31-112">.</span><span class="sxs-lookup"><span data-stu-id="f1d31-112">.</span></span>  
  
-   <span data-ttu-id="f1d31-113">Podjęto próbę uzyskania dostępu do elementu tablicy zmiennej, która nie została poprawnie zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="f1d31-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="f1d31-114">Na przykład Tablica zadeklarowana jako `products() As String` wyzwoli błąd, jeśli zostanie podjęta próba odwołania się do elementu tablicy `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="f1d31-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="f1d31-115">Tablica nie ma żadnych elementów i jest traktowany jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="f1d31-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="f1d31-116">Podjęto próbę kodu dostępu w ramach `With...End With` zablokować przed bloku został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="f1d31-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="f1d31-117">A `With...End With` bloku musi zostać zainicjowany, wykonując `With` instrukcji punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="f1d31-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1d31-118">We wcześniejszych wersjach programu Visual Basic lub VBA ten błąd został także wywołany przez przypisywanie wartości do zmiennej, bez korzystania z `Set` — słowo kluczowe (`x = "name"` zamiast `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="f1d31-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="f1d31-119">`Set` — Słowo kluczowe nie jest już prawidłowy w języku Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="f1d31-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1d31-120">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f1d31-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="f1d31-121">Ustaw `Option Strict` do `On` przez dodanie poniższego kodu do początku pliku:</span><span class="sxs-lookup"><span data-stu-id="f1d31-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="f1d31-122">Jeśli nie chcesz włączyć `Option Strict`, wyszukiwanie kodu zmiennych, które zostały określone bez typu (`Dim x` zamiast `Dim x As String`) i Dodaj do deklaracji danego typu.</span><span class="sxs-lookup"><span data-stu-id="f1d31-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="f1d31-123">Upewnij się, że nie ma odwołanie do zmiennej obiektu, który został ustawiony na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f1d31-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="f1d31-124">Wyszukiwanie kodu słowa kluczowego `Nothing`, a zmienić swój kod, aby obiekt nie został skonfigurowany do `Nothing` dopóki po ma on wywołany.</span><span class="sxs-lookup"><span data-stu-id="f1d31-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="f1d31-125">Upewnij się, że wszystkie zmienne tablicy są wymiarów przed ich dostępu.</span><span class="sxs-lookup"><span data-stu-id="f1d31-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="f1d31-126">Po utworzeniu tablicy można przypisać wymiaru (`Dim x(5) As String` zamiast `Dim x() As String`), lub użyj `ReDim` — słowo kluczowe ustawienie wymiarów tablicy, zanim zostanie najpierw do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="f1d31-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="f1d31-127">Upewnij się, że Twoje `With` bloku został zainicjowany, wykonując `With` instrukcji punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="f1d31-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d31-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1d31-128">See Also</span></span>  
 [<span data-ttu-id="f1d31-129">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="f1d31-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="f1d31-130">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f1d31-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="f1d31-131">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f1d31-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
