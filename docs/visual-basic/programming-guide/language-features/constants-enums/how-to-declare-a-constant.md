---
title: 'Porady: deklarowanie stałej (Visual Basic)'
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
ms.openlocfilehash: ce45e4df7f74cd68bde0fb2adba10197a11edb1b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394317"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="15203-102">Porady: deklarowanie stałej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15203-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="15203-103">Możesz użyć `Const` instrukcję, aby zadeklarować stałą i określanie jego wartości.</span><span class="sxs-lookup"><span data-stu-id="15203-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="15203-104">Wartość, przez zadeklarowanie stałą, przypisać znaczącą nazwę.</span><span class="sxs-lookup"><span data-stu-id="15203-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="15203-105">Po zadeklarowaniu stałej nie można modyfikować ani przypisywana nowa wartość.</span><span class="sxs-lookup"><span data-stu-id="15203-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="15203-106">Możesz deklarować stałą w procedurze lub w sekcji deklaracji modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="15203-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="15203-107">Klasa lub stałe na poziomie struktury są `Private` domyślnie, ale może być także zadeklarowana jako `Public`, `Friend`, `Protected`, lub `Protected Friend` na odpowiedni poziom dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="15203-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="15203-108">Stała musi mieć poprawną nazwę symboliczną (zasady są takie same jak w przypadku tworzenia nazwy zmiennych) i wyrażenie złożone, liczbą lub ciągiem stałe i operatory (ale nie wywołań funkcji).</span><span class="sxs-lookup"><span data-stu-id="15203-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="15203-109">Aby zadeklarować — stała</span><span class="sxs-lookup"><span data-stu-id="15203-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="15203-110">Deklaracja, która zawiera specyfikator dostępu do zapisu `Const` — słowo kluczowe i wyrażenie, tak jak w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="15203-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     <span data-ttu-id="15203-111">Gdy [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off` i [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, należy jawnie zadeklarować stałą, określając typ danych (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, lub `String`).</span><span class="sxs-lookup"><span data-stu-id="15203-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="15203-112">Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, stałej można zadeklarować bez określania typu danych za pomocą `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="15203-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="15203-113">Kompilator Określa typ stałej z typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="15203-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="15203-114">Aby uzyskać więcej informacji, zobacz [stała i typy danych literału](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="15203-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="15203-115">Aby zadeklarować stałą, która ma typ danych podane jawnie</span><span class="sxs-lookup"><span data-stu-id="15203-115">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="15203-116">Zapis deklaracji, która obejmuje `As` — słowo kluczowe i jawne danych typu, jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="15203-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     <span data-ttu-id="15203-117">Można zadeklarować kilka stałych w jednym wierszu, mimo że kod jest bardziej czytelny, jeśli zadeklarujesz pojedynczej stałej dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="15203-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="15203-118">Jeśli możesz zadeklarować kilka stałych w jednym wierszu, muszą mieć ten sam poziom dostępu (`Public`, `Private`, `Friend`, `Protected`, lub `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="15203-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="15203-119">Aby zadeklarować kilka stałych w pojedynczym wierszu</span><span class="sxs-lookup"><span data-stu-id="15203-119">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="15203-120">Deklaracje oddzielać przecinkiem i spacją, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="15203-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="15203-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15203-121">See Also</span></span>  
 [<span data-ttu-id="15203-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="15203-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="15203-123">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="15203-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)  
 <span data-ttu-id="15203-124">[Stałe — Przegląd](constants-overview.md) [porady: deklarowanie stałej](how-to-declare-a-constant.md) [stałe zdefiniowane przez użytkownika](user-defined-constants.md) [typy danych stała i literał](constant-and-literal-data-types.md) [jak: Grupa Powiązanych wartości stałych](how-to-group-related-constant-values-together.md) [Enumerations — Przegląd](enumerations-overview.md) [porady: deklarowanie wyliczeń](how-to-declare-enumerations.md) [jak: odnoszą się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md) [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md) [porady: iterowanie za pomocą wyliczania](how-to-iterate-through-an-enumeration.md) [porady: Określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="15203-124">[Constants Overview](constants-overview.md) [How to: Declare A Constant](how-to-declare-a-constant.md) [User-Defined Constants](user-defined-constants.md) [Constant and Literal Data Types](constant-and-literal-data-types.md) [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md) [Enumerations Overview](enumerations-overview.md) [How to: Declare Enumerations](how-to-declare-enumerations.md) [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md) [Enumerations and Name Qualification](enumerations-and-name-qualification.md) [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md) [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md) [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 [<span data-ttu-id="15203-125">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="15203-125">Enumerations Overview</span></span>](enumerations-overview.md)  
 [<span data-ttu-id="15203-126">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="15203-126">Constants Overview</span></span>](constants-overview.md)  
 [<span data-ttu-id="15203-127">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="15203-127">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)  
 [<span data-ttu-id="15203-128">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="15203-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)  
 [<span data-ttu-id="15203-129">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="15203-129">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="15203-130">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="15203-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
