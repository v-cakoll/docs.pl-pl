---
title: "Słowa kluczowe jako nazwy elementów w Code (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="d8151-102">Słowa kluczowe jako nazwy elementów w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8151-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="d8151-103">Każdy element program — takie jak zmienna, klasa lub element członkowski — może mieć taką samą nazwę jak ograniczeniami — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d8151-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="d8151-104">Na przykład można utworzyć zmiennej o nazwie `Loop`.</span><span class="sxs-lookup"><span data-stu-id="d8151-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="d8151-105">Jednak aby odwołać się do używanej wersji — który ma taką samą nazwę jak ograniczeniami `Loop` — słowo kluczowe — należy poprzedzić ciągu pełnej kwalifikacji lub została ujęta w nawiasy kwadratowe (`[ ]`), jak pokazano na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d8151-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="d8151-106">Wykonaj jedną z nich, a następnie Visual Basic założono użycie wewnętrznej `Loop` — słowo kluczowe i tworzy błąd, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d8151-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="d8151-107">Podczas odwoływania się do formularzy i kontrolek i gdy służy nawiasy kwadratowe deklarowanie zmiennej lub definiujący procedurę o tej samej nazwie jako ograniczeniami — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d8151-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="d8151-108">Można go łatwo Pamiętaj, aby zakwalifikować nazwy lub obejmują nawiasów kwadratowych, w związku z tym spowodują one błędów w kodzie i utrudnić odczytu.</span><span class="sxs-lookup"><span data-stu-id="d8151-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="d8151-109">Z tego powodu zalecamy nie używać ograniczeniami słowa kluczowe jako nazwy elementów programu.</span><span class="sxs-lookup"><span data-stu-id="d8151-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="d8151-110">Jednak jeśli przyszłych wersjach programu Visual Basic definiuje new — słowo kluczowe powodujący konflikt z istniejącym formularzu lub nazwa formantu, następnie służy ta technika podczas aktualizowania kodu do pracy z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="d8151-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8151-111">Program może również obejmować nazwy elementów udostępnione przez innych zestawów występujących w odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="d8151-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="d8151-112">Jeśli te nazwy w konflikcie z ograniczeniami słów kluczowych, następnie umieszczenie nawiasy kwadratowe wokół nich spowoduje Visual Basic zinterpretować je jako określonych elementów.</span><span class="sxs-lookup"><span data-stu-id="d8151-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8151-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8151-113">See Also</span></span>  
 [<span data-ttu-id="d8151-114">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d8151-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="d8151-115">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="d8151-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="d8151-116">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d8151-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
