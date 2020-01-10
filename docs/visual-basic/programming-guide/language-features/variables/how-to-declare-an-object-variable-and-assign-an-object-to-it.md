---
title: 'Instrukcje: deklarowanie zmiennej obiektu i przypisywanie do niej obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: eaaeda2a986584e6e1a2e0d2cda3890fb6187598
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344237"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="37b9e-102">Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37b9e-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="37b9e-103">Należy zadeklarować zmienną [typu danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) , określając `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="37b9e-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="37b9e-104">Obiekt można przypisać do takiej zmiennej poprzez umieszczenie obiektu po znaku równości (`=`) w instrukcji przypisania lub klauzuli inicjacji.</span><span class="sxs-lookup"><span data-stu-id="37b9e-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="37b9e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="37b9e-105">Example</span></span>

<span data-ttu-id="37b9e-106">Poniższy przykład deklaruje zmienną `Object` i przypisuje do niej bieżące wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="37b9e-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="37b9e-107">Deklarację i przypisanie można połączyć przez zainicjowanie zmiennej jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="37b9e-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="37b9e-108">Poniższy przykład jest równoważny z poprzednim przykładem.</span><span class="sxs-lookup"><span data-stu-id="37b9e-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="37b9e-109">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="37b9e-109">Compile the code</span></span>

<span data-ttu-id="37b9e-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="37b9e-110">This example requires:</span></span>

- <span data-ttu-id="37b9e-111">Odwołanie do przestrzeni nazw <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="37b9e-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="37b9e-112">Klasa, struktura lub moduł, w którym ma zostać umieszczona instrukcja `Dim`.</span><span class="sxs-lookup"><span data-stu-id="37b9e-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="37b9e-113">Procedura, w której ma zostać umieszczona Instrukcja przypisania.</span><span class="sxs-lookup"><span data-stu-id="37b9e-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="37b9e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37b9e-114">See also</span></span>

- [<span data-ttu-id="37b9e-115">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="37b9e-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="37b9e-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="37b9e-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="37b9e-117">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="37b9e-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="37b9e-118">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="37b9e-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="37b9e-119">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="37b9e-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="37b9e-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="37b9e-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="37b9e-121">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="37b9e-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
