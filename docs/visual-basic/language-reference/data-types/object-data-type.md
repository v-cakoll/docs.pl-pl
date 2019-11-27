---
title: Object — typ danych
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 2ccb9b69b865c259d078ed9642d63c7f83514756
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343964"
---
# <a name="object-data-type"></a><span data-ttu-id="615be-102">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="615be-102">Object Data Type</span></span>

<span data-ttu-id="615be-103">Przechowuje adresy odwołujące się do obiektów.</span><span class="sxs-lookup"><span data-stu-id="615be-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="615be-104">Do zmiennej `Object` można przypisać dowolny typ referencyjny (ciąg, tablicę, klasę lub interfejs).</span><span class="sxs-lookup"><span data-stu-id="615be-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="615be-105">Zmienna `Object` może odwoływać się również do danych dowolnego typu wartości (numeryczne, `Boolean`, `Char`, `Date`, struktura lub Wyliczenie).</span><span class="sxs-lookup"><span data-stu-id="615be-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>

## <a name="remarks"></a><span data-ttu-id="615be-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="615be-106">Remarks</span></span>

<span data-ttu-id="615be-107">Typ danych `Object` może wskazywać na dane dowolnego typu danych, łącznie z każdym wystąpieniem obiektu rozpoznawanym przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="615be-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="615be-108">Użyj `Object`, gdy nie wiesz w czasie kompilacji, jakie dane może wskazywać zmienna.</span><span class="sxs-lookup"><span data-stu-id="615be-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>

<span data-ttu-id="615be-109">Wartość domyślna `Object` jest `Nothing` (odwołanie o wartości null).</span><span class="sxs-lookup"><span data-stu-id="615be-109">The default value of `Object` is `Nothing` (a null reference).</span></span>

## <a name="data-types"></a><span data-ttu-id="615be-110">Typy danych</span><span class="sxs-lookup"><span data-stu-id="615be-110">Data Types</span></span>

<span data-ttu-id="615be-111">Do zmiennej `Object` można przypisać zmienną, stałą lub wyrażenie dowolnego typu danych.</span><span class="sxs-lookup"><span data-stu-id="615be-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="615be-112">Aby określić typ danych, do których odwołuje się `Object` zmienna, można użyć metody <xref:System.Type.GetTypeCode%2A> klasy <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="615be-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="615be-113">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="615be-113">The following example illustrates this.</span></span>

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

<span data-ttu-id="615be-114">Typ danych `Object` jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="615be-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="615be-115">Jednak Visual Basic traktuje zmienną `Object` jako typ wartości, gdy odwołuje się ona do danych typu wartości.</span><span class="sxs-lookup"><span data-stu-id="615be-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>

## <a name="storage"></a><span data-ttu-id="615be-116">Magazyn</span><span class="sxs-lookup"><span data-stu-id="615be-116">Storage</span></span>

<span data-ttu-id="615be-117">Niezależnie od tego, jaki typ danych odwołuje się do, zmienna `Object` nie zawiera samej wartości danych, ale raczej wskaźnikiem do wartości.</span><span class="sxs-lookup"><span data-stu-id="615be-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="615be-118">Zawsze używa czterech bajtów w pamięci komputera, ale nie obejmuje to magazynu dla danych reprezentujących wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="615be-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="615be-119">Ze względu na kod, który używa wskaźnika do lokalizowania danych, zmienne `Object` przechowujące typy wartości są nieco wolniejsze w celu uzyskania dostępu niż jawnie wpisane zmienne.</span><span class="sxs-lookup"><span data-stu-id="615be-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="615be-120">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="615be-120">Programming Tips</span></span>

- <span data-ttu-id="615be-121">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="615be-121">**Interop Considerations.**</span></span> <span data-ttu-id="615be-122">Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że typy wskaźnika w innych środowiskach nie są zgodne z typem `Object` Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="615be-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>

- <span data-ttu-id="615be-123">**Skuteczności.**</span><span class="sxs-lookup"><span data-stu-id="615be-123">**Performance.**</span></span> <span data-ttu-id="615be-124">Zmienna zadeklarowana z typem `Object` jest wystarczająco elastyczna, aby zawierała odwołanie do dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="615be-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="615be-125">Jednak po wywołaniu metody lub właściwości w takiej zmiennej zawsze naliczane są *późne powiązania* (w czasie wykonywania).</span><span class="sxs-lookup"><span data-stu-id="615be-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="615be-126">Aby wymusić *wczesne wiązanie* (w czasie kompilacji) i lepszą wydajność, należy zadeklarować zmienną z określoną nazwą klasy lub rzutować ją na określony typ danych.</span><span class="sxs-lookup"><span data-stu-id="615be-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>

  <span data-ttu-id="615be-127">Podczas deklarowania zmiennej obiektu spróbuj użyć konkretnego typu klasy, na przykład <xref:System.OperatingSystem>, zamiast uogólnionego typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="615be-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="615be-128">Należy również użyć najbardziej konkretnej dostępnej klasy, takiej jak <xref:System.Windows.Forms.TextBox>, a nie <xref:System.Windows.Forms.Control>, aby można było uzyskać dostęp do jej właściwości i metod.</span><span class="sxs-lookup"><span data-stu-id="615be-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="615be-129">Zazwyczaj można użyć listy **klas** w **Przeglądarka obiektów** , aby znaleźć dostępne nazwy klas.</span><span class="sxs-lookup"><span data-stu-id="615be-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>

- <span data-ttu-id="615be-130">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="615be-130">**Widening.**</span></span> <span data-ttu-id="615be-131">Wszystkie typy danych i wszystkie typy odwołań rozszerzają się do typu danych `Object`.</span><span class="sxs-lookup"><span data-stu-id="615be-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="615be-132">Oznacza to, że można skonwertować dowolny typ do `Object` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="615be-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

  <span data-ttu-id="615be-133">Jednak w przypadku konwersji między typami wartości i `Object`, Visual Basic wykonuje operacje nazywane *opakowaniem* i *rozpakowywaniem*, co powoduje wolniejsze wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="615be-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>

- <span data-ttu-id="615be-134">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="615be-134">**Type Characters.**</span></span> <span data-ttu-id="615be-135">`Object` nie ma znaku typu literału lub typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="615be-135">`Object` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="615be-136">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="615be-136">**Framework Type.**</span></span> <span data-ttu-id="615be-137">Odpowiedni typ w .NET Framework jest klasą <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="615be-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>

## <a name="example"></a><span data-ttu-id="615be-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="615be-138">Example</span></span>

<span data-ttu-id="615be-139">Poniższy przykład ilustruje zmienną `Object` wskazującą na wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="615be-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a><span data-ttu-id="615be-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="615be-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="615be-141">Typy danych</span><span class="sxs-lookup"><span data-stu-id="615be-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="615be-142">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="615be-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="615be-143">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="615be-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="615be-144">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="615be-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="615be-145">Instrukcje: określanie, czy dwa obiekty są powiązane</span><span class="sxs-lookup"><span data-stu-id="615be-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="615be-146">Instrukcje: określanie, czy dwa obiekty są jednakowe</span><span class="sxs-lookup"><span data-stu-id="615be-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
