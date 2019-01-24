---
title: Definicja typu anonimowego (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 9cb03eab00033c3d08b51de7524e9489198d6d76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678404"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="8a280-102">Definicja typu anonimowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a280-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="8a280-103">W odpowiedzi na deklarację wystąpienia typu anonimowego kompilator utworzy nową definicję klasy, która zawiera określone właściwości typu.</span><span class="sxs-lookup"><span data-stu-id="8a280-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="8a280-104">Kod wygenerowany przez kompilator</span><span class="sxs-lookup"><span data-stu-id="8a280-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="8a280-105">Dla następujących definicji `product`, kompilator utworzy nową definicję klasy, który zawiera właściwości `Name`, `Price`, i `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="8a280-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 <span data-ttu-id="8a280-106">Definicja klasy zawiera podobne do następujących definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a280-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="8a280-107">Zwróć uwagę, że ma nie `Set` metody dla właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="8a280-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="8a280-108">Wartości właściwości klucza są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="8a280-108">The values of key properties are read-only.</span></span>  
  
```vb  
Public Class $Anonymous1  
    Private _name As String  
    Private _price As Double  
    Private _onHand As Integer  
     Public ReadOnly Property Name() As String  
        Get  
            Return _name  
        End Get  
    End Property  
  
    Public ReadOnly Property Price() As Double  
        Get  
            Return _price  
        End Get  
    End Property  
  
    Public Property OnHand() As Integer  
        Get  
            Return _onHand  
        End Get  
        Set(ByVal Value As Integer)  
            _onHand = Value  
        End Set  
    End Property  
  
End Class  
```  
  
 <span data-ttu-id="8a280-109">Ponadto definicje typów anonimowych zawierać konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="8a280-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="8a280-110">Konstruktory, które są wymagane parametry nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="8a280-110">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="8a280-111">Jeśli deklaracja typu anonimowego zawiera co najmniej jedną właściwość klucza, definicja typu zastępuje trzech członków dziedziczonych po elemencie <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="8a280-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="8a280-112">Jeśli nie właściwości klucza nie został zadeklarowany, tylko <xref:System.Object.ToString%2A> zostanie zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="8a280-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="8a280-113">Zastąpienia są dostępne następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="8a280-113">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="8a280-114">`Equals` Zwraca `True` czy dwa wystąpienia typu anonimowego są tego samego wystąpienia, czy są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="8a280-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="8a280-115">Mają one taką samą liczbę właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a280-115">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="8a280-116">Właściwości są deklarowane w tej samej kolejności, przy użyciu tych samych nazw i wywnioskować takie same typy.</span><span class="sxs-lookup"><span data-stu-id="8a280-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="8a280-117">Nazwa porównania nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="8a280-117">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="8a280-118">Co najmniej jedna z właściwości jest właściwość klucza i `Key` — słowo kluczowe jest stosowany do tej samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a280-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="8a280-119">Zwraca porównania parom odpowiednie właściwości klucza `True`.</span><span class="sxs-lookup"><span data-stu-id="8a280-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="8a280-120">Na przykład w poniższych przykładach `Equals` zwraca `True` tylko w przypadku `employee01` i `employee08`.</span><span class="sxs-lookup"><span data-stu-id="8a280-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="8a280-121">Komentarz przed każdy wiersz określa przyczyny, dlaczego nie pasuje nowe wystąpienie `employee01`.</span><span class="sxs-lookup"><span data-stu-id="8a280-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   <span data-ttu-id="8a280-122">`GetHashcode` zawiera unikatowy odpowiednio algorytm GetHashCode.</span><span class="sxs-lookup"><span data-stu-id="8a280-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="8a280-123">Algorytm używa tylko właściwości klucza do Oblicz wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="8a280-123">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="8a280-124">`ToString` Zwraca ciąg wartości właściwości połączonych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8a280-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="8a280-125">Zarówno klucz, jak i właściwości klucza nie są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="8a280-125">Both key and non-key properties are included.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 <span data-ttu-id="8a280-126">Jawnie nazwane właściwości typu anonimowego nie może powodować konflikt z tych metod wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="8a280-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="8a280-127">Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`, lub `.ToString` nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a280-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="8a280-128">Definicje typu anonimowego, które obejmują co najmniej jednej właściwości klucza również implementują <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu, gdzie `T` to rodzaj typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="8a280-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a280-129">Deklaracjach typu anonimowego utworzyć ten sam typ anonimowy, tylko wtedy, gdy występują one w tym samym zestawie, ich właściwości o tych samych nazwach wywnioskować takie same typy, właściwości są deklarowane w tej samej kolejności i te same właściwości są oznaczone jako właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="8a280-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a280-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a280-130">See also</span></span>
- [<span data-ttu-id="8a280-131">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="8a280-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="8a280-132">Instrukcje: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="8a280-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
