---
title: Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: dd5618bd0533f885a6aef8229b2d8cb1bc34c237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="62901-102">Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania</span><span class="sxs-lookup"><span data-stu-id="62901-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="62901-103">Instrukcja podejmuje próbę przypisania wartości dla wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62901-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="62901-104">Można przypisać wartość tylko do zapisu zmienną, właściwością lub element tablicy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="62901-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="62901-105">Poniższy przykład przedstawia, jak ten błąd może wystąpić.</span><span class="sxs-lookup"><span data-stu-id="62901-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="62901-106">Podobne przykłady można zastosować do właściwości i elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="62901-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="62901-107">**Pośredni dostęp.**</span><span class="sxs-lookup"><span data-stu-id="62901-107">**Indirect Access.**</span></span> <span data-ttu-id="62901-108">Pośredni dostęp do typu wartości można również generować tego błędu.</span><span class="sxs-lookup"><span data-stu-id="62901-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="62901-109">Należy wziąć pod uwagę poniższy przykład kodu, który próbuje ustawić wartość <xref:System.Drawing.Point> uzyskując pośredni przez <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="62901-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="62901-110">Ostatnią instrukcją w poprzednim przykładzie nie powiedzie się, ponieważ spowoduje to utworzenie tymczasowego alokacji dla <xref:System.Drawing.Point> zwrócony przez strukturę <xref:System.Windows.Forms.Control.Location%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="62901-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="62901-111">Struktura jest typem wartości, a struktura tymczasowe nie są zachowywane po wykonaniu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="62901-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="62901-112">Problem został rozwiązany przez deklarowanie i użycie zmiennej <xref:System.Windows.Forms.Control.Location%2A>, co powoduje stałej alokacji dla <xref:System.Drawing.Point> struktury.</span><span class="sxs-lookup"><span data-stu-id="62901-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="62901-113">Poniższy przykład przedstawia kod, który można zastąpić ostatniej instrukcji w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="62901-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="62901-114">**Identyfikator błędu:** BC30068</span><span class="sxs-lookup"><span data-stu-id="62901-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62901-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="62901-115">To correct this error</span></span>  
  
-   <span data-ttu-id="62901-116">Jeśli instrukcja przypisuje wartość do wyrażenia, Zastąp wyrażenie pojedynczą zmienną zapisywalny, właściwość lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="62901-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="62901-117">Jeśli instrukcja dokonuje bezpośredni dostęp do typu wartość (zazwyczaj struktury), Utwórz zmienną do przechowywania wartości typu.</span><span class="sxs-lookup"><span data-stu-id="62901-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="62901-118">Przypisz odpowiednie struktury (lub innego typu wartość) do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="62901-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="62901-119">Umożliwia dostęp do właściwości, aby przypisać wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="62901-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62901-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62901-120">See Also</span></span>  
 [<span data-ttu-id="62901-121">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="62901-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="62901-122">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="62901-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="62901-123">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="62901-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
