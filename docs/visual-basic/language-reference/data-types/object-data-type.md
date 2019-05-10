---
title: Object — typ danych (Visual Basic)
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
ms.openlocfilehash: 593fda6a4949a55d77ae70edd19159a618cc6b6d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592077"
---
# <a name="object-data-type"></a><span data-ttu-id="ff822-102">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="ff822-102">Object Data Type</span></span>
<span data-ttu-id="ff822-103">Zawiera adresy, które odwołują się do obiektów.</span><span class="sxs-lookup"><span data-stu-id="ff822-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="ff822-104">Dowolnego typu odwołania (ciąg, macierz, klasy lub interfejsu) można przypisać do `Object` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ff822-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="ff822-105">`Object` Zmiennej może również odnosić się do danych o dowolnym typie wartości (numeryczne, `Boolean`, `Char`, `Date`, struktury lub wyliczenia).</span><span class="sxs-lookup"><span data-stu-id="ff822-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff822-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff822-106">Remarks</span></span>  
 <span data-ttu-id="ff822-107">`Object` Danych dowolnego typu danych, w tym dowolne wystąpienie obiektu, aplikacja rozpoznaje wskazać typ danych.</span><span class="sxs-lookup"><span data-stu-id="ff822-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="ff822-108">Użyj `Object` Jeśli nie wiesz, w czasie kompilacji dane typu zmiennej może wskazywać.</span><span class="sxs-lookup"><span data-stu-id="ff822-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="ff822-109">Wartość domyślna `Object` jest `Nothing` (odwołanie o wartości null).</span><span class="sxs-lookup"><span data-stu-id="ff822-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="ff822-110">Typy danych</span><span class="sxs-lookup"><span data-stu-id="ff822-110">Data Types</span></span>  
 <span data-ttu-id="ff822-111">Można przypisać zmiennej, stałej lub wyrażenia dowolnego typu danych, aby `Object` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ff822-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="ff822-112">Można ustalić typu danych `Object` obecnie odnosi się zmienna, możesz użyć <xref:System.Type.GetTypeCode%2A> metody <xref:System.Type?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="ff822-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ff822-113">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="ff822-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="ff822-114">`Object` — Typ danych jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="ff822-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="ff822-115">Jednakże, Visual Basic traktuje `Object` zmienną jako typ wartości, gdy jest on odnosi się do danych o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="ff822-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="ff822-116">Magazyn</span><span class="sxs-lookup"><span data-stu-id="ff822-116">Storage</span></span>  
 <span data-ttu-id="ff822-117">Niezależnie od typu danych, to dotyczy, `Object` automatycznie, ale raczej wskaźnika do wartości zmiennej nie zawiera wartości danych.</span><span class="sxs-lookup"><span data-stu-id="ff822-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="ff822-118">Zawsze używa cztery bajty w pamięci komputera, ale nie obejmuje to magazyn dla danych reprezentujący wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ff822-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="ff822-119">Ze względu na kod, który używa wskaźnika do zlokalizowania danych `Object` zawierający typy wartości zmiennych są nieco wolniejszy dostęp niż jawnie wpisane zmienne do.</span><span class="sxs-lookup"><span data-stu-id="ff822-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="ff822-120">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="ff822-120">Programming Tips</span></span>  
  
- <span data-ttu-id="ff822-121">**Uwagi dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="ff822-121">**Interop Considerations.**</span></span> <span data-ttu-id="ff822-122">Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać o tym, że typy wskaźników w innych środowiskach nie są zgodne z języka Visual Basic `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="ff822-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
- <span data-ttu-id="ff822-123">**Wydajność.**</span><span class="sxs-lookup"><span data-stu-id="ff822-123">**Performance.**</span></span> <span data-ttu-id="ff822-124">Zmienna deklarowana za pomocą `Object` typu jest na tyle elastyczna, aby zawierała odwołanie do dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff822-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="ff822-125">Jednak gdy wywołujesz metodę lub właściwość takiej zmiennej zawsze wiąże się z *późnym wiązaniu* (w czasie wykonywania).</span><span class="sxs-lookup"><span data-stu-id="ff822-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="ff822-126">Aby wymusić *wczesne powiązania* (w czasie kompilacji) i większą wydajność, Zadeklaruj zmienną o nazwie określonej klasy lub go rzutować na typ danych określonych.</span><span class="sxs-lookup"><span data-stu-id="ff822-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="ff822-127">Kiedy Deklarujesz zmienną obiektu, spróbuj użyć typu określonej klasy, na przykład <xref:System.OperatingSystem>, zamiast ogólnych `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="ff822-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="ff822-128">Należy również użyć najbardziej odpowiednią klasę dostępne, takich jak <xref:System.Windows.Forms.TextBox> zamiast <xref:System.Windows.Forms.Control>, dzięki czemu można uzyskać dostęp, jego właściwości i metod.</span><span class="sxs-lookup"><span data-stu-id="ff822-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="ff822-129">Zazwyczaj można używać **klasy** listy w **przeglądarki obiektów** można znaleźć nazwy dostępnych klas.</span><span class="sxs-lookup"><span data-stu-id="ff822-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
- <span data-ttu-id="ff822-130">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="ff822-130">**Widening.**</span></span> <span data-ttu-id="ff822-131">Wszystkie typy danych i wszystkie typy referencyjne mogą zostać poszerzone do `Object` typu danych.</span><span class="sxs-lookup"><span data-stu-id="ff822-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="ff822-132">Oznacza to, że można przekonwertować dowolnego typu do `Object` nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="ff822-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
     <span data-ttu-id="ff822-133">Jednak po konwersji między typami wartości i `Object`, Visual Basic wykonuje operacje o nazwie *pakowania* i *Rozpakowywanie*, udostępniają wykonywania wolniej.</span><span class="sxs-lookup"><span data-stu-id="ff822-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
- <span data-ttu-id="ff822-134">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="ff822-134">**Type Characters.**</span></span> <span data-ttu-id="ff822-135">`Object` nie ma znak literalny typu lub znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="ff822-135">`Object` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="ff822-136">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="ff822-136">**Framework Type.**</span></span> <span data-ttu-id="ff822-137">Odpowiedni typ w .NET Framework jest <xref:System.Object?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="ff822-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff822-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff822-138">Example</span></span>  
 <span data-ttu-id="ff822-139">W poniższym przykładzie pokazano `Object` zmiennej wskazuje na wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff822-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff822-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff822-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="ff822-141">Typy danych</span><span class="sxs-lookup"><span data-stu-id="ff822-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="ff822-142">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="ff822-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="ff822-143">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="ff822-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="ff822-144">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="ff822-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="ff822-145">Instrukcje: Określanie, czy dwa obiekty są powiązane</span><span class="sxs-lookup"><span data-stu-id="ff822-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="ff822-146">Instrukcje: Określanie, czy dwa obiekty są jednakowe</span><span class="sxs-lookup"><span data-stu-id="ff822-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
