---
title: Zmienna obiektu lub zmienna bloku With nie jest ustawiona
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2c0c47b359e218111c1629ea574303a6d663046
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297931"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="10bed-102">Zmienna obiektu lub zmienna bloku With nie jest ustawiona</span><span class="sxs-lookup"><span data-stu-id="10bed-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="10bed-103">Odwołuje się do nieprawidłowego obiektu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="10bed-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="10bed-104">Ten błąd może wystąpić z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="10bed-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="10bed-105">Zmienna została zadeklarowana bez określania typu.</span><span class="sxs-lookup"><span data-stu-id="10bed-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="10bed-106">Jeśli zmienna jest zadeklarowana bez określania typu, jego wartość domyślna to typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="10bed-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="10bed-107">Na przykład, Zmienna zadeklarowana ze `Dim x` byłoby typu `Object;` Zmienna zadeklarowana ze `Dim x As String` byłoby typu `String`.</span><span class="sxs-lookup"><span data-stu-id="10bed-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="10bed-108">`Option Strict` Instrukcji nie zezwalają na niejawnego wpisywania, które spowodowało, że `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="10bed-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="10bed-109">Jeżeli pominięto ten typ, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="10bed-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="10bed-110">Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="10bed-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="10bed-111">Podjęto próbę odwołują się do obiektu, który został ustawiony na `Nothing`</span><span class="sxs-lookup"><span data-stu-id="10bed-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="10bed-112">.</span><span class="sxs-lookup"><span data-stu-id="10bed-112">.</span></span>  
  
-   <span data-ttu-id="10bed-113">Podjęto próbę uzyskania dostępu do elementu zmienną tablicy, która nie została prawidłowo zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="10bed-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="10bed-114">Na przykład Tablica zadeklarowana jako `products() As String` wyzwoli ten błąd, jeśli zostanie podjęta próba odwołania się do elementu tablicy `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="10bed-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="10bed-115">Tablica nie ma żadnych elementów i jest traktowany jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="10bed-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="10bed-116">Podjęto próbę dostępu do kodu w ramach `With...End With` blokowania, zanim blok został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="10bed-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="10bed-117">A `With...End With` bloku musi zostać zainicjowany, wykonując `With` instrukcji punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="10bed-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10bed-118">We wcześniejszych wersjach programu Visual Basic lub VBA ten błąd również została wyzwolona przez przypisywanie wartości do zmiennej bez użycia `Set` — słowo kluczowe (`x = "name"` zamiast `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="10bed-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="10bed-119">`Set` — Słowo kluczowe nie jest już prawidłowy w języku Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="10bed-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10bed-120">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="10bed-120">To correct this error</span></span>  
  
1. <span data-ttu-id="10bed-121">Ustaw `Option Strict` do `On` , dodając następujący kod na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="10bed-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2. <span data-ttu-id="10bed-122">Jeśli nie chcesz umożliwić `Option Strict`, wyszukiwanie w kodzie żadnych zmiennych, które zostały określone bez typu (`Dim x` zamiast `Dim x As String`) i Dodaj zamierzony typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="10bed-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3. <span data-ttu-id="10bed-123">Upewnij się, że nie są odwołujesz się do zmiennej obiektu, który został ustawiony na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="10bed-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="10bed-124">Wyszukiwanie w kodzie słowa kluczowego `Nothing`i popraw swój kod, aby obiekt nie jest ustawiony na `Nothing` dopóki po ma on wywołany.</span><span class="sxs-lookup"><span data-stu-id="10bed-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4. <span data-ttu-id="10bed-125">Upewnij się, że wszystkie zmienne tablicy są wymiary przed można uzyskiwać do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="10bed-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="10bed-126">Po utworzeniu tablicy można przypisać wymiaru (`Dim x(5) As String` zamiast `Dim x() As String`), lub użyj `ReDim` słowo kluczowe, aby ustawić wymiary tablicy, zanim zostanie najpierw uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="10bed-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5. <span data-ttu-id="10bed-127">Upewnij się, że Twoje `With` bloku jest inicjowany przez wykonanie `With` instrukcji punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="10bed-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10bed-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10bed-128">See also</span></span>

- [<span data-ttu-id="10bed-129">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="10bed-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="10bed-130">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="10bed-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="10bed-131">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="10bed-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
