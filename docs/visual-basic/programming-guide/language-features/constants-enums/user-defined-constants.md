---
title: Stałe zdefiniowane przez użytkownika
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 194a420b3749ca5c858a65c07b8c164287c1582a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354008"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="32755-102">Stałe zdefiniowane przez użytkownika (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32755-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="32755-103">Stała jest zrozumiałą nazwą, która przyjmuje miejsce liczby lub ciągu, który nie jest zmieniany.</span><span class="sxs-lookup"><span data-stu-id="32755-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="32755-104">Stałe wartości magazynu, których nazwa to oznacza, pozostają stałe przez cały czas wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32755-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="32755-105">Możesz użyć stałych, które są zdefiniowane przez kontrolki lub składniki, z którymi pracujesz, lub możesz utworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="32755-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="32755-106">Utworzone przez Ciebie stałe są określane jako *zdefiniowane przez użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="32755-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="32755-107">Można zadeklarować stałą za pomocą instrukcji `Const`, korzystając z tych samych wytycznych dotyczących tworzenia nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="32755-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="32755-108">Jeśli `Option Strict` jest `On`, należy jawnie zadeklarować typ stałej.</span><span class="sxs-lookup"><span data-stu-id="32755-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="32755-109">Użycie instrukcji const</span><span class="sxs-lookup"><span data-stu-id="32755-109">Const Statement Usage</span></span>  
 <span data-ttu-id="32755-110">Instrukcja `Const` może reprezentować liczbę matematyczną lub datę/godzinę:</span><span class="sxs-lookup"><span data-stu-id="32755-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="32755-111">Można również zdefiniować `String` stałych:</span><span class="sxs-lookup"><span data-stu-id="32755-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="32755-112">Wyrażenie po prawej stronie znaku równości (`=`) jest często ciągiem liczbowym lub literalnym, ale również może być wyrażeniem, które powoduje użycie liczby lub ciągu (chociaż wyrażenie nie może zawierać wywołań funkcji).</span><span class="sxs-lookup"><span data-stu-id="32755-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="32755-113">Można nawet definiować stałe pod względem wcześniej zdefiniowanych stałych:</span><span class="sxs-lookup"><span data-stu-id="32755-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="32755-114">Zakres stałych zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="32755-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="32755-115">Zakres instrukcji `Const` jest taki sam jak w przypadku zmiennej zadeklarowanej w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="32755-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="32755-116">Można określić zakres w dowolny z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="32755-116">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="32755-117">Aby utworzyć stałą, która istnieje tylko w ramach procedury, zadeklaruj ją w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="32755-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="32755-118">Aby utworzyć stałą dostępną dla wszystkich procedur w obrębie klasy, ale nie do żadnego kodu spoza tego modułu, zadeklaruj go w sekcji deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="32755-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="32755-119">Aby utworzyć stałą dostępną dla wszystkich elementów członkowskich zestawu, ale nie do klientów zewnętrznych zestawu, zadeklaruj ją przy użyciu słowa kluczowego `Friend` w sekcji deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="32755-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="32755-120">Aby utworzyć stałą dostępną w całej aplikacji, należy ją zadeklarować przy użyciu słowa kluczowego `Public` w sekcji deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="32755-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="32755-121">Aby uzyskać więcej informacji, zobacz [How to: DECLARE A stała](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="32755-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="32755-122">Unikanie odwołań cyklicznych</span><span class="sxs-lookup"><span data-stu-id="32755-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="32755-123">Ze względu na to, że stałe mogą być zdefiniowane w warunkach innych stałych, można przypadkowo utworzyć *cykl*lub odwołanie cykliczne między dwoma lub więcej stałych.</span><span class="sxs-lookup"><span data-stu-id="32755-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="32755-124">Cykl występuje, gdy istnieją co najmniej dwie stałe publiczne, z których każdy jest zdefiniowany w warunkach innych, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="32755-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="32755-125">Jeśli wystąpi cykl, Visual Basic generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="32755-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32755-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32755-126">See also</span></span>

- [<span data-ttu-id="32755-127">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="32755-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="32755-128">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="32755-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="32755-129">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="32755-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="32755-130">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="32755-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="32755-131">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="32755-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="32755-132">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="32755-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="32755-133">Instrukcje: deklarowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="32755-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="32755-134">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="32755-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="32755-135">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="32755-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
