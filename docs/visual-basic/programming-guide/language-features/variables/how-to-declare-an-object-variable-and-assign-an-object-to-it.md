---
title: 'Instrukcje: deklarowanie zmiennej obiektu i przypisywanie do niej obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410506"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="9e0e4-102">Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e0e4-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="9e0e4-103">Należy zadeklarować zmienną [typu danych obiektu](../../../language-reference/data-types/object-data-type.md) przez określenie `As Object` w [instrukcji Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9e0e4-103">You declare a variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="9e0e4-104">Obiekt można przypisać do takiej zmiennej poprzez umieszczenie obiektu po znaku równości ( `=` ) w instrukcji przypisania lub klauzuli inicjującej.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="9e0e4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e0e4-105">Example</span></span>

<span data-ttu-id="9e0e4-106">Poniższy przykład deklaruje `Object` zmienną i przypisuje do niej bieżące wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="9e0e4-107">Deklarację i przypisanie można połączyć przez zainicjowanie zmiennej jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="9e0e4-108">Poniższy przykład jest równoważny z poprzednim przykładem.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="9e0e4-109">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="9e0e4-109">Compile the code</span></span>

<span data-ttu-id="9e0e4-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9e0e4-110">This example requires:</span></span>

- <span data-ttu-id="9e0e4-111">Odwołanie do <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="9e0e4-112">Klasa, struktura lub moduł, w którym należy umieścić `Dim` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="9e0e4-113">Procedura, w której ma zostać umieszczona Instrukcja przypisania.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e0e4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e0e4-114">See also</span></span>

- [<span data-ttu-id="9e0e4-115">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="9e0e4-115">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="9e0e4-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="9e0e4-116">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="9e0e4-117">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="9e0e4-117">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="9e0e4-118">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="9e0e4-118">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="9e0e4-119">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9e0e4-119">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="9e0e4-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="9e0e4-120">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="9e0e4-121">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="9e0e4-121">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
