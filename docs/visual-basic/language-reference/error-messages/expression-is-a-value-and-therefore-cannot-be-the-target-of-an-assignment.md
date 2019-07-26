---
title: Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: d5aae4d30abbf9ed2af260412352a5e0452e0dcc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513037"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="cdcb5-102">Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania</span><span class="sxs-lookup"><span data-stu-id="cdcb5-102">Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="cdcb5-103">Instrukcja próbuje przypisać wartość do wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="cdcb5-104">Można przypisać wartość tylko do zapisywalnej zmiennej, właściwości lub elementu tablicy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="cdcb5-105">Poniższy przykład ilustruje, jak ten błąd może wystąpić.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-105">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="cdcb5-106">Podobne przykłady mogą dotyczyć właściwości i elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-106">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="cdcb5-107">**Dostęp pośredni.**</span><span class="sxs-lookup"><span data-stu-id="cdcb5-107">**Indirect Access.**</span></span> <span data-ttu-id="cdcb5-108">Bezpośredni dostęp za pomocą typu wartości może również generować ten błąd.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="cdcb5-109">Rozważmy następujący przykład kodu, który podejmuje próbę ustawienia wartości <xref:System.Drawing.Point> przez uzyskanie dostępu do niej <xref:System.Windows.Forms.Control.Location%2A>pośrednio za pomocą.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="cdcb5-110">Ostatnia instrukcja w powyższym przykładzie kończy się niepowodzeniem, ponieważ powoduje utworzenie tylko tymczasowej alokacji dla <xref:System.Drawing.Point> struktury zwróconej <xref:System.Windows.Forms.Control.Location%2A> przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="cdcb5-111">Struktura jest typem wartości, a tymczasowa struktura nie jest zachowywana po uruchomieniu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="cdcb5-112">Problem został rozwiązany przez zadeklarowanie i użycie zmiennej dla <xref:System.Windows.Forms.Control.Location%2A>, co powoduje utworzenie bardziej trwałego przydziału <xref:System.Drawing.Point> dla struktury.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="cdcb5-113">Poniższy przykład pokazuje kod, który może zastąpić ostatnią instrukcję z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-113">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="cdcb5-114">**Identyfikator błędu:** BC30068</span><span class="sxs-lookup"><span data-stu-id="cdcb5-114">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cdcb5-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cdcb5-115">To correct this error</span></span>

- <span data-ttu-id="cdcb5-116">Jeśli instrukcja przypisuje wartość do wyrażenia, zastąp wyrażenie pojedynczym zapisywalną zmienną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="cdcb5-117">Jeśli instrukcja wykonuje pośredni dostęp za pomocą typu wartości (zazwyczaj struktury), Utwórz zmienną do przechowywania typu wartości.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="cdcb5-118">Przypisz odpowiednią strukturę (lub inny typ wartości) do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-118">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="cdcb5-119">Użyj zmiennej, aby uzyskać dostęp do właściwości w celu przypisania jej wartości.</span><span class="sxs-lookup"><span data-stu-id="cdcb5-119">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdcb5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdcb5-120">See also</span></span>

- [<span data-ttu-id="cdcb5-121">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="cdcb5-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="cdcb5-122">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="cdcb5-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="cdcb5-123">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="cdcb5-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
