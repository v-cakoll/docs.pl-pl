---
title: Definicja typu anonimowego (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8b5b7eba55d719c1482b7224ecffc78b776feb00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="d8fe8-102">Definicja typu anonimowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8fe8-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="d8fe8-103">W odpowiedzi na deklaracji wystąpienia typu anonimowego kompilator tworzy nową definicję klasy zawierający właściwości określonego typu.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="d8fe8-104">Kod wygenerowany przez kompilator</span><span class="sxs-lookup"><span data-stu-id="d8fe8-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="d8fe8-105">Dla następujących definicji `product`, kompilator tworzy nową definicję klasy, który zawiera właściwości `Name`, `Price`, i `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 <span data-ttu-id="d8fe8-106">Definicja klasy zawiera definicje właściwości podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="d8fe8-107">Należy zauważyć, że istnieje nie `Set` metody dla właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="d8fe8-108">Wartości właściwości klucza są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-108">The values of key properties are read-only.</span></span>  
  
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
  
 <span data-ttu-id="d8fe8-109">Ponadto definicji typu anonimowego zawierać konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="d8fe8-110">Konstruktory, które są wymagane parametry nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-110">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="d8fe8-111">Jeśli w deklaracji typu anonimowego zawiera co najmniej jedną właściwość klucza, definicja typu zastępuje trzy członków dziedziczonych po elemencie <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="d8fe8-112">Nie właściwości klucza jest zadeklarowana, tylko <xref:System.Object.ToString%2A> zostanie zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="d8fe8-113">Zastąpienia są dostępne następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="d8fe8-113">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="d8fe8-114">`Equals`Zwraca `True` czy dwa wystąpienia typu anonimowego są tego samego wystąpienia, czy są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="d8fe8-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="d8fe8-115">Mają one taką samą liczbę właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-115">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="d8fe8-116">Właściwości są zadeklarowane w tej samej kolejności, pod tą samą nazwą i wywnioskować takie same typy.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="d8fe8-117">Nazwa porównania nie jest rozróżniana.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-117">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="d8fe8-118">Co najmniej jedna z właściwości jest właściwością klucza i `Key` — słowo kluczowe jest stosowany do tej samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="d8fe8-119">Zwraca porównania każda para odpowiednie właściwości klucza `True`.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="d8fe8-120">Na przykład w poniższych przykładach `Equals` zwraca `True` tylko w przypadku `employee01` i `employee08`.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="d8fe8-121">Komentarz przed każdym wierszu określa przyczynę, dlaczego nowego wystąpienia nie pasuje `employee01`.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   <span data-ttu-id="d8fe8-122">`GetHashcode`zawiera unikatowy odpowiednio algorytmu GetHashCode.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="d8fe8-123">Algorytm używa tylko właściwości klucza można obliczyć skrótu.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-123">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="d8fe8-124">`ToString`Zwraca ciąg o wartości właściwości połączonych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="d8fe8-125">Zarówno klucz i niż właściwości klucza są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-125">Both key and non-key properties are included.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 <span data-ttu-id="d8fe8-126">Jawnie nazwane właściwości typu anonimowego nie powodują konflikt z tych metod wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="d8fe8-127">Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`, lub `.ToString` nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="d8fe8-128">Definicje typu anonimowego, które obejmują co najmniej jedna właściwość klucza również wdrożenie <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu, gdzie `T` to rodzaj typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8fe8-129">Deklaracje typu anonimowego tworzenia tego samego typu anonimowego tylko, jeśli występują one w tym samym zestawie, ich właściwości mają takie same nazwy i wywnioskować takie same typy właściwości są zadeklarowane w tej samej kolejności i takie same właściwości są oznaczone jako właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="d8fe8-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fe8-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8fe8-130">See Also</span></span>  
 [<span data-ttu-id="d8fe8-131">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="d8fe8-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="d8fe8-132">Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="d8fe8-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
