---
title: 'Instrukcje: deklarowanie wyliczeń'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: c8f228c205c93adf7f2f555dc840a7daac61950b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414456"
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="ccd5d-102">Porady: deklarowanie wyliczeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccd5d-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="ccd5d-103">Wyliczenie można utworzyć przy użyciu `Enum` instrukcji w sekcji deklaracji klasy lub modułu.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="ccd5d-104">Nie można zadeklarować wyliczenia w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="ccd5d-105">Aby określić odpowiedni poziom dostępu, użyj,, `Private` `Protected` `Friend` , lub `Public` .</span><span class="sxs-lookup"><span data-stu-id="ccd5d-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="ccd5d-106">`Enum`Typ ma nazwę, typ podstawowy i zestaw pól, z których każdy reprezentuje stałą.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="ccd5d-107">Nazwa musi być prawidłowym kwalifikatorem Visual Basic platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="ccd5d-108">Typ podstawowy musi być jednym z typów całkowitych — `Byte` , `Short` , `Long` lub `Integer` .</span><span class="sxs-lookup"><span data-stu-id="ccd5d-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="ccd5d-109">Wartość domyślna to `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-109">`Integer` is the default.</span></span> <span data-ttu-id="ccd5d-110">Wyliczenia są zawsze silnie wpisane i nie mogą być zamienne z typami liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="ccd5d-111">Wyliczenia nie mogą mieć wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="ccd5d-112">Jeśli Wyliczenie ma przypisaną wartość zmiennoprzecinkową z `Option Strict On` , wynik błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="ccd5d-113">Jeśli `Option Strict` jest `Off` , wartość jest automatycznie konwertowana na `Enum` Typ.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="ccd5d-114">Aby uzyskać informacje o nazwach i sposobie używania `Imports` instrukcji w celu niepotrzebnej kwalifikacji nazwy, zobacz [wyliczenia i kwalifikowanie nazw](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="ccd5d-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="ccd5d-115">Aby zadeklarować Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ccd5d-115">To declare an enumeration</span></span>  
  
1. <span data-ttu-id="ccd5d-116">Napisz deklarację zawierającą poziom dostępu do kodu, `Enum` słowo kluczowe i prawidłową nazwę, jak w poniższych przykładach, z których każdy deklaruje inną `Enum` .</span><span class="sxs-lookup"><span data-stu-id="ccd5d-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. <span data-ttu-id="ccd5d-117">Zdefiniuj stałe w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="ccd5d-118">Domyślnie pierwsza stała w wyliczeniu jest inicjowana do `0` , a kolejne stałe są inicjowane do wartości jednej z więcej niż poprzednia stała.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="ccd5d-119">Na przykład następujące Wyliczenie, `Days` ,, zawiera stałą o nazwie `Sunday` z wartością `0` , stała o nazwie `Monday` z wartością `1` , stała o nazwie `Tuesday` z wartością `2` i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. <span data-ttu-id="ccd5d-120">Można jawnie przypisać wartości do stałych w wyliczeniu przy użyciu instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="ccd5d-121">Można przypisać dowolną liczbę całkowitą, łącznie z liczbami ujemnymi.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="ccd5d-122">Na przykład, możesz chcieć mieć stałe z wartościami mniejszymi od zera, aby reprezentować warunki błędu.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="ccd5d-123">W poniższym wyliczeniu, stała `Invalid` ma jawnie przypisaną wartość `–1` , a stała `Sunday` ma przypisaną wartość `0` .</span><span class="sxs-lookup"><span data-stu-id="ccd5d-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="ccd5d-124">Ponieważ jest to pierwsza stała w wyliczeniu, `Saturday` również jest inicjowana do wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="ccd5d-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="ccd5d-125">Wartość `Monday` jest `1` (jedna większa niż wartość `Sunday` ); wartość `Tuesday` jest `2` i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="ccd5d-126">Aby zadeklarować Wyliczenie jako typ jawny</span><span class="sxs-lookup"><span data-stu-id="ccd5d-126">To declare an enumeration as an explicit type</span></span>  
  
- <span data-ttu-id="ccd5d-127">Określ typ wyliczenia przy użyciu `As` klauzuli, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ccd5d-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ccd5d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccd5d-128">See also</span></span>

- [<span data-ttu-id="ccd5d-129">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="ccd5d-129">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="ccd5d-130">Porady: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ccd5d-130">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="ccd5d-131">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ccd5d-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="ccd5d-132">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ccd5d-132">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="ccd5d-133">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="ccd5d-133">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="ccd5d-134">Stałe — Przegląd</span><span class="sxs-lookup"><span data-stu-id="ccd5d-134">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="ccd5d-135">Stała i typy literałów</span><span class="sxs-lookup"><span data-stu-id="ccd5d-135">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="ccd5d-136">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ccd5d-136">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
