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
ms.openlocfilehash: 7b375c5a45998fc0bd06f7c075f23a30dd377295
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Struktury oraz inne elementy programowania (Visual Basic)
Struktury można użyć w połączeniu z tablic, obiektów i procedur, a także ze sobą. Interakcje używać tej samej składni jak te elementy pojedynczo.  
  
> [!NOTE]
>  Nie można zainicjować elementy struktury w deklaracji struktury. Wartości można przypisać tylko do elementów zmiennej, która została zadeklarowana, aby mieć typ struktury.  
  
## <a name="structures-and-arrays"></a>Struktury i tablic  
 Struktura może zawierać tablicę jako co najmniej jeden z jego elementów. Ilustruje to poniższy przykład.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Możesz uzyskać dostęp do wartości tablicy w ramach struktury taki sam sposób uzyskać dostępu do właściwości w obiekcie. Ilustruje to poniższy przykład.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Można również zadeklarować tablicę struktury. Ilustruje to poniższy przykład.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Możesz są zgodne z regułami dostęp do składników tej architektury danych. Ilustruje to poniższy przykład.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Struktury i obiektów  
 Struktura może zawierać obiektu jako co najmniej jeden z jego elementów. Ilustruje to poniższy przykład.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Należy użyć konkretnego obiektu klasy w deklaracji, zamiast `Object`.  
  
## <a name="structures-and-procedures"></a>Struktury i procedury  
 Struktura można przekazać jako argumentu procedury. Ilustruje to poniższy przykład.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 Powyższy przykład przekazuje struktury *przez odwołanie*, dzięki czemu procedury zmodyfikować jego elementy, tak aby zmiany wprowadzone w wywoływanym kodzie. Jeśli chcesz chronić struktury przed zmianami przekazywany przez wartość.  
  
 Można także wrócić struktury z `Function` procedury. Ilustruje to poniższy przykład.  
  
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
  
## <a name="structures-within-structures"></a>Struktury wewnątrz struktur  
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
  
 Ta metoda umożliwia również Hermetyzowanie struktury zdefiniowane w jednym module w ramach struktury zdefiniowane w innym module.  
  
 Struktury mogą zawierać inne struktury dowolnego głębokość.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Zmienne struktur](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [Struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
