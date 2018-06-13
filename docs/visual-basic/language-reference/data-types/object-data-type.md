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
ms.openlocfilehash: e9b1da5a88c12e0d883c3afe63be98c3fa3e9173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591631"
---
# <a name="object-data-type"></a><span data-ttu-id="1f3f8-102">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="1f3f8-102">Object Data Type</span></span>
<span data-ttu-id="1f3f8-103">Przechowuje adresy, które odwołują się do obiektów.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="1f3f8-104">Można przypisać do dowolnego typu odwołanie (ciąg, tablic, klasy lub interfejsu) `Object` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="1f3f8-105">`Object` Zmiennej znajdują się dane dowolnego typu wartość (numeryczną, `Boolean`, `Char`, `Date`, struktury lub wyliczenia).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f3f8-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f3f8-106">Remarks</span></span>  
 <span data-ttu-id="1f3f8-107">`Object` Danych dowolnego typu danych, w tym wszystkie wystąpienia obiektu aplikacja rozpoznaje może wskazywać typ danych.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="1f3f8-108">Użyj `Object` Jeśli nie znasz w czasie kompilacji, jakie dane typu zmienną może wskazywać.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="1f3f8-109">Wartość domyślna `Object` jest `Nothing` (odwołanie o wartości null).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="1f3f8-110">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1f3f8-110">Data Types</span></span>  
 <span data-ttu-id="1f3f8-111">Można przypisać zmiennej, stałej lub wyrażenia typu danych do `Object` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="1f3f8-112">Można ustalić typu danych `Object` obecnie odnosi się zmienna, możesz użyć <xref:System.Type.GetTypeCode%2A> metody <xref:System.Type?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="1f3f8-113">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="1f3f8-114">`Object` — Typ danych jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="1f3f8-115">Jednak traktuje Visual Basic `Object` zmiennej jako typ wartości, gdy odwołuje się do danych typu wartości.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="1f3f8-116">Magazyn</span><span class="sxs-lookup"><span data-stu-id="1f3f8-116">Storage</span></span>  
 <span data-ttu-id="1f3f8-117">Niezależnie od typu danych odwołuje się do, `Object` zmiennej nie zawiera wartości danych sam, ale raczej wskaźnik do wartości.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="1f3f8-118">Zawsze używa czterech bajtów pamięci, ale nie obejmuje magazyn danych reprezentujący wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="1f3f8-119">Ze względu na kod, który używa wskaźnika do lokalizowania danych `Object` zawierający typy wartości zmiennych są nieco dłużej dostępu niż jawnie zmienne typu.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="1f3f8-120">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="1f3f8-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="1f3f8-121">**Zagadnienia dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="1f3f8-121">**Interop Considerations.**</span></span> <span data-ttu-id="1f3f8-122">Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typów wskaźnikowych w innych środowiskach nie są zgodne z programem Visual Basic `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
-   <span data-ttu-id="1f3f8-123">**Wydajność.**</span><span class="sxs-lookup"><span data-stu-id="1f3f8-123">**Performance.**</span></span> <span data-ttu-id="1f3f8-124">Zmienna zadeklarowana z `Object` typ jest wystarczająco elastyczny, aby zawierać odwołania do dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="1f3f8-125">Jednak po wywołaniu metody lub właściwości na przekazanie zmiennej, należy zawsze pociągnąć za sobą *późne wiązanie* (w czasie wykonywania).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="1f3f8-126">Aby wymusić *wczesne wiązanie* (w czasie kompilacji) i lepsza wydajność, zadeklarować zmiennej o nazwie określonej klasy lub rzutować go na typ danych.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="1f3f8-127">Deklaracja zmiennej obiektu, spróbuj użyć określonego typu klasy, na przykład <xref:System.OperatingSystem>, zamiast ogólnych `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="1f3f8-128">Należy korzystać z najbardziej określonej klasy dostępne, takich jak <xref:System.Windows.Forms.TextBox> zamiast <xref:System.Windows.Forms.Control>, dzięki czemu można uzyskać dostępu do jego właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="1f3f8-129">Zazwyczaj można używać **klasy** na liście **przeglądarki obiektów** można znaleźć nazwy klasy dostępne.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
-   <span data-ttu-id="1f3f8-130">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="1f3f8-130">**Widening.**</span></span> <span data-ttu-id="1f3f8-131">Wszystkie typy danych i wszystkie typy referencyjne rozszerzane `Object` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="1f3f8-132">Oznacza to, że można przekonwertować dowolnego typu do `Object` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
     <span data-ttu-id="1f3f8-133">Jednak po konwersji między typami wartości i `Object`, Visual Basic wykonuje operacje o nazwie *boxing* i *rozpakowującej*, udostępniają wykonywania wolniej.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
-   <span data-ttu-id="1f3f8-134">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="1f3f8-134">**Type Characters.**</span></span> <span data-ttu-id="1f3f8-135">`Object` nie ma znak literalny typu ani znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-135">`Object` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="1f3f8-136">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="1f3f8-136">**Framework Type.**</span></span> <span data-ttu-id="1f3f8-137">Danego typu w programie .NET Framework jest <xref:System.Object?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f3f8-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f3f8-138">Example</span></span>  
 <span data-ttu-id="1f3f8-139">Poniższy przykład przedstawia `Object` zmiennej wskazuje na wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f3f8-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f3f8-140">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="1f3f8-141">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1f3f8-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="1f3f8-142">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="1f3f8-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="1f3f8-143">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="1f3f8-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="1f3f8-144">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="1f3f8-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="1f3f8-145">Instrukcje: określanie, czy dwa obiekty są powiązane</span><span class="sxs-lookup"><span data-stu-id="1f3f8-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="1f3f8-146">Instrukcje: określanie, czy dwa obiekty są jednakowe</span><span class="sxs-lookup"><span data-stu-id="1f3f8-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
