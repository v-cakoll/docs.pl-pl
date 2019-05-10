---
title: 'Instrukcje: Deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: e172d62e5bfadded254d5a5fd25b1dcf2da9634d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663583"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="eac2b-102">Instrukcje: Deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eac2b-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="eac2b-103">Zadeklaruj zmienną [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) , określając `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="eac2b-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="eac2b-104">Przypisz obiekt takiej zmiennej, umieszczając obiekt po znaku równości (`=`) w klauzuli instrukcji lub inicjowania przypisania.</span><span class="sxs-lookup"><span data-stu-id="eac2b-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eac2b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="eac2b-105">Example</span></span>  
 <span data-ttu-id="eac2b-106">Poniższy przykład deklaruje `Object` zmienną i przypisuje bieżące wystąpienie do niego.</span><span class="sxs-lookup"><span data-stu-id="eac2b-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="eac2b-107">Możesz połączyć deklarację i przypisanie przez inicjowanie zmiennej jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="eac2b-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="eac2b-108">Poniższy przykład jest równoważny do poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="eac2b-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eac2b-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="eac2b-109">Compiling the Code</span></span>  
 <span data-ttu-id="eac2b-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="eac2b-110">This example requires:</span></span>  
  
- <span data-ttu-id="eac2b-111">Odwołanie do <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="eac2b-111">A reference to the <xref:System> namespace.</span></span>  
  
- <span data-ttu-id="eac2b-112">Klasy, struktury lub modułu, w której chcesz umieścić `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="eac2b-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
- <span data-ttu-id="eac2b-113">Procedura, w której chcesz umieścić w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="eac2b-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac2b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eac2b-114">See also</span></span>

- [<span data-ttu-id="eac2b-115">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="eac2b-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="eac2b-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="eac2b-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="eac2b-117">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="eac2b-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="eac2b-118">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="eac2b-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="eac2b-119">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eac2b-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="eac2b-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="eac2b-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="eac2b-121">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eac2b-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
