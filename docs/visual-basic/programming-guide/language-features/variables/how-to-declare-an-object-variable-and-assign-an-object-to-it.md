---
title: 'Instrukcje: deklarowanie zmiennej obiektu i przypisywanie do niej obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352905"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="b60d1-102">Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b60d1-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="b60d1-103">Należy zadeklarować zmienną [typu danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) , określając `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b60d1-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="b60d1-104">Obiekt można przypisać do takiej zmiennej poprzez umieszczenie obiektu po znaku równości (`=`) w instrukcji przypisania lub klauzuli inicjacji.</span><span class="sxs-lookup"><span data-stu-id="b60d1-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="b60d1-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b60d1-105">Example</span></span>

<span data-ttu-id="b60d1-106">Poniższy przykład deklaruje zmienną `Object` i przypisuje do niej bieżące wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b60d1-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="b60d1-107">Deklarację i przypisanie można połączyć przez zainicjowanie zmiennej jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b60d1-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="b60d1-108">Poniższy przykład jest równoważny z poprzednim przykładem.</span><span class="sxs-lookup"><span data-stu-id="b60d1-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="b60d1-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b60d1-109">Compiling the Code</span></span>

<span data-ttu-id="b60d1-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b60d1-110">This example requires:</span></span>

- <span data-ttu-id="b60d1-111">Odwołanie do przestrzeni nazw <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="b60d1-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="b60d1-112">Klasa, struktura lub moduł, w którym ma zostać umieszczona instrukcja `Dim`.</span><span class="sxs-lookup"><span data-stu-id="b60d1-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="b60d1-113">Procedura, w której ma zostać umieszczona Instrukcja przypisania.</span><span class="sxs-lookup"><span data-stu-id="b60d1-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="b60d1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b60d1-114">See also</span></span>

- [<span data-ttu-id="b60d1-115">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="b60d1-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="b60d1-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="b60d1-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="b60d1-117">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="b60d1-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="b60d1-118">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="b60d1-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="b60d1-119">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b60d1-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="b60d1-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="b60d1-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="b60d1-121">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b60d1-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
