---
title: 'Instrukcje: Deklarowanie stałej (Visual Basic)'
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
ms.openlocfilehash: b84afe4e354d4029bc61ba67bc93bd36a3430de4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610600"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="9b17e-102">Instrukcje: Deklarowanie stałej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b17e-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="9b17e-103">Możesz użyć `Const` instrukcję, aby zadeklarować stałą i określanie jego wartości.</span><span class="sxs-lookup"><span data-stu-id="9b17e-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="9b17e-104">Wartość, przez zadeklarowanie stałą, przypisać znaczącą nazwę.</span><span class="sxs-lookup"><span data-stu-id="9b17e-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="9b17e-105">Po zadeklarowaniu stałej nie można modyfikować ani przypisywana nowa wartość.</span><span class="sxs-lookup"><span data-stu-id="9b17e-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="9b17e-106">Możesz deklarować stałą w procedurze lub w sekcji deklaracji modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9b17e-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="9b17e-107">Klasa lub stałe na poziomie struktury są `Private` domyślnie, ale może być także zadeklarowana jako `Public`, `Friend`, `Protected`, lub `Protected Friend` na odpowiedni poziom dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="9b17e-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="9b17e-108">Stała musi mieć poprawną nazwę symboliczną (zasady są takie same jak w przypadku tworzenia nazwy zmiennych) i wyrażenie złożone, liczbą lub ciągiem stałe i operatory (ale nie wywołań funkcji).</span><span class="sxs-lookup"><span data-stu-id="9b17e-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="9b17e-109">Aby zadeklarować — stała</span><span class="sxs-lookup"><span data-stu-id="9b17e-109">To declare a constant</span></span>  
  
- <span data-ttu-id="9b17e-110">Deklaracja, która zawiera specyfikator dostępu do zapisu `Const` — słowo kluczowe i wyrażenie, tak jak w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="9b17e-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="9b17e-111">Gdy [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off` i [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, należy jawnie zadeklarować stałą, określając typ danych (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, lub `String`).</span><span class="sxs-lookup"><span data-stu-id="9b17e-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="9b17e-112">Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, stałej można zadeklarować bez określania typu danych za pomocą `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9b17e-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="9b17e-113">Kompilator Określa typ stałej z typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9b17e-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="9b17e-114">Aby uzyskać więcej informacji, zobacz [stała i typy danych literału](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="9b17e-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="9b17e-115">Aby zadeklarować stałą, która ma typ danych podane jawnie</span><span class="sxs-lookup"><span data-stu-id="9b17e-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="9b17e-116">Zapis deklaracji, która obejmuje `As` — słowo kluczowe i jawne danych typu, jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="9b17e-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="9b17e-117">Można zadeklarować kilka stałych w jednym wierszu, mimo że kod jest bardziej czytelny, jeśli zadeklarujesz pojedynczej stałej dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="9b17e-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="9b17e-118">Jeśli możesz zadeklarować kilka stałych w jednym wierszu, muszą mieć ten sam poziom dostępu (`Public`, `Private`, `Friend`, `Protected`, lub `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="9b17e-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="9b17e-119">Aby zadeklarować kilka stałych w pojedynczym wierszu</span><span class="sxs-lookup"><span data-stu-id="9b17e-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="9b17e-120">Deklaracje oddzielać przecinkiem i spacją, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b17e-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9b17e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b17e-121">See also</span></span>

- [<span data-ttu-id="9b17e-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9b17e-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="9b17e-123">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="9b17e-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="9b17e-124">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="9b17e-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="9b17e-125">Instrukcje: Deklarowanie stałej</span><span class="sxs-lookup"><span data-stu-id="9b17e-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="9b17e-126">Stałe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="9b17e-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="9b17e-127">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="9b17e-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="9b17e-128">Instrukcje: Grupowanie powiązanych ze sobą wartości stałych</span><span class="sxs-lookup"><span data-stu-id="9b17e-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="9b17e-129">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="9b17e-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="9b17e-130">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="9b17e-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="9b17e-131">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9b17e-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="9b17e-132">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="9b17e-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="9b17e-133">Instrukcje: Iterowanie za pomocą wyliczania</span><span class="sxs-lookup"><span data-stu-id="9b17e-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="9b17e-134">Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9b17e-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="9b17e-135">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="9b17e-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="9b17e-136">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="9b17e-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="9b17e-137">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="9b17e-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="9b17e-138">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="9b17e-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="9b17e-139">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="9b17e-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="9b17e-140">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9b17e-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="9b17e-141">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9b17e-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
