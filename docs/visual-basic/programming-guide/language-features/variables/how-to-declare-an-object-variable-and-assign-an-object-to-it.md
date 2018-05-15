---
title: 'Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 1f38c90f0571b3fc73c4c89812092cdada936d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="32813-102">Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32813-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="32813-103">Deklarowanie zmiennej [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) , określając `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="32813-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="32813-104">Przypisz obiekt takiej zmiennej umieszczając obiekt po znaku równości (`=`) w klauzuli przypisania instrukcji lub inicjowania.</span><span class="sxs-lookup"><span data-stu-id="32813-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32813-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="32813-105">Example</span></span>  
 <span data-ttu-id="32813-106">Poniższy przykład deklaruje `Object` zmienną i przypisuje bieżące wystąpienie do niego.</span><span class="sxs-lookup"><span data-stu-id="32813-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="32813-107">Deklaracja i przypisania można połączyć za inicjowanie zmiennej jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="32813-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="32813-108">Poniższy przykład jest odpowiednikiem poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="32813-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="32813-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="32813-109">Compiling the Code</span></span>  
 <span data-ttu-id="32813-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="32813-110">This example requires:</span></span>  
  
-   <span data-ttu-id="32813-111">Odwołanie do <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32813-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="32813-112">Klasy, struktury lub moduł, w której chcesz umieścić `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="32813-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="32813-113">Procedura, w której chcesz umieścić w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="32813-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32813-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32813-114">See Also</span></span>  
 [<span data-ttu-id="32813-115">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="32813-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="32813-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="32813-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="32813-117">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="32813-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="32813-118">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="32813-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="32813-119">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="32813-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="32813-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="32813-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="32813-121">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="32813-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
