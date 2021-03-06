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
# <a name="structures-and-other-programming-elements-visual-basic"></a>Struktury oraz inne elementy programowania (Visual Basic)
Można używać struktur w połączeniu z tablicami, obiektami i procedurami, a także ze sobą. Interakcje używają tej samej składni, w której te elementy używają pojedynczo.  
  
> [!NOTE]
> Nie można zainicjować któregokolwiek z elementów struktury w deklaracji struktury. Wartości można przypisywać tylko do elementów zmiennej, która została zadeklarowana jako typu struktury.  
  
## <a name="structures-and-arrays"></a>Struktury i tablice  
 Struktura może zawierać tablicę jako jeden lub kilka jej elementów. Ilustruje to poniższy przykład.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 Dostęp do wartości tablicy w strukturze jest taki sam jak w przypadku dostępu do właściwości obiektu. Ilustruje to poniższy przykład.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Można również zadeklarować tablicę struktur. Ilustruje to poniższy przykład.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Aby uzyskać dostęp do składników tej architektury danych, należy przestrzegać tych samych reguł. Ilustruje to poniższy przykład.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Struktury i obiekty  
 Struktura może zawierać obiekt jako jeden lub więcej elementów. Ilustruje to poniższy przykład.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Należy użyć określonej klasy obiektów w takiej deklaracji, a nie `Object` .  
  
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
  
 Powyższy przykład przekazuje strukturę *przez odwołanie*, co umożliwia wykonanie procedury modyfikacji jej elementów w celu wprowadzenia zmian w kodzie wywołującym. Jeśli chcesz chronić strukturę przed taką modyfikacją, przekaż ją przez wartość.  
  
 Możesz również zwrócić strukturę z `Function` procedury. Ilustruje to poniższy przykład.  
  
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
  
 Tej techniki można również użyć do hermetyzacji struktury zdefiniowanej w jednym module w strukturze zdefiniowanej w innym module.  
  
 Struktury mogą zawierać inne struktury do arbitralnej głębokości.  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](index.md)
- [Typy danych podstawowych](elementary-data-types.md)
- [Złożone typy danych](composite-data-types.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Struktury](structures.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Instrukcje: Deklarowanie struktury](how-to-declare-a-structure.md)
- [Zmienne struktur](structure-variables.md)
- [Struktury i klasy](structures-and-classes.md)
- [Structure — Instrukcja](../../../language-reference/statements/structure-statement.md)
