---
title: 'Instrukcje: Kontrolowanie dostępności zmiennej (Visual Basic)'
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
ms.openlocfilehash: fb400b113e3f3305f5b724734b2bf9aa9425d03f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943354"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="ad3d4-102">Instrukcje: Kontrolowanie dostępności zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad3d4-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="ad3d4-103">Kontrolowanie dostępności zmiennej, określając jego *poziom dostępu*.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="ad3d4-104">Poziom dostępu decyduje o tym, jaki kod ma uprawnienie do odczytu lub zapisu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="ad3d4-105">*Zmienne Członkowskie* (zdefiniowany na poziomie modułu i na zewnątrz dowolnej procedury) domyślnie publicznym dostępem, który oznacza, że wszelki kod, który je wyświetlić mają do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="ad3d4-106">Można to zmienić, określając modyfikatora dostępu.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="ad3d4-107">*Zmienne lokalne* (zdefiniowane wewnątrz procedury) nominalnie ma dostęp publiczny, mimo że tylko kod w ramach ich procedury mają do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="ad3d4-108">Nie można zmienić poziomu dostępu do zmiennej lokalnej, ale można zmienić poziomu dostępu procedury, która go zawiera.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="ad3d4-109">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ad3d4-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="ad3d4-110">Dostęp do prywatnych i publicznych</span><span class="sxs-lookup"><span data-stu-id="ad3d4-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="ad3d4-111">Aby zmienna był dostępny tylko w obrębie jego modułu, klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="ad3d4-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="ad3d4-112">Miejsce [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zmiennej wewnątrz modułu, klasy lub struktury, ale poza programem dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="ad3d4-113">Obejmują [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ad3d4-114">Może odczytać lub zapisać zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, ale nie z poza nim.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="ad3d4-115">Aby udostępnić zmienną z dowolnego kodu, który można zobaczyć, jak to</span><span class="sxs-lookup"><span data-stu-id="ad3d4-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="ad3d4-116">Dla zmiennej składowej, umieść `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza programem dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="ad3d4-117">Obejmują [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ad3d4-118">Można odczytu lub zapisu do zmiennej wszelki kod, który współdziała z zestawu.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="ad3d4-119">—lub—</span><span class="sxs-lookup"><span data-stu-id="ad3d4-119">-or-</span></span>  
  
1. <span data-ttu-id="ad3d4-120">Dla zmiennej lokalnej, należy umieścić `Dim` instrukcji dla zmiennej wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="ad3d4-121">Nie dołączaj `Public` — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ad3d4-122">Może odczytać lub zapisać zmiennej z dowolnego miejsca, w ramach procedury, ale nie z poza nim.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="ad3d4-123">Chronione i dostępu przyjaznego</span><span class="sxs-lookup"><span data-stu-id="ad3d4-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="ad3d4-124">Można ograniczyć poziomu dostępu zmiennej, do swojej klasy i wszystkie klasy pochodne lub własnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="ad3d4-125">Można również określić sumę tych ograniczeń, która zezwala na dostęp z kodu w dowolnej klasy pochodnej lub w innym miejscu, w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="ad3d4-126">Należy określić ten Unii, łącząc `Protected` i `Friend` słów kluczowych w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="ad3d4-127">Aby zmienna był dostępny tylko w obrębie swojej klasy i wszystkie klasy pochodne</span><span class="sxs-lookup"><span data-stu-id="ad3d4-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="ad3d4-128">Miejsce `Dim` instrukcji dla zmiennej wewnątrz klasy, ale poza programem dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="ad3d4-129">Obejmują [chronione](../../../../visual-basic/language-reference/modifiers/protected.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ad3d4-130">Może odczytać lub zapisać zmiennej z dowolnego miejsca, w ramach klasy, a także z poziomu dowolnej klasy pochodnej z niego, ale nie z poza dowolnej klasy w łańcuchu pochodnym.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="ad3d4-131">Aby zmienna był dostępny tylko w obrębie tego samego zestawu</span><span class="sxs-lookup"><span data-stu-id="ad3d4-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="ad3d4-132">Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza programem dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="ad3d4-133">Obejmują [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ad3d4-134">Może odczytać lub zapisać zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, a także z dowolnego kodu, w tym samym zestawie, ale nie z spoza zestawu.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad3d4-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad3d4-135">Example</span></span>  
 <span data-ttu-id="ad3d4-136">W poniższym przykładzie pokazano deklaracje zmiennych z `Public`, `Protected`, `Friend`, `Protected Friend`, i `Private` poziomy dostępu.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="ad3d4-137">Należy pamiętać, że w przypadku `Dim` Instrukcja określa poziom dostępu, nie musisz uwzględnić `Dim` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="ad3d4-138">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad3d4-138">.NET Framework Security</span></span>  
 <span data-ttu-id="ad3d4-139">Bardziej restrykcyjny poziom dostępu do zmiennej, z niego korzystać mniejszy szanse, że złośliwy kod może być niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="ad3d4-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3d4-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad3d4-140">See also</span></span>

- [<span data-ttu-id="ad3d4-141">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad3d4-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="ad3d4-142">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ad3d4-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="ad3d4-143">Public</span><span class="sxs-lookup"><span data-stu-id="ad3d4-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="ad3d4-144">Protected</span><span class="sxs-lookup"><span data-stu-id="ad3d4-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="ad3d4-145">Friend</span><span class="sxs-lookup"><span data-stu-id="ad3d4-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="ad3d4-146">Private</span><span class="sxs-lookup"><span data-stu-id="ad3d4-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
