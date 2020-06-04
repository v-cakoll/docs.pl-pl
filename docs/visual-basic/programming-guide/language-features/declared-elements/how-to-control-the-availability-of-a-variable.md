---
title: 'Porady: kontrolowanie dostępności zmiennej'
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
ms.openlocfilehash: 0bfa7fa2bdac4746827884c1dad62734c549a48e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357390"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="d69b6-102">Porady: kontrolowanie dostępności zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d69b6-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="d69b6-103">Możesz kontrolować dostępność zmiennej, określając jej *poziom dostępu*.</span><span class="sxs-lookup"><span data-stu-id="d69b6-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="d69b6-104">Poziom dostępu określa kod, który ma uprawnienia do odczytu lub zapisu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d69b6-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="d69b6-105">*Zmienne składowe* (zdefiniowane na poziomie modułu i poza każdą procedurę) domyślnie mają dostęp publiczny, co oznacza, że każdy kod, który może je zobaczyć, może uzyskać do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="d69b6-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="d69b6-106">Można to zmienić, określając modyfikator dostępu.</span><span class="sxs-lookup"><span data-stu-id="d69b6-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="d69b6-107">*Zmienne lokalne* (zdefiniowane wewnątrz procedury) mają nominalny dostęp publiczny, chociaż tylko kod w ramach procedury ma dostęp do nich.</span><span class="sxs-lookup"><span data-stu-id="d69b6-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="d69b6-108">Nie można zmienić poziomu dostępu zmiennej lokalnej, ale można zmienić poziom dostępu do procedury, która go zawiera.</span><span class="sxs-lookup"><span data-stu-id="d69b6-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="d69b6-109">Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d69b6-109">For more information, see [Access levels in Visual Basic](access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="d69b6-110">Dostęp prywatny i publiczny</span><span class="sxs-lookup"><span data-stu-id="d69b6-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="d69b6-111">Aby udostępnić zmienną tylko z poziomu jej modułu, klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="d69b6-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="d69b6-112">Umieść [instrukcję Dim](../../../language-reference/statements/dim-statement.md) dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.</span><span class="sxs-lookup"><span data-stu-id="d69b6-112">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="d69b6-113">Dołącz [prywatne](../../../language-reference/modifiers/private.md) słowo kluczowe do `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d69b6-113">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="d69b6-114">Możesz odczytać lub zapisać w zmiennej z dowolnego miejsca w module, klasie lub strukturze, ale nie spoza niej.</span><span class="sxs-lookup"><span data-stu-id="d69b6-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="d69b6-115">Aby udostępnić zmienną z dowolnego kodu, który może go zobaczyć</span><span class="sxs-lookup"><span data-stu-id="d69b6-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="d69b6-116">Dla zmiennej składowej należy umieścić `Dim` instrukcję dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolną procedurą.</span><span class="sxs-lookup"><span data-stu-id="d69b6-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="d69b6-117">Dołącz słowo kluczowe [Public](../../../language-reference/modifiers/public.md) do `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d69b6-117">Include the [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="d69b6-118">Można odczytać lub zapisać w zmiennej z dowolnego kodu, który współdziała z zestawem.</span><span class="sxs-lookup"><span data-stu-id="d69b6-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="d69b6-119">-lub-</span><span class="sxs-lookup"><span data-stu-id="d69b6-119">-or-</span></span>  
  
1. <span data-ttu-id="d69b6-120">Dla zmiennej lokalnej Umieść `Dim` instrukcję dla zmiennej wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="d69b6-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="d69b6-121">Nie dodawaj `Public` słowa kluczowego do `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d69b6-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="d69b6-122">Możesz odczytać lub zapisać w zmiennej z dowolnego miejsca w ramach procedury, ale nie spoza niej.</span><span class="sxs-lookup"><span data-stu-id="d69b6-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="d69b6-123">Dostęp chroniony i przyjazny</span><span class="sxs-lookup"><span data-stu-id="d69b6-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="d69b6-124">Można ograniczyć poziom dostępu zmiennej do jej klasy i wszelkich klas pochodnych lub do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d69b6-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="d69b6-125">Można również określić Unię tych ograniczeń, co umożliwia dostęp z kodu w dowolnej klasie pochodnej lub w innym miejscu w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="d69b6-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="d69b6-126">Ten związek należy określić, łącząc `Protected` `Friend` słowa kluczowe i w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="d69b6-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="d69b6-127">Aby udostępnić zmienną tylko z poziomu jej klasy i wszystkich klas pochodnych</span><span class="sxs-lookup"><span data-stu-id="d69b6-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="d69b6-128">Umieść `Dim` instrukcję dla zmiennej wewnątrz klasy, ale poza żadną procedurą.</span><span class="sxs-lookup"><span data-stu-id="d69b6-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="d69b6-129">Uwzględnij [chronione](../../../language-reference/modifiers/protected.md) słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d69b6-129">Include the [Protected](../../../language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="d69b6-130">Można odczytać lub zapisać w zmiennej z dowolnego miejsca w klasie, a także z poziomu dowolnej klasy pochodnej, ale nie spoza żadnej klasy w łańcuchu pochodnym.</span><span class="sxs-lookup"><span data-stu-id="d69b6-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="d69b6-131">Aby udostępnić zmienną tylko z poziomu tego samego zestawu</span><span class="sxs-lookup"><span data-stu-id="d69b6-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="d69b6-132">Umieść `Dim` instrukcję dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.</span><span class="sxs-lookup"><span data-stu-id="d69b6-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="d69b6-133">Dołącz słowo kluczowe [zaprzyjaźnione](../../../language-reference/modifiers/friend.md) w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d69b6-133">Include the [Friend](../../../language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="d69b6-134">Możesz odczytać lub zapisać w zmiennej z dowolnego miejsca w module, klasie lub strukturze, a także z dowolnego kodu w tym samym zestawie, ale nie spoza zestawu.</span><span class="sxs-lookup"><span data-stu-id="d69b6-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d69b6-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="d69b6-135">Example</span></span>  
 <span data-ttu-id="d69b6-136">W poniższym przykładzie przedstawiono deklaracje zmiennych z `Public` `Protected` `Friend` `Protected Friend` poziomami dostępu,,, i `Private` .</span><span class="sxs-lookup"><span data-stu-id="d69b6-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="d69b6-137">Należy pamiętać, że gdy `Dim` instrukcja określa poziom dostępu, nie trzeba uwzględniać `Dim` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="d69b6-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="d69b6-138">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d69b6-138">.NET Framework Security</span></span>  
 <span data-ttu-id="d69b6-139">Im bardziej restrykcyjny poziom dostępu zmiennej, tym mniejsze prawdopodobieństwo, że złośliwy kod może być niewłaściwym użyciem.</span><span class="sxs-lookup"><span data-stu-id="d69b6-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d69b6-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d69b6-140">See also</span></span>

- [<span data-ttu-id="d69b6-141">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d69b6-141">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="d69b6-142">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d69b6-142">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="d69b6-143">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="d69b6-143">Public</span></span>](../../../language-reference/modifiers/public.md)
- [<span data-ttu-id="d69b6-144">Chronione</span><span class="sxs-lookup"><span data-stu-id="d69b6-144">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="d69b6-145">Osoby</span><span class="sxs-lookup"><span data-stu-id="d69b6-145">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="d69b6-146">Użytek</span><span class="sxs-lookup"><span data-stu-id="d69b6-146">Private</span></span>](../../../language-reference/modifiers/private.md)
