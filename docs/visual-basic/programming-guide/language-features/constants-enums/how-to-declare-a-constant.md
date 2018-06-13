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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649740"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="7f20c-102">Porady: deklarowanie stałej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f20c-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="7f20c-103">Możesz użyć `Const` instrukcji deklarowanie stałej i ustaw jej wartość.</span><span class="sxs-lookup"><span data-stu-id="7f20c-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="7f20c-104">Przez deklarowanie stałej, nazwę opisową przypisać wartość.</span><span class="sxs-lookup"><span data-stu-id="7f20c-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="7f20c-105">Po zadeklarowaniu stałą, nie można zmodyfikować ani przypisywana nowa wartość.</span><span class="sxs-lookup"><span data-stu-id="7f20c-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="7f20c-106">Należy zadeklarować stała w procedurze lub w sekcji deklaracji modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="7f20c-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="7f20c-107">Klasa lub stałe na poziomie struktury są `Private` domyślnie, ale może również być zadeklarowany jako `Public`, `Friend`, `Protected`, lub `Protected Friend` na odpowiedni poziom dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="7f20c-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="7f20c-108">Stała musi mieć poprawną nazwę symboliczną (reguły są takie same jak do tworzenia nazwy zmiennych) i wyrażeń składają numeryczny lub ciąg stałe i operatory (ale nie wywołania funkcji).</span><span class="sxs-lookup"><span data-stu-id="7f20c-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="7f20c-109">Deklarowanie stałej</span><span class="sxs-lookup"><span data-stu-id="7f20c-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="7f20c-110">Zapis deklaracji, która obejmuje specyfikator dostępu `Const` — słowo kluczowe i wyrażenia, na przykład:</span><span class="sxs-lookup"><span data-stu-id="7f20c-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     <span data-ttu-id="7f20c-111">Gdy [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off` i [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, musisz jawnie zadeklarować stałą przez określenie typu danych (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, lub `String`).</span><span class="sxs-lookup"><span data-stu-id="7f20c-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="7f20c-112">Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, mogą zadeklarować stałą bez określania typu danych z `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7f20c-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="7f20c-113">Kompilator Określa typ stałej z typem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7f20c-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="7f20c-114">Aby uzyskać więcej informacji, zobacz [stała i typy danych literału](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="7f20c-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="7f20c-115">Aby zadeklarować o typie danych jawnie określonej stałej</span><span class="sxs-lookup"><span data-stu-id="7f20c-115">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="7f20c-116">Zapis deklaracji, która obejmuje `As` — słowo kluczowe i jawnych danych, wpisz na przykład:</span><span class="sxs-lookup"><span data-stu-id="7f20c-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     <span data-ttu-id="7f20c-117">Można zadeklarować wiele stałych w jednym wierszu, mimo że kod jest bardziej przejrzysta zadeklarować pojedynczej stałej w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="7f20c-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="7f20c-118">W przypadku wielu stałe w jednym wierszu, ich muszą mieć ten sam poziom dostępu (`Public`, `Private`, `Friend`, `Protected`, lub `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="7f20c-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="7f20c-119">Aby zadeklarować wiele stałych w jednym wierszu</span><span class="sxs-lookup"><span data-stu-id="7f20c-119">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="7f20c-120">Deklaracje oddzielać przecinkiem i spacją, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7f20c-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7f20c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f20c-121">See Also</span></span>  
 [<span data-ttu-id="7f20c-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7f20c-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="7f20c-123">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="7f20c-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)  
 <span data-ttu-id="7f20c-124">[Stałe — Przegląd](constants-overview.md) [porady: deklarowanie stałej](how-to-declare-a-constant.md) [stałe zdefiniowane przez użytkownika](user-defined-constants.md) [stała i typy literałów](constant-and-literal-data-types.md) [porady: Grupa Związanych wartości stałych](how-to-group-related-constant-values-together.md) [Enumerations — Przegląd](enumerations-overview.md) [porady: deklarowanie wyliczeń](how-to-declare-enumerations.md) [porady: odwołuje się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md) [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md) [porady: iterowanie za pomocą wyliczenie](how-to-iterate-through-an-enumeration.md) [porady: Określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="7f20c-124">[Constants Overview](constants-overview.md) [How to: Declare A Constant](how-to-declare-a-constant.md) [User-Defined Constants](user-defined-constants.md) [Constant and Literal Data Types](constant-and-literal-data-types.md) [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md) [Enumerations Overview](enumerations-overview.md) [How to: Declare Enumerations](how-to-declare-enumerations.md) [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md) [Enumerations and Name Qualification](enumerations-and-name-qualification.md) [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md) [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md) [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 [<span data-ttu-id="7f20c-125">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="7f20c-125">Enumerations Overview</span></span>](enumerations-overview.md)  
 [<span data-ttu-id="7f20c-126">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="7f20c-126">Constants Overview</span></span>](constants-overview.md)  
 [<span data-ttu-id="7f20c-127">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="7f20c-127">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)  
 [<span data-ttu-id="7f20c-128">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="7f20c-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)  
 [<span data-ttu-id="7f20c-129">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7f20c-129">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="7f20c-130">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7f20c-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
