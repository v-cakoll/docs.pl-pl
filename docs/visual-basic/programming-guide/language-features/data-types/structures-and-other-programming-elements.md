---
title: Struktury oraz inne elementy programowania
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: dbd24065a954e5611663963371d5a9f4bbbaea68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393497"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="0bbcb-102">Struktury oraz inne elementy programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bbcb-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="0bbcb-103">Można używać struktur w połączeniu z tablicami, obiektami i procedurami, a także ze sobą.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="0bbcb-104">Interakcje używają tej samej składni, w której te elementy używają pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bbcb-105">Nie można zainicjować któregokolwiek z elementów struktury w deklaracji struktury.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="0bbcb-106">Wartości można przypisywać tylko do elementów zmiennej, która została zadeklarowana jako typu struktury.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="0bbcb-107">Struktury i tablice</span><span class="sxs-lookup"><span data-stu-id="0bbcb-107">Structures and Arrays</span></span>  
 <span data-ttu-id="0bbcb-108">Struktura może zawierać tablicę jako jeden lub kilka jej elementów.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="0bbcb-109">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 <span data-ttu-id="0bbcb-110">Dostęp do wartości tablicy w strukturze jest taki sam jak w przypadku dostępu do właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="0bbcb-111">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="0bbcb-112">Można również zadeklarować tablicę struktur.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-112">You can also declare an array of structures.</span></span> <span data-ttu-id="0bbcb-113">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="0bbcb-114">Aby uzyskać dostęp do składników tej architektury danych, należy przestrzegać tych samych reguł.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="0bbcb-115">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="0bbcb-116">Struktury i obiekty</span><span class="sxs-lookup"><span data-stu-id="0bbcb-116">Structures and Objects</span></span>  
 <span data-ttu-id="0bbcb-117">Struktura może zawierać obiekt jako jeden lub więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="0bbcb-118">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="0bbcb-119">Należy użyć określonej klasy obiektów w takiej deklaracji, a nie `Object` .</span><span class="sxs-lookup"><span data-stu-id="0bbcb-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="0bbcb-120">Struktury i procedury</span><span class="sxs-lookup"><span data-stu-id="0bbcb-120">Structures and Procedures</span></span>  
 <span data-ttu-id="0bbcb-121">Strukturę można przekazać jako argument procedury.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="0bbcb-122">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="0bbcb-123">Powyższy przykład przekazuje strukturę *przez odwołanie*, co umożliwia wykonanie procedury modyfikacji jej elementów w celu wprowadzenia zmian w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="0bbcb-124">Jeśli chcesz chronić strukturę przed taką modyfikacją, przekaż ją przez wartość.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="0bbcb-125">Możesz również zwrócić strukturę z `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="0bbcb-126">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="0bbcb-127">Struktury w strukturach</span><span class="sxs-lookup"><span data-stu-id="0bbcb-127">Structures Within Structures</span></span>  
 <span data-ttu-id="0bbcb-128">Struktury mogą zawierać inne struktury.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-128">Structures can contain other structures.</span></span> <span data-ttu-id="0bbcb-129">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="0bbcb-130">Tej techniki można również użyć do hermetyzacji struktury zdefiniowanej w jednym module w strukturze zdefiniowanej w innym module.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="0bbcb-131">Struktury mogą zawierać inne struktury do arbitralnej głębokości.</span><span class="sxs-lookup"><span data-stu-id="0bbcb-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bbcb-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bbcb-132">See also</span></span>

- [<span data-ttu-id="0bbcb-133">Typy danych</span><span class="sxs-lookup"><span data-stu-id="0bbcb-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="0bbcb-134">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="0bbcb-134">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="0bbcb-135">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="0bbcb-135">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="0bbcb-136">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="0bbcb-136">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="0bbcb-137">Struktury</span><span class="sxs-lookup"><span data-stu-id="0bbcb-137">Structures</span></span>](structures.md)
- [<span data-ttu-id="0bbcb-138">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="0bbcb-138">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="0bbcb-139">Instrukcje: Deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="0bbcb-139">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="0bbcb-140">Zmienne struktur</span><span class="sxs-lookup"><span data-stu-id="0bbcb-140">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="0bbcb-141">Struktury i klasy</span><span class="sxs-lookup"><span data-stu-id="0bbcb-141">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="0bbcb-142">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="0bbcb-142">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
