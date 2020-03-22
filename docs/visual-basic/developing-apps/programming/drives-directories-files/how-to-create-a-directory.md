---
title: 'Porady: tworzenie katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348810"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Porady: tworzenie katalogu w Visual Basic

Użyj `CreateDirectory` metody obiektu, `My.Computer.FileSystem` aby utworzyć katalogi.  
  
 Jeśli katalog już istnieje, nie jest zgłaszany wyjątek.  
  
### <a name="to-create-a-directory"></a>Aby utworzyć katalog  
  
- Użyj `CreateDirectory` tej metody, określając pełną ścieżkę lokalizacji, w której ma zostać utworzony katalog. W tym przykładzie `NewDirectory` `C:\Documents and Settings\All Users\Documents`tworzy katalog w .  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa katalogu jest zniekształcona. Na przykład zawiera nielegalne znaki lub jest<xref:System.ArgumentException>tylko biały znak ( ).  
  
- Katalog nadrzędny katalogu, który ma zostać utworzony,<xref:System.IO.IOException>jest tylko do odczytu ( ).  
  
- Nazwa katalogu jest `Nothing` <xref:System.ArgumentNullException>( ).  
  
- Nazwa katalogu jest za<xref:System.IO.PathTooLongException>długa ( ).  
  
- Nazwa katalogu to dwukropek<xref:System.NotSupportedException>":" ( ).  
  
- Użytkownik nie ma uprawnień do tworzenia<xref:System.UnauthorizedAccessException>katalogu ( ).  
  
- Użytkownik nie ma uprawnień w sytuacji<xref:System.Security.SecurityException>częściowego zaufania ( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Tworzenie, usuwanie i przenoszenie plików i katalogów](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
