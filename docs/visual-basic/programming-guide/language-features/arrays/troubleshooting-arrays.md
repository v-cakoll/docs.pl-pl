---
title: Rozwiązywanie problemów związanych z tablicami
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: e633c5a00693f188270b1610abaf2decb656b00a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414598"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="12f58-102">Rozwiązywanie problemów związanych z tablicami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12f58-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="12f58-103">Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas pracy z tablicami.</span><span class="sxs-lookup"><span data-stu-id="12f58-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="12f58-104">Błędy kompilacji deklarujące i inicjujące tablicę</span><span class="sxs-lookup"><span data-stu-id="12f58-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="12f58-105">Błędy kompilacji mogą wynikać z nieporozumienia reguł do deklarowania, tworzenia i inicjowania tablic.</span><span class="sxs-lookup"><span data-stu-id="12f58-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="12f58-106">Najczęstszymi przyczynami błędów są następujące:</span><span class="sxs-lookup"><span data-stu-id="12f58-106">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="12f58-107">Dostarczenie [nowej klauzuli operatora](../../../language-reference/operators/new-operator.md) po określeniu długości wymiarów w deklaracji zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="12f58-107">Supplying a [New Operator](../../../language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="12f58-108">Poniższe wiersze kodu pokazują nieprawidłowe deklaracje tego typu.</span><span class="sxs-lookup"><span data-stu-id="12f58-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="12f58-109">Określanie długości wymiarów dla więcej niż tablicy najwyższego poziomu tablicy nieregularnej.</span><span class="sxs-lookup"><span data-stu-id="12f58-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="12f58-110">Poniższy wiersz kodu przedstawia nieprawidłową deklarację tego typu.</span><span class="sxs-lookup"><span data-stu-id="12f58-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="12f58-111">Pomijanie `New` słowa kluczowego podczas określania wartości elementów.</span><span class="sxs-lookup"><span data-stu-id="12f58-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="12f58-112">Poniższy wiersz kodu przedstawia nieprawidłową deklarację tego typu.</span><span class="sxs-lookup"><span data-stu-id="12f58-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="12f58-113">Dostarczanie `New` klauzuli bez nawiasów klamrowych ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="12f58-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="12f58-114">Poniższe wiersze kodu pokazują nieprawidłowe deklaracje tego typu.</span><span class="sxs-lookup"><span data-stu-id="12f58-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="12f58-115">Uzyskiwanie dostępu do tablicy poza granicami</span><span class="sxs-lookup"><span data-stu-id="12f58-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="12f58-116">Proces inicjowania tablicy przypisuje górną granicę i dolną granicę dla każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="12f58-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="12f58-117">Każdy dostęp do elementu tablicy musi określać prawidłowy indeks (lub dolny) dla każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="12f58-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="12f58-118">Jeśli indeks jest niższy od jego dolnej granicy lub przekracza górną granicę, zostanie <xref:System.IndexOutOfRangeException> osiągnięty wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12f58-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="12f58-119">Kompilator nie może wykryć takiego błędu, dlatego wystąpi błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12f58-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="12f58-120">Określanie granic</span><span class="sxs-lookup"><span data-stu-id="12f58-120">Determining Bounds</span></span>  
 <span data-ttu-id="12f58-121">Jeśli inny składnik przekazuje tablicę do kodu, na przykład jako argument procedury, nie jest znany rozmiar tej tablicy lub długość jej wymiarów.</span><span class="sxs-lookup"><span data-stu-id="12f58-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="12f58-122">Należy zawsze określić górną granicę dla każdego wymiaru tablicy przed podjęciem próby dostępu do dowolnych elementów.</span><span class="sxs-lookup"><span data-stu-id="12f58-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="12f58-123">Jeśli tablica została utworzona za pomocą pewnych metod innych niż `New` klauzula Visual Basic, Dolna granica może być coś innego niż 0 i jest najbezpieczniejsza, aby określić, że jest to Dolna granica.</span><span class="sxs-lookup"><span data-stu-id="12f58-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="12f58-124">Określanie wymiaru</span><span class="sxs-lookup"><span data-stu-id="12f58-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="12f58-125">Podczas określania granic tablicy wielowymiarowej należy zadbać o to, aby określić wymiar.</span><span class="sxs-lookup"><span data-stu-id="12f58-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="12f58-126">`dimension`Parametry <xref:System.Array.GetLowerBound%2A> metody i są oparte na liczbie <xref:System.Array.GetUpperBound%2A> 0, a `Rank` Parametry Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> i <xref:Microsoft.VisualBasic.Information.UBound%2A> funkcje są oparte na liczbie 1.</span><span class="sxs-lookup"><span data-stu-id="12f58-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f58-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12f58-127">See also</span></span>

- [<span data-ttu-id="12f58-128">Tablice</span><span class="sxs-lookup"><span data-stu-id="12f58-128">Arrays</span></span>](index.md)
- [<span data-ttu-id="12f58-129">Porady: inicjowanie zmiennej tablicy w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12f58-129">How to: Initialize an Array Variable in Visual Basic</span></span>](how-to-initialize-an-array-variable.md)
