---
title: 'Porady: określanie, do jakiego typu odnosi się zmienna obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 0dfd4ed87b65f536802ae71cbc3de41e1c4f83af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651317"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="b3574-102">Porady: określanie, do jakiego typu odnosi się zmienna obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3574-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>
<span data-ttu-id="b3574-103">Zmienna obiektu zawiera wskaźnik do danych przechowywanych w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="b3574-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="b3574-104">Typ danych można zmienić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b3574-104">The type of that data can change during run time.</span></span> <span data-ttu-id="b3574-105">W dowolnym momencie można użyć <xref:System.Type.GetTypeCode%2A> metody w celu określenia bieżącego typu czasu wykonywania, lub [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) można sprawdzić, czy bieżący typu run-time jest zgodny z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="b3574-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="b3574-106">W celu określenia dokładnie typu zmienną obiektu obecnie odwołuje się do</span><span class="sxs-lookup"><span data-stu-id="b3574-106">To determine the exact type an object variable currently refers to</span></span>  
  
1.  <span data-ttu-id="b3574-107">Zmiennej obiektu wywołania <xref:System.Object.GetType%2A> metoda pobierania <xref:System.Type?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3574-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <span data-ttu-id="b3574-108">Na <xref:System.Type?displayProperty=nameWithType> klasy, należy wywołać metodę udostępnionego <xref:System.Type.GetTypeCode%2A> można pobrać <xref:System.TypeCode> wartość wyliczenia dla typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3574-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     <span data-ttu-id="b3574-109">Możesz przetestować <xref:System.TypeCode> wartość wyliczenia z dowolną wskazaną wyliczane elementy Członkowskie mogą być przydatne, takich jak `Double`.</span><span class="sxs-lookup"><span data-stu-id="b3574-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="b3574-110">Aby określić, czy obiekt jest zgodny z określonym typem Typ zmiennej</span><span class="sxs-lookup"><span data-stu-id="b3574-110">To determine whether an object variable's type is compatible with a specified type</span></span>  
  
-   <span data-ttu-id="b3574-111">Użyj `TypeOf` operatora w połączeniu z [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) do testowania obiektu o `TypeOf`... `Is` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b3574-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     <span data-ttu-id="b3574-112">`TypeOf`... `Is` zwraca wyrażenie `True` Jeśli obiektu środowiska wykonawczego typ jest zgodny z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="b3574-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>  
  
     <span data-ttu-id="b3574-113">Kryterium zgodności zależy od tego, czy określony typ jest klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b3574-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="b3574-114">Ogólnie rzecz biorąc typy są zgodne, jeśli obiekt jest taki sam typ jak dziedziczy i implementuje określonego typu.</span><span class="sxs-lookup"><span data-stu-id="b3574-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="b3574-115">Aby uzyskać więcej informacji, zobacz [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b3574-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3574-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b3574-116">Compiling the Code</span></span>  
 <span data-ttu-id="b3574-117">Należy pamiętać, że określony typ nie może być zmiennej lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b3574-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="b3574-118">Musi to być nazwa zdefiniowanego typu, takich jak klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b3574-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="b3574-119">Obejmuje to typy wewnętrzne takich jak `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="b3574-119">This includes intrinsic types such as `Integer` and `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3574-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3574-120">See Also</span></span>  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [<span data-ttu-id="b3574-121">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="b3574-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="b3574-122">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="b3574-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="b3574-123">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="b3574-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
