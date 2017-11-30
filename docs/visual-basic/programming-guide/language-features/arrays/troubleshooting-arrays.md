---
title: "Rozwiązywanie problemów związanych z tablicami (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0417ae8d37642a65b14cc81ae9dcf3a3c32d63ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="68772-102">Rozwiązywanie problemów związanych z tablicami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68772-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="68772-103">Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas pracy z tablicami.</span><span class="sxs-lookup"><span data-stu-id="68772-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="68772-104">Błędy kompilacji deklarowanie i Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="68772-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="68772-105">Błędy kompilacji mogą wynikać z nieporozumienia zasady deklarowanie, tworzenie i Inicjowanie tablic.</span><span class="sxs-lookup"><span data-stu-id="68772-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="68772-106">Najczęstszymi przyczynami błędów są następujące:</span><span class="sxs-lookup"><span data-stu-id="68772-106">The most common causes of errors are the following:</span></span>  
  
-   <span data-ttu-id="68772-107">Dostarczanie [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) klauzuli po określeniu długości wymiaru w deklaracji zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="68772-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="68772-108">Poniższe wiersze kodu pokazują nieprawidłowy deklaracje tego typu.</span><span class="sxs-lookup"><span data-stu-id="68772-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   <span data-ttu-id="68772-109">Określanie długości wymiaru więcej niż tablicy nieregularnej tablicy najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="68772-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="68772-110">Następujący wiersz kodu zawiera nieprawidłową deklaracją tego typu.</span><span class="sxs-lookup"><span data-stu-id="68772-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   <span data-ttu-id="68772-111">Pominięcie `New` — słowo kluczowe podczas określania wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="68772-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="68772-112">Następujący wiersz kodu zawiera nieprawidłową deklaracją tego typu.</span><span class="sxs-lookup"><span data-stu-id="68772-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   <span data-ttu-id="68772-113">Dostarczanie `New` klauzuli bez nawiasów klamrowych (`{}`).</span><span class="sxs-lookup"><span data-stu-id="68772-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="68772-114">Poniższe wiersze kodu pokazują nieprawidłowy deklaracje tego typu.</span><span class="sxs-lookup"><span data-stu-id="68772-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="68772-115">Uzyskiwanie dostępu do tablicy poza zakresem</span><span class="sxs-lookup"><span data-stu-id="68772-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="68772-116">Proces inicjowania tablicy przypisuje górną i dolną granicę każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="68772-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="68772-117">Nieprawidłowy indeks lub indeks, dla każdego wymiaru, należy określić co dostępu do elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="68772-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="68772-118">W przypadku indeksu poniżej dolna lub powyżej górnej granicy, <xref:System.IndexOutOfRangeException> wyników wyjątku.</span><span class="sxs-lookup"><span data-stu-id="68772-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="68772-119">Kompilator nie może wykryć wystąpił błąd, więc wystąpi błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="68772-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="68772-120">Określanie granic</span><span class="sxs-lookup"><span data-stu-id="68772-120">Determining Bounds</span></span>  
 <span data-ttu-id="68772-121">Jeśli inny składnik przekazuje tablicy do kodu, na przykład jako argument procedury nie znasz rozmiaru tablicy lub długości jej wymiarów.</span><span class="sxs-lookup"><span data-stu-id="68772-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="68772-122">Zawsze należy określić górną granicę każdego wymiaru tablicy można było uzyskać dostępu do żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="68772-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="68772-123">Jeśli tablica został utworzony w sposób inny niż [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `New` klauzuli, dolna granica może być inną niż 0 i jest najbezpieczniejszy określić, że dolna granica również.</span><span class="sxs-lookup"><span data-stu-id="68772-123">If the array has been created by some means other than a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="68772-124">Określanie wymiaru</span><span class="sxs-lookup"><span data-stu-id="68772-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="68772-125">Podczas określania granice tablicy wielowymiarowej, należy zadbać określania wymiaru.</span><span class="sxs-lookup"><span data-stu-id="68772-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="68772-126">`dimension` Parametry <xref:System.Array.GetLowerBound%2A> i <xref:System.Array.GetUpperBound%2A> metody są oparte na 0, podczas `Rank` parametry [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> i <xref:Microsoft.VisualBasic.Information.UBound%2A> funkcje są oparte na 1.</span><span class="sxs-lookup"><span data-stu-id="68772-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68772-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68772-127">See Also</span></span>  
 [<span data-ttu-id="68772-128">Tablice</span><span class="sxs-lookup"><span data-stu-id="68772-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="68772-129">Porady: inicjowanie zmiennej tablicy w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68772-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
