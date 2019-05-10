---
title: 'Instrukcje: Wyznaczyć, jakiego typu odnosi się zmienna obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 4ae73e6b3dec7864eb670bed67630b1cc96e5e61
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663549"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="49318-102">Instrukcje: Wyznaczyć, jakiego typu odnosi się zmienna obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49318-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>
<span data-ttu-id="49318-103">Zmienna obiektu zawiera wskaźnik do danych przechowywanych w różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="49318-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="49318-104">Typ danych można zmienić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="49318-104">The type of that data can change during run time.</span></span> <span data-ttu-id="49318-105">W każdej chwili możesz użyć <xref:System.Type.GetTypeCode%2A> metodę pozwala ustalić bieżącego typu run-time lub [TypeOf — Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) można sprawdzić, czy bieżący typu run-time jest zgodny z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="49318-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="49318-106">Można określić konkretny typ zmiennej obiektu obecnie odwołuje się do</span><span class="sxs-lookup"><span data-stu-id="49318-106">To determine the exact type an object variable currently refers to</span></span>  
  
1. <span data-ttu-id="49318-107">Na zmienną obiektu, wywołaj <xref:System.Object.GetType%2A> metodę, która pobierze <xref:System.Type?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="49318-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2. <span data-ttu-id="49318-108">Na <xref:System.Type?displayProperty=nameWithType> klasy, wywołaj metodę udostępnionego <xref:System.Type.GetTypeCode%2A> można pobrać <xref:System.TypeCode> wartość wyliczenia typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="49318-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     <span data-ttu-id="49318-109">Możesz przetestować <xref:System.TypeCode> wartość wyliczenia dla jednego z tych elementów członkowskich wyliczenia są interesujące, takie jak `Double`.</span><span class="sxs-lookup"><span data-stu-id="49318-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="49318-110">Aby określić, czy obiekt jest zgodny z określonym typem Typ zmiennej</span><span class="sxs-lookup"><span data-stu-id="49318-110">To determine whether an object variable's type is compatible with a specified type</span></span>  
  
- <span data-ttu-id="49318-111">Użyj `TypeOf` operatora w połączeniu z [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) do testowania obiekt z `TypeOf`... `Is` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49318-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     <span data-ttu-id="49318-112">`TypeOf`... `Is` zwraca wyrażenie `True` Jeśli obiekt środowiska wykonawczego typ jest zgodny z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="49318-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>  
  
     <span data-ttu-id="49318-113">Dla zgodności kryterium zależy od tego, czy określony typ jest klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="49318-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="49318-114">Ogólnie rzecz biorąc typy są zgodne, jeśli obiekt jest taki sam jak, dziedziczy lub implementuje określonego typu.</span><span class="sxs-lookup"><span data-stu-id="49318-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="49318-115">Aby uzyskać więcej informacji, zobacz [TypeOf — Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="49318-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49318-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="49318-116">Compiling the Code</span></span>  
 <span data-ttu-id="49318-117">Należy pamiętać, że określony typ nie może być zmiennej lub wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49318-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="49318-118">Musi to być nazwa zdefiniowanego typu, takich jak klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="49318-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="49318-119">Obejmuje to typy wewnętrzne takie jak `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="49318-119">This includes intrinsic types such as `Integer` and `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49318-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49318-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="49318-121">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="49318-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="49318-122">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="49318-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="49318-123">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="49318-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
