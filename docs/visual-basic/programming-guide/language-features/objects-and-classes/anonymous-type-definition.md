---
title: Definicja typu anonimowego
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: f8ac26577a7fbef865605a7ecf643fa733b2c2c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344917"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="d99ac-102">Definicja typu anonimowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d99ac-102">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="d99ac-103">W odpowiedzi na deklarację wystąpienia typu anonimowego kompilator tworzy nową definicję klasy, która zawiera określone właściwości dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="d99ac-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="d99ac-104">Kod wygenerowany przez kompilator</span><span class="sxs-lookup"><span data-stu-id="d99ac-104">Compiler-Generated Code</span></span>

<span data-ttu-id="d99ac-105">Dla następującej definicji `product`kompilator tworzy nową definicję klasy, która zawiera właściwości `Name`, `Price`i `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="d99ac-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="d99ac-106">Definicja klasy zawiera definicje właściwości podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="d99ac-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="d99ac-107">Należy zauważyć, że nie ma `Set` metody dla właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="d99ac-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="d99ac-108">Wartości właściwości klucza są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d99ac-108">The values of key properties are read-only.</span></span>

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

<span data-ttu-id="d99ac-109">Ponadto definicja typu anonimowego zawiera konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="d99ac-109">In addition, anonymous type definitions contain a parameterless constructor.</span></span> <span data-ttu-id="d99ac-110">Konstruktory wymagające parametrów są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="d99ac-110">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="d99ac-111">Jeśli deklaracja typu anonimowego zawiera co najmniej jedną właściwość klucza, definicja typu przesłania trzy składowe dziedziczone z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>i <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="d99ac-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="d99ac-112">Jeśli nie zadeklarowano żadnych właściwości klucza, tylko <xref:System.Object.ToString%2A> jest zastępowany.</span><span class="sxs-lookup"><span data-stu-id="d99ac-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="d99ac-113">Przesłonięcia zapewniają następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="d99ac-113">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="d99ac-114">`Equals` zwraca `True`, jeśli dwa wystąpienia typu anonimowego są tego samego wystąpienia lub spełniają następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="d99ac-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="d99ac-115">Mają tę samą liczbę właściwości.</span><span class="sxs-lookup"><span data-stu-id="d99ac-115">They have the same number of properties.</span></span>

  - <span data-ttu-id="d99ac-116">Właściwości są deklarowane w tej samej kolejności, z tymi samymi nazwami i tymi samymi typem wywnioskowanym.</span><span class="sxs-lookup"><span data-stu-id="d99ac-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="d99ac-117">W porównaniach nazw nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="d99ac-117">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="d99ac-118">Co najmniej jedna z właściwości jest właściwością klucza, a słowo kluczowe `Key` jest stosowane do tych samych właściwości.</span><span class="sxs-lookup"><span data-stu-id="d99ac-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="d99ac-119">Porównanie każdej odpowiadającej pary właściwości klucza zwraca `True`.</span><span class="sxs-lookup"><span data-stu-id="d99ac-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="d99ac-120">Na przykład w poniższych przykładach `Equals` zwraca `True` tylko dla `employee01` i `employee08`.</span><span class="sxs-lookup"><span data-stu-id="d99ac-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="d99ac-121">Komentarz przed każdym wierszem określa powód, dla którego nowe wystąpienie nie jest zgodne `employee01`.</span><span class="sxs-lookup"><span data-stu-id="d99ac-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="d99ac-122">`GetHashcode` zapewnia odpowiedni unikatowy algorytm GetHashCode.</span><span class="sxs-lookup"><span data-stu-id="d99ac-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="d99ac-123">Algorytm używa tylko właściwości klucza do obliczenia kodu skrótu.</span><span class="sxs-lookup"><span data-stu-id="d99ac-123">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="d99ac-124">`ToString` zwraca ciąg połączonych wartości właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d99ac-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="d99ac-125">Uwzględniane są zarówno właściwości klucza, jak i niebędących kluczami.</span><span class="sxs-lookup"><span data-stu-id="d99ac-125">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="d99ac-126">Właściwości jawnie nazwane typu anonimowego nie mogą powodować konfliktu z tymi wygenerowanymi metodami.</span><span class="sxs-lookup"><span data-stu-id="d99ac-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="d99ac-127">Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`lub `.ToString` do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="d99ac-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="d99ac-128">Definicje typu anonimowego, które obejmują co najmniej jedną właściwość klucza, również implementują interfejs <xref:System.IEquatable%601?displayProperty=nameWithType>, gdzie `T` jest typem typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="d99ac-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="d99ac-129">Deklaracje typu anonimowego tworzą ten sam typ anonimowy tylko wtedy, gdy występują w tym samym zestawie, ich właściwości mają takie same nazwy, jak te same wywnioskowane typy, właściwości są deklarowane w tej samej kolejności, a te same właściwości są oznaczane jako właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="d99ac-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="d99ac-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d99ac-130">See also</span></span>

- [<span data-ttu-id="d99ac-131">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="d99ac-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="d99ac-132">Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="d99ac-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
