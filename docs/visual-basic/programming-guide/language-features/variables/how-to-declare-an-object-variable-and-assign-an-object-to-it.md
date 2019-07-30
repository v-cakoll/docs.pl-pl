---
title: 'Instrukcje: Zadeklaruj zmienną obiektu i przypisz do niej obiekt w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630873"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="80c90-102">Instrukcje: Zadeklaruj zmienną obiektu i przypisz do niej obiekt w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80c90-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="80c90-103">Należy zadeklarować zmienną [typu danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) przez określenie `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="80c90-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="80c90-104">Obiekt można przypisać do takiej zmiennej poprzez umieszczenie obiektu po znaku równości (`=`) w instrukcji przypisania lub klauzuli inicjującej.</span><span class="sxs-lookup"><span data-stu-id="80c90-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="80c90-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="80c90-105">Example</span></span>

<span data-ttu-id="80c90-106">Poniższy przykład deklaruje `Object` zmienną i przypisuje do niej bieżące wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="80c90-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="80c90-107">Deklarację i przypisanie można połączyć przez zainicjowanie zmiennej jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="80c90-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="80c90-108">Poniższy przykład jest równoważny z poprzednim przykładem.</span><span class="sxs-lookup"><span data-stu-id="80c90-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="80c90-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80c90-109">Compiling the Code</span></span>

<span data-ttu-id="80c90-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="80c90-110">This example requires:</span></span>

- <span data-ttu-id="80c90-111">Odwołanie do <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="80c90-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="80c90-112">Klasa, struktura lub moduł, w którym należy umieścić `Dim` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="80c90-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="80c90-113">Procedura, w której ma zostać umieszczona Instrukcja przypisania.</span><span class="sxs-lookup"><span data-stu-id="80c90-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="80c90-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80c90-114">See also</span></span>

- [<span data-ttu-id="80c90-115">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="80c90-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="80c90-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="80c90-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="80c90-117">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="80c90-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="80c90-118">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="80c90-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="80c90-119">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="80c90-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="80c90-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="80c90-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="80c90-121">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="80c90-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
