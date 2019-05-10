---
title: 'Instrukcje: Utwórz katalog w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 54696dab41c99774bb3638e0c19837a906144d27
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64629075"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Instrukcje: Utwórz katalog w języku Visual Basic
Użyj `CreateDirectory` metody `My.Computer.FileSystem` obiekt do tworzenia katalogów.  
  
 Jeśli katalog już istnieje, jest zgłaszany żaden wyjątek.  
  
### <a name="to-create-a-directory"></a>Aby utworzyć katalog  
  
- Użyj `CreateDirectory` metody, podając pełną ścieżkę lokalizacji, w którym można utworzyć katalogu. W tym przykładzie tworzy katalog `NewDirectory` w `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa katalogu jest nieprawidłowo sformułowany. Na przykład zawiera niedozwolone znaki lub jest tylko spacją (<xref:System.ArgumentException>).  
  
- Katalog, który ma zostać utworzony w katalogu nadrzędnym jest tylko do odczytu (<xref:System.IO.IOException>).  
  
- Nazwa katalogu jest `Nothing` (<xref:System.ArgumentNullException>).  
  
- Nazwa katalogu jest zbyt długa (<xref:System.IO.PathTooLongException>).  
  
- Nazwa katalogu jest dwukropek ":" (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma uprawnień do tworzenia katalogu (<xref:System.UnauthorizedAccessException>).  
  
- Użytkownik nie ma uprawnienia w sytuacjach częściowego zaufania (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Tworzenie, usuwanie i przenoszenie plików i katalogów](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
