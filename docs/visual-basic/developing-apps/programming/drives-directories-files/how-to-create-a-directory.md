---
title: 'Instrukcje: Tworzenie katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 0da915054a2e38c778f15bc0b472fe9b02521189
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401670"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Porady: tworzenie katalogu w Visual Basic

Użyj `CreateDirectory` metody `My.Computer.FileSystem` obiektu do tworzenia katalogów.  
  
 Jeśli katalog już istnieje, nie jest zgłaszany żaden wyjątek.  
  
### <a name="to-create-a-directory"></a>Aby utworzyć katalog  
  
- Użyj `CreateDirectory` metody, określając pełną ścieżkę lokalizacji, w której ma zostać utworzony katalog. Ten przykład tworzy katalog `NewDirectory` w `C:\Documents and Settings\All Users\Documents` .  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa katalogu jest nieprawidłowo sformułowana. Na przykład zawiera niedozwolone znaki lub jest tylko białym znakiem ( <xref:System.ArgumentException> ).  
  
- Katalog nadrzędny katalogu, który ma zostać utworzony, jest tylko do odczytu ( <xref:System.IO.IOException> ).  
  
- Nazwa katalogu to `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Nazwa katalogu jest za długa ( <xref:System.IO.PathTooLongException> ).  
  
- Nazwa katalogu jest dwukropek ":" ( <xref:System.NotSupportedException> ).  
  
- Użytkownik nie ma uprawnienia do tworzenia katalogu ( <xref:System.UnauthorizedAccessException> ).  
  
- Użytkownik nie ma uprawnień w sytuacji częściowej zaufania ( <xref:System.Security.SecurityException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Tworzenie, usuwanie i przenoszenie plików i katalogów](creating-deleting-and-moving-files-and-directories.md)
