---
title: Struktury oraz inne elementy programowania (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: a943bbdec617ba6c95685df3a4fcdb36b52def22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819112"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="e691f-102">Struktury oraz inne elementy programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e691f-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="e691f-103">Struktury można użyć w połączeniu z tablicami, obiektów i procedur, a także ze sobą.</span><span class="sxs-lookup"><span data-stu-id="e691f-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="e691f-104">Interakcje używać tej samej składni, ponieważ te elementy używane pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="e691f-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e691f-105">Nie można zainicjować elementy struktury w deklaracji struktury.</span><span class="sxs-lookup"><span data-stu-id="e691f-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="e691f-106">Wartości można przypisać tylko do elementów w zmiennej, która została zadeklarowana jako typu struktury.</span><span class="sxs-lookup"><span data-stu-id="e691f-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="e691f-107">Struktury i tablice</span><span class="sxs-lookup"><span data-stu-id="e691f-107">Structures and Arrays</span></span>  
 <span data-ttu-id="e691f-108">Struktura może zawierać tablicę jako co najmniej jeden z jego elementów.</span><span class="sxs-lookup"><span data-stu-id="e691f-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="e691f-109">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e691f-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="e691f-110">Możesz uzyskać dostęp do wartości tablicy w ramach struktury taki sam sposób, możesz uzyskać dostęp do właściwości w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e691f-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="e691f-111">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e691f-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="e691f-112">Można również zadeklarować tablicy struktur.</span><span class="sxs-lookup"><span data-stu-id="e691f-112">You can also declare an array of structures.</span></span> <span data-ttu-id="e691f-113">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e691f-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="e691f-114">Postępuj zgodnie z tych samych zasad dostępu składniki tej architektury danych.</span><span class="sxs-lookup"><span data-stu-id="e691f-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="e691f-115">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e691f-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="e691f-116">Struktury i obiekty</span><span class="sxs-lookup"><span data-stu-id="e691f-116">Structures and Objects</span></span>  
 <span data-ttu-id="e691f-117">Struktura może zawierać obiektu jako co najmniej jeden z jego elementów.</span><span class="sxs-lookup"><span data-stu-id="e691f-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="e691f-118">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e691f-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="e691f-119">Klasa określonego obiektu należy używać w deklaracji, zamiast `Object`.</span><span class="sxs-lookup"><span data-stu-id="e691f-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="e691f-120">Struktury i procedury</span><span class="sxs-lookup"><span data-stu-id="e691f-120">Structures and Procedures</span></span>  
 <span data-ttu-id="e691f-121">Struktura można przekazać jako argument procedury.</span><span class="sxs-lookup"><span data-stu-id="e691f-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="e691f-122">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e691f-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="e691f-123">Poprzedni przykład przekazuje strukturę *przez odwołanie*, co pozwala procedury zmodyfikować jego elementy, tak, aby zmiany zostały wprowadzone w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e691f-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="e691f-124">Jeśli chcesz chronić strukturę przed zmianami, przekazywać wg wartości.</span><span class="sxs-lookup"><span data-stu-id="e691f-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="e691f-125">Możesz też zwrócić struktury z `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="e691f-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="e691f-126">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e691f-126">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="e691f-127">Struktury w ramach struktury</span><span class="sxs-lookup"><span data-stu-id="e691f-127">Structures Within Structures</span></span>  
 <span data-ttu-id="e691f-128">Struktury mogą zawierać inne struktury.</span><span class="sxs-lookup"><span data-stu-id="e691f-128">Structures can contain other structures.</span></span> <span data-ttu-id="e691f-129">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e691f-129">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="e691f-130">Ta metoda umożliwia również hermetyzacji struktury zdefiniowany w jeden moduł w ramach struktury zdefiniowany w oddzielnym modułem.</span><span class="sxs-lookup"><span data-stu-id="e691f-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="e691f-131">Struktury mogą zawierać inne struktury dowolnego głębokość.</span><span class="sxs-lookup"><span data-stu-id="e691f-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e691f-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e691f-132">See also</span></span>

- [<span data-ttu-id="e691f-133">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e691f-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="e691f-134">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="e691f-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="e691f-135">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="e691f-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="e691f-136">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="e691f-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="e691f-137">Struktury</span><span class="sxs-lookup"><span data-stu-id="e691f-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="e691f-138">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="e691f-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="e691f-139">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="e691f-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="e691f-140">Zmienne struktur</span><span class="sxs-lookup"><span data-stu-id="e691f-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="e691f-141">Struktury i klasy</span><span class="sxs-lookup"><span data-stu-id="e691f-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="e691f-142">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e691f-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
