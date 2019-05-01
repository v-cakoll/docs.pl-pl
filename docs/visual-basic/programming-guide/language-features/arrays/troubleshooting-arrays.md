---
title: Rozwiązywanie problemów związanych z tablicami (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2b051d22fe3d331626f2e181c008043e576b7526
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908131"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="e55f6-102">Rozwiązywanie problemów związanych z tablicami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e55f6-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="e55f6-103">Ta strona zawiera listę niektórych typowych problemów, które mogą wystąpić podczas pracy z tablicami.</span><span class="sxs-lookup"><span data-stu-id="e55f6-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="e55f6-104">Błędy kompilacji deklarowania i inicjowania tablicy</span><span class="sxs-lookup"><span data-stu-id="e55f6-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="e55f6-105">Błędy kompilacji mogą wynikać z nieporozumienia reguły deklarowania, tworzenia i inicjowania tablic.</span><span class="sxs-lookup"><span data-stu-id="e55f6-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="e55f6-106">Najbardziej typowe przyczyny błędów są następujące:</span><span class="sxs-lookup"><span data-stu-id="e55f6-106">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="e55f6-107">Dostarczanie [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) klauzuli po określeniu długości wymiarów w deklaracji zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="e55f6-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="e55f6-108">Następujące wiersze kodu pokazują nieprawidłowe deklarację tego typu.</span><span class="sxs-lookup"><span data-stu-id="e55f6-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="e55f6-109">Określenie długości wymiarów dla więcej niż najwyższego poziomu tablicy nieregularnej tablicy.</span><span class="sxs-lookup"><span data-stu-id="e55f6-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="e55f6-110">Następujący wiersz kodu zawiera nieprawidłowy deklaracja tego typu.</span><span class="sxs-lookup"><span data-stu-id="e55f6-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="e55f6-111">Pominięcie `New` — słowo kluczowe podczas określania wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="e55f6-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="e55f6-112">Następujący wiersz kodu zawiera nieprawidłowy deklaracja tego typu.</span><span class="sxs-lookup"><span data-stu-id="e55f6-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="e55f6-113">Dostarczanie `New` klauzuli bez nawiasów klamrowych (`{}`).</span><span class="sxs-lookup"><span data-stu-id="e55f6-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="e55f6-114">Następujące wiersze kodu pokazują nieprawidłowe deklarację tego typu.</span><span class="sxs-lookup"><span data-stu-id="e55f6-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="e55f6-115">Uzyskiwanie dostępu do tablicy poza zakresem</span><span class="sxs-lookup"><span data-stu-id="e55f6-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="e55f6-116">Proces inicjowania tablicy przypisuje górną granicę i dolną granicę każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="e55f6-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="e55f6-117">Każdy dostęp do elementu tablicy, należy określić prawidłowy indeksu lub indeksu dolnego, dla każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="e55f6-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="e55f6-118">W przypadku dowolnego indeksu poniżej dolna lub powyżej jego górnej granicy <xref:System.IndexOutOfRangeException> wynikiem będzie wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e55f6-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="e55f6-119">Kompilator nie może wykryć takiego komunikatu o błędzie, więc wystąpi błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e55f6-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="e55f6-120">Określanie granice</span><span class="sxs-lookup"><span data-stu-id="e55f6-120">Determining Bounds</span></span>  
 <span data-ttu-id="e55f6-121">Jeśli inny składnik przekazuje tablicę do kodu, na przykład jako argumentu procedury nie znasz rozmiaru tablicy lub długości jej wymiarów.</span><span class="sxs-lookup"><span data-stu-id="e55f6-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="e55f6-122">Przed przystąpieniem do dostępu do żadnych elementów, należy zawsze określić górną granicę dla każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="e55f6-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="e55f6-123">Jeśli tablica została utworzona przy użyciu niektórych metod innych niż w języku Visual Basic `New` klauzuli dolna granica może być coś innego niż 0 i jest najbezpieczniejszy określić również tego dolna granica.</span><span class="sxs-lookup"><span data-stu-id="e55f6-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="e55f6-124">Określanie wymiaru</span><span class="sxs-lookup"><span data-stu-id="e55f6-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="e55f6-125">Podczas określania granice tablicy wielowymiarowej, powinien zachować ostrożność, jak określić wymiaru.</span><span class="sxs-lookup"><span data-stu-id="e55f6-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="e55f6-126">`dimension` Parametry <xref:System.Array.GetLowerBound%2A> i <xref:System.Array.GetUpperBound%2A> metody są oparte na 0, podczas `Rank` parametry języka Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> i <xref:Microsoft.VisualBasic.Information.UBound%2A> funkcje są oparte na 1.</span><span class="sxs-lookup"><span data-stu-id="e55f6-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55f6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e55f6-127">See also</span></span>

- [<span data-ttu-id="e55f6-128">Tablice</span><span class="sxs-lookup"><span data-stu-id="e55f6-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="e55f6-129">Instrukcje: Inicjowanie zmiennej tablicy w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e55f6-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
