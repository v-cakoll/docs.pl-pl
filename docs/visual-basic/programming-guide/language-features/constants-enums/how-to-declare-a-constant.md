---
title: 'Porady: deklarowanie stałej'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: ffaa98f6af3d4b276f5c0b1153841acdea0809d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414482"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="6b25d-102">Porady: deklarowanie stałej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b25d-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="6b25d-103">Użyj instrukcji, `Const` Aby zadeklarować stałą i ustawić jej wartość.</span><span class="sxs-lookup"><span data-stu-id="6b25d-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="6b25d-104">Deklarując stałą, należy przypisać do wartości nazwę zrozumiałą.</span><span class="sxs-lookup"><span data-stu-id="6b25d-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="6b25d-105">Po zadeklarowaniu stałej nie można jej modyfikować ani przypisywać nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="6b25d-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="6b25d-106">Należy zadeklarować stałą w ramach procedury lub w sekcji deklaracji modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="6b25d-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="6b25d-107">Stałe klasy lub struktury są `Private` Domyślnie, ale mogą być również deklarowane jako,, `Public` `Friend` `Protected` lub `Protected Friend` dla odpowiedniego poziomu dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="6b25d-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="6b25d-108">Stała musi mieć prawidłową nazwę symboliczną (reguły są takie same jak w przypadku tworzenia nazw zmiennych) i wyrażenie składające się ze stałych liczbowych lub ciągów oraz operatorów (ale bez wywołań funkcji).</span><span class="sxs-lookup"><span data-stu-id="6b25d-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="6b25d-109">Aby zadeklarować stałą</span><span class="sxs-lookup"><span data-stu-id="6b25d-109">To declare a constant</span></span>  
  
- <span data-ttu-id="6b25d-110">Napisz deklarację, która zawiera specyfikator dostępu, `Const` słowo kluczowe i wyrażenie, jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="6b25d-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="6b25d-111">Gdy [opcja wnioskowanie](../../../language-reference/statements/option-infer-statement.md) jest `Off` i [opcją Strict](../../../language-reference/statements/option-strict-statement.md) jest `On` , należy zadeklarować stałą jawnie przez określenie typu danych (,,,,,,,,, `Boolean` `Byte` `Char` `DateTime` `Decimal` `Double` `Integer` `Long` `Short` `Single` lub `String` ).</span><span class="sxs-lookup"><span data-stu-id="6b25d-111">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="6b25d-112">Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off` , można zadeklarować stałą bez określania typu danych z `As` klauzulą.</span><span class="sxs-lookup"><span data-stu-id="6b25d-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="6b25d-113">Kompilator określa typ stałej z typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6b25d-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="6b25d-114">Aby uzyskać więcej informacji, zobacz [typy danych stałej i literału](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="6b25d-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="6b25d-115">Aby zadeklarować stałą, która ma jawnie zadeklarowany typ danych</span><span class="sxs-lookup"><span data-stu-id="6b25d-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="6b25d-116">Napisz deklarację zawierającą `As` słowo kluczowe i jawny typ danych, jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="6b25d-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="6b25d-117">Można zadeklarować wiele stałych w pojedynczym wierszu, chociaż kod jest bardziej czytelny, Jeśli zadeklarujesz tylko jedną stałą na wiersz.</span><span class="sxs-lookup"><span data-stu-id="6b25d-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="6b25d-118">Jeśli zadeklarujesz wiele stałych w pojedynczym wierszu, muszą one mieć taki sam poziom dostępu ( `Public` , `Private` , `Friend` , `Protected` lub `Protected Friend` ).</span><span class="sxs-lookup"><span data-stu-id="6b25d-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="6b25d-119">Aby zadeklarować wiele stałych w pojedynczym wierszu</span><span class="sxs-lookup"><span data-stu-id="6b25d-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="6b25d-120">Oddziel deklaracje przecinkami i spacjami, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6b25d-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6b25d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b25d-121">See also</span></span>

- [<span data-ttu-id="6b25d-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b25d-122">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="6b25d-123">Stała i typy literałów</span><span class="sxs-lookup"><span data-stu-id="6b25d-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="6b25d-124">Stałe — Przegląd</span><span class="sxs-lookup"><span data-stu-id="6b25d-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="6b25d-125">Instrukcje: deklarowanie stałej</span><span class="sxs-lookup"><span data-stu-id="6b25d-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="6b25d-126">Stałe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="6b25d-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="6b25d-127">Stała i typy literałów</span><span class="sxs-lookup"><span data-stu-id="6b25d-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="6b25d-128">Porady: grupowanie związanych wartości stałych</span><span class="sxs-lookup"><span data-stu-id="6b25d-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="6b25d-129">Enumerations — Przegląd</span><span class="sxs-lookup"><span data-stu-id="6b25d-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="6b25d-130">Instrukcje: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="6b25d-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="6b25d-131">Porady: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6b25d-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="6b25d-132">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="6b25d-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="6b25d-133">Instrukcje: iterowanie za pomocą wyliczania</span><span class="sxs-lookup"><span data-stu-id="6b25d-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="6b25d-134">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6b25d-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="6b25d-135">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="6b25d-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="6b25d-136">Enumerations — Przegląd</span><span class="sxs-lookup"><span data-stu-id="6b25d-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="6b25d-137">Stałe — Przegląd</span><span class="sxs-lookup"><span data-stu-id="6b25d-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="6b25d-138">Instrukcje: deklarowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6b25d-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="6b25d-139">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="6b25d-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="6b25d-140">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b25d-140">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="6b25d-141">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6b25d-141">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
