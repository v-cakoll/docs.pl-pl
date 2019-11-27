---
title: 'Porady: określanie, do jakiego typu odnosi się zmienna obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 9f9b89e2fea0bd69cba6d50fa1d1fb9cc3927685
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348616"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="80af1-102">Porady: określanie, do jakiego typu odnosi się zmienna obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80af1-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="80af1-103">Zmienna obiektu zawiera wskaźnik do danych, które są przechowywane w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="80af1-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="80af1-104">Typ tych danych może ulec zmianie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="80af1-104">The type of that data can change during run time.</span></span> <span data-ttu-id="80af1-105">W dowolnym momencie można użyć metody <xref:System.Type.GetTypeCode%2A>, aby określić bieżący typ uruchomieniowy lub [operator typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) , aby dowiedzieć się, czy bieżący typ czasu wykonywania jest zgodny z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="80af1-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="80af1-106">Aby określić dokładny typ, do którego odwołuje się zmienna obiektu</span><span class="sxs-lookup"><span data-stu-id="80af1-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="80af1-107">Na zmiennej obiektu Wywołaj metodę <xref:System.Object.GetType%2A>, aby pobrać obiekt <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80af1-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="80af1-108">W klasie <xref:System.Type?displayProperty=nameWithType> Wywołaj <xref:System.Type.GetTypeCode%2A> metody udostępnionej, aby pobrać <xref:System.TypeCode> wartość wyliczenia dla typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="80af1-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="80af1-109">Można testować <xref:System.TypeCode> wartość wyliczenia dla elementów członkowskich wyliczenia, które są istotne, takich jak `Double`.</span><span class="sxs-lookup"><span data-stu-id="80af1-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="80af1-110">Aby określić, czy typ zmiennej obiektu jest zgodny z określonym typem</span><span class="sxs-lookup"><span data-stu-id="80af1-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="80af1-111">Użyj operatora `TypeOf` w połączeniu z [operatorem is](../../../../visual-basic/language-reference/operators/is-operator.md) , aby przetestować obiekt za pomocą wyrażenia `TypeOf`...`Is`.</span><span class="sxs-lookup"><span data-stu-id="80af1-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="80af1-112">Wyrażenie `TypeOf`...`Is` zwraca `True`, jeśli typ czasu wykonywania obiektu jest zgodny z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="80af1-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="80af1-113">Kryterium zgodności zależy od tego, czy określony typ jest klasą, strukturą lub interfejsem.</span><span class="sxs-lookup"><span data-stu-id="80af1-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="80af1-114">Ogólnie rzecz biorąc, typy są zgodne, jeśli obiekt jest tego samego typu co, dziedziczy po lub implementuje określony typ.</span><span class="sxs-lookup"><span data-stu-id="80af1-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="80af1-115">Aby uzyskać więcej informacji, zobacz [operator typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="80af1-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="80af1-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80af1-116">Compiling the Code</span></span>

<span data-ttu-id="80af1-117">Należy zauważyć, że określony typ nie może być zmienną ani wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="80af1-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="80af1-118">Musi to być nazwa typu zdefiniowanego, na przykład klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="80af1-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="80af1-119">Obejmuje to typy wewnętrzne, takie jak `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="80af1-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="80af1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80af1-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="80af1-121">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="80af1-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="80af1-122">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="80af1-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="80af1-123">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="80af1-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
