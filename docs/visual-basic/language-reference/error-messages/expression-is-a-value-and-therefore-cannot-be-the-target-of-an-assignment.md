---
title: Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 3027be6ee4ed3664b81c661b6a086a3604573833
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826136"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="c3c1f-102">Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania</span><span class="sxs-lookup"><span data-stu-id="c3c1f-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="c3c1f-103">Instrukcja próbuje przypisać wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="c3c1f-104">W czasie wykonywania, można przypisać wartości tylko do zapisu zmiennej, właściwości lub elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="c3c1f-105">W poniższym przykładzie pokazano, jak ten błąd może wystąpić.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="c3c1f-106">Podobne przykłady można zastosować do właściwości i elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="c3c1f-107">**Bezpośredni dostęp.**</span><span class="sxs-lookup"><span data-stu-id="c3c1f-107">**Indirect Access.**</span></span> <span data-ttu-id="c3c1f-108">Pośredni dostęp za pośrednictwem typu wartości można również wygenerować ten błąd.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="c3c1f-109">Należy wziąć pod uwagę poniższy przykład kodu, który próbuje ustawić wartość <xref:System.Drawing.Point> uzyskując pośrednio za pomocą <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="c3c1f-110">Ostatnią instrukcją poprzedni przykład nie powiedzie się, ponieważ powoduje to utworzenie tymczasowego alokacji dla <xref:System.Drawing.Point> zwracany przez strukturę <xref:System.Windows.Forms.Control.Location%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="c3c1f-111">Struktura jest typem wartości, a struktura tymczasowe nie są zachowywane po uruchomieniu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="c3c1f-112">Problem został rozwiązany przez deklarowanie i użycie zmiennej dla <xref:System.Windows.Forms.Control.Location%2A>, co powoduje utworzenie bardziej trwałych alokacji dla <xref:System.Drawing.Point> struktury.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="c3c1f-113">Poniższy przykład pokazuje kod, który można zastąpić ostatnią instrukcję w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="c3c1f-114">**Identyfikator błędu:** BC30068</span><span class="sxs-lookup"><span data-stu-id="c3c1f-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c3c1f-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c3c1f-115">To correct this error</span></span>  
  
-   <span data-ttu-id="c3c1f-116">Jeśli instrukcja przypisuje wartość do wyrażenia, Zamień wyrażenia pojedynczej zmiennej zapisywalny, właściwości lub elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="c3c1f-117">Jeśli instrukcja sprawia, że pośredni dostęp za pośrednictwem typu wartości (zwykle struktura), należy utworzyć zmienną typu wartości.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="c3c1f-118">Przypisz odpowiednią strukturę (lub innego typu wartości) do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="c3c1f-119">Umożliwia dostęp do właściwości, aby przypisać wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c3c1f-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c1f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3c1f-120">See also</span></span>

- [<span data-ttu-id="c3c1f-121">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="c3c1f-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="c3c1f-122">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="c3c1f-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="c3c1f-123">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="c3c1f-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
