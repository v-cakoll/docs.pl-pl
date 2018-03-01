---
title: "Zmienna &#39; &lt;nazwa_zmiennej&gt;&#39; jest używana, zanim została do niej przypisana wartość"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="10ba3-102">Zmienna &#39; &lt;nazwa_zmiennej&gt;&#39; jest używana, zanim została do niej przypisana wartość</span><span class="sxs-lookup"><span data-stu-id="10ba3-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="10ba3-103">Zmienna "\<nazwa_zmiennej >" jest używana, zanim została do niej przypisana wartość.</span><span class="sxs-lookup"><span data-stu-id="10ba3-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="10ba3-104">W czasie wykonywania może wystąpić wyjątek odwołania zerowego.</span><span class="sxs-lookup"><span data-stu-id="10ba3-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="10ba3-105">Aplikacja ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod odczytujący zmiennej przed przypisaniem do niej żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="10ba3-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="10ba3-106">Jeśli zmienna nie zostanie przypisana wartość, zawiera wartość domyślną dla tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="10ba3-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="10ba3-107">Odwołanie do typu danych, że wartość domyślna to [nic](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="10ba3-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="10ba3-108">Odczytywanie odwołanie do zmiennej, która ma wartość `Nothing` może spowodować <xref:System.NullReferenceException> w pewnych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="10ba3-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="10ba3-109">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="10ba3-109">By default, this message is a warning.</span></span> <span data-ttu-id="10ba3-110">Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="10ba3-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="10ba3-111">**Identyfikator błędu:** BC42104</span><span class="sxs-lookup"><span data-stu-id="10ba3-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10ba3-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="10ba3-112">To correct this error</span></span>  
  
-   <span data-ttu-id="10ba3-113">Sprawdź logika przepływu sterowania i upewnij się, że zmienna ma prawidłową wartość, zanim formant przekazuje do żadnych instrukcji, która odczytuje go.</span><span class="sxs-lookup"><span data-stu-id="10ba3-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="10ba3-114">Jest jednym ze sposobów gwarantuje, że zmienna zawsze ma prawidłową wartość zainicjować go jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="10ba3-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="10ba3-115">Zobacz sekcję "Inicjowanie" w [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="10ba3-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ba3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10ba3-116">See Also</span></span>  
 [<span data-ttu-id="10ba3-117">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="10ba3-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="10ba3-118">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="10ba3-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="10ba3-119">Rozwiązywanie problemów z zmiennych</span><span class="sxs-lookup"><span data-stu-id="10ba3-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
