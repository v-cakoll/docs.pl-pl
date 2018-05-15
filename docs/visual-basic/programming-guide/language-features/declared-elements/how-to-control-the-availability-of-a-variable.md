---
title: 'Porady: kontrolowanie dostępności zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 27ee5d3405ea24c0754cffa85e9b89b2ac561e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="8e959-102">Porady: kontrolowanie dostępności zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e959-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="8e959-103">Kontrolowanie dostępności zmiennej, określając jego *poziom dostępu*.</span><span class="sxs-lookup"><span data-stu-id="8e959-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="8e959-104">Poziom dostępu określa, jaki kod ma uprawnienie do odczytu lub zapisu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8e959-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="8e959-105">*Zmienne Członkowskie* (zdefiniowane na poziomie modułu w i poza dowolnej procedury) domyślnie dostęp publiczny, co oznacza kodu, który można wyświetlić ich mogą uzyskiwać do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="8e959-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="8e959-106">Można to zmienić, określając modyfikatora dostępu.</span><span class="sxs-lookup"><span data-stu-id="8e959-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="8e959-107">*Zmienne lokalne* (zdefiniowany wewnątrz procedury) nominalnie mają dostęp publiczny, mimo że tylko kodu w ramach ich procedury mogą uzyskiwać do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="8e959-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="8e959-108">Nie można zmienić poziom dostępu do zmiennej lokalnej, ale można zmienić poziom dostępu tej procedury, która go zawiera.</span><span class="sxs-lookup"><span data-stu-id="8e959-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="8e959-109">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8e959-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="8e959-110">Prywatne i publiczne dostępu</span><span class="sxs-lookup"><span data-stu-id="8e959-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="8e959-111">Aby zmienna dostępny tylko w obrębie swojego modułu, klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="8e959-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="8e959-112">Miejsce [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="8e959-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="8e959-113">Obejmują [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8e959-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="8e959-114">Można odczytu lub zapisu do zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, ale nie z poza nią.</span><span class="sxs-lookup"><span data-stu-id="8e959-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="8e959-115">Aby udostępnić zmienną z kodu, który może go wyświetlać</span><span class="sxs-lookup"><span data-stu-id="8e959-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="8e959-116">Dla zmiennej członkowskiej, umieść `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="8e959-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="8e959-117">Obejmują [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8e959-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="8e959-118">Można odczytu lub zapisu do zmiennej kodu, który współdziała z tym zestawem.</span><span class="sxs-lookup"><span data-stu-id="8e959-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="8e959-119">—lub—</span><span class="sxs-lookup"><span data-stu-id="8e959-119">-or-</span></span>  
  
1.  <span data-ttu-id="8e959-120">Do zmiennej lokalnej, umieść `Dim` instrukcji dla zmiennej wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="8e959-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="8e959-121">Nie dołączaj `Public` — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8e959-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="8e959-122">Można odczytu lub zapisu do zmiennej z dowolnego miejsca w ramach procedury, ale nie z poza nią.</span><span class="sxs-lookup"><span data-stu-id="8e959-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="8e959-123">Protected Friend dostępu i</span><span class="sxs-lookup"><span data-stu-id="8e959-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="8e959-124">Można ograniczyć poziom dostępu do zmiennej do swojej klasy i wszystkie klasy pochodne, lub jego zestaw.</span><span class="sxs-lookup"><span data-stu-id="8e959-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="8e959-125">Można również określić Unii tych ograniczeń, który zezwala na dostęp z kodu w dowolnej klasy pochodnej lub w innym miejscu, w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="8e959-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="8e959-126">Określ ten Unii łącząc `Protected` i `Friend` słów kluczowych w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8e959-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="8e959-127">Aby zmienna dostępny tylko w obrębie swojej klasy i wszystkie klasy pochodne</span><span class="sxs-lookup"><span data-stu-id="8e959-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="8e959-128">Miejsce `Dim` instrukcji dla zmiennej wewnątrz klasy, ale poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="8e959-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="8e959-129">Obejmują [chronione](../../../../visual-basic/language-reference/modifiers/protected.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8e959-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="8e959-130">Można odczytu lub zapisu do zmiennej z dowolnego miejsca w klasie, a także z poziomu dowolnej klasy pochodnej, ale nie z poza dowolnej klasy w łańcuchu pochodnym.</span><span class="sxs-lookup"><span data-stu-id="8e959-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="8e959-131">Aby zmienna dostępny tylko w obrębie tego samego zestawu</span><span class="sxs-lookup"><span data-stu-id="8e959-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="8e959-132">Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="8e959-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="8e959-133">Obejmują [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8e959-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="8e959-134">Można odczytu lub zapisu do zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, a także z dowolnego kodu, w tym samym zestawie, ale nie z poza zestaw.</span><span class="sxs-lookup"><span data-stu-id="8e959-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e959-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e959-135">Example</span></span>  
 <span data-ttu-id="8e959-136">W poniższym przykładzie przedstawiono deklaracje zmiennych o `Public`, `Protected`, `Friend`, `Protected Friend`, i `Private` poziomy dostępu.</span><span class="sxs-lookup"><span data-stu-id="8e959-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="8e959-137">Należy pamiętać, że w przypadku `Dim` instrukcji określa poziom dostępu, nie musisz uwzględnić `Dim` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8e959-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="8e959-138">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="8e959-138">.NET Framework Security</span></span>  
 <span data-ttu-id="8e959-139">Bardziej restrykcyjne poziom dostępu do zmiennej z niego korzystać im mniejsza ryzyko, które złośliwy kod może wykonać niewłaściwy.</span><span class="sxs-lookup"><span data-stu-id="8e959-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e959-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e959-140">See Also</span></span>  
 [<span data-ttu-id="8e959-141">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e959-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="8e959-142">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8e959-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="8e959-143">Public</span><span class="sxs-lookup"><span data-stu-id="8e959-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="8e959-144">Protected</span><span class="sxs-lookup"><span data-stu-id="8e959-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="8e959-145">Friend</span><span class="sxs-lookup"><span data-stu-id="8e959-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="8e959-146">Private</span><span class="sxs-lookup"><span data-stu-id="8e959-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
