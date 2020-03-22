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
ms.openlocfilehash: 73d3f999e95c484dff3f5409f2cdb9032b64fe38
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266862"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Struktury oraz inne elementy programowania (Visual Basic)
Można używać struktur w połączeniu z tablicami, obiektami i procedurami, a także ze sobą. Interakcje używają tej samej składni, co te elementy używają indywidualnie.  
  
> [!NOTE]
> Nie można zainicjować żadnych elementów struktury w deklaracji struktury. Wartości można przypisać tylko do elementów zmiennej, która została zadeklarowana jako typu struktury.  
  
## <a name="structures-and-arrays"></a>Struktury i tablice  
 Struktura może zawierać tablicę jako jeden lub więcej jej elementów. Ilustruje to poniższy przykład.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 Dostęp do wartości tablicy w strukturze w taki sam sposób, jak dostęp do właściwości na obiekcie. Ilustruje to poniższy przykład.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Można również zadeklarować tablicę struktur. Ilustruje to poniższy przykład.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Należy przestrzegać tych samych reguł, aby uzyskać dostęp do składników tej architektury danych. Ilustruje to poniższy przykład.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Struktury i obiekty  
 Struktura może zawierać obiekt jako jeden lub więcej jego elementów. Ilustruje to poniższy przykład.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 W takiej deklaracji należy użyć określonej klasy `Object`obiektu, a nie .  
  
## <a name="structures-and-procedures"></a>Struktury i procedury  
 Strukturę można przekazać jako argument procedury. Ilustruje to poniższy przykład.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 W poprzednim przykładzie przekazuje strukturę *przez odwołanie*, co pozwala procedurze zmodyfikować jego elementy, tak aby zmiany zostały wprowadzone w kodzie wywołującym. Jeśli chcesz chronić strukturę przed taką modyfikacją, przekaż ją przez wartość.  
  
 Można również zwrócić strukturę `Function` z procedury. Ilustruje to poniższy przykład.  
  
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
  
## <a name="structures-within-structures"></a>Struktury w strukturach  
 Struktury mogą zawierać inne struktury. Ilustruje to poniższy przykład.  
  
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
  
 Można również użyć tej techniki do hermetyzacji struktury zdefiniowanej w jednym module w strukturze zdefiniowanej w innym module.  
  
 Struktury mogą zawierać inne struktury do dowolnej głębokości.  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Zmienne struktur](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure — Instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
