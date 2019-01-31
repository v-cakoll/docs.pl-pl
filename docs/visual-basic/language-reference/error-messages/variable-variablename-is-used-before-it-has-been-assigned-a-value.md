---
title: Zmienna „<variablename>” jest używana, zanim zostanie do niej przypisana wartość
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 23201b89f44f6384ae9f75d941d264e8d59bef80
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268837"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="565d4-102">Zmienna "\<nazwa_zmiennej >" jest używana, zanim została do niej przypisana wartość</span><span class="sxs-lookup"><span data-stu-id="565d4-102">Variable '\<variablename>' is used before it has been assigned a value</span></span>
<span data-ttu-id="565d4-103">Zmienna "\<nazwa_zmiennej >" jest używana, zanim została do niej przypisana wartość.</span><span class="sxs-lookup"><span data-stu-id="565d4-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="565d4-104">W czasie wykonywania może wystąpić wyjątek pustej referencji.</span><span class="sxs-lookup"><span data-stu-id="565d4-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="565d4-105">Aplikacja ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod, który odczytuje zmienną przed przypisaniem do niej dowolną wartość.</span><span class="sxs-lookup"><span data-stu-id="565d4-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="565d4-106">Jeśli zmienna nie zostanie przypisana wartość, zawiera wartość domyślna dla jego typu danych.</span><span class="sxs-lookup"><span data-stu-id="565d4-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="565d4-107">Odwołanie do typu danych, że wartość domyślna to [nic](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="565d4-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="565d4-108">Odczytywanie zmienną odwołania, który ma wartość `Nothing` może spowodować, że <xref:System.NullReferenceException> w pewnych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="565d4-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="565d4-109">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="565d4-109">By default, this message is a warning.</span></span> <span data-ttu-id="565d4-110">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="565d4-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="565d4-111">**Identyfikator błędu:** BC42104</span><span class="sxs-lookup"><span data-stu-id="565d4-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="565d4-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="565d4-112">To correct this error</span></span>  
  
-   <span data-ttu-id="565d4-113">Sprawdź logikę przepływu sterowania i upewnij się, że zmienna ma prawidłową wartość przed kontrola przechodzi do żadnej instrukcji, który odczyta go.</span><span class="sxs-lookup"><span data-stu-id="565d4-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="565d4-114">Jest jednym ze sposobów, aby zagwarantować, że zmienna zawsze ma prawidłową wartość zainicjować go jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="565d4-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="565d4-115">Zobacz sekcję "Inicjowanie" w [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="565d4-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565d4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="565d4-116">See also</span></span>
- [<span data-ttu-id="565d4-117">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="565d4-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="565d4-118">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="565d4-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="565d4-119">Rozwiązywanie problemów związanych ze zmiennymi</span><span class="sxs-lookup"><span data-stu-id="565d4-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
