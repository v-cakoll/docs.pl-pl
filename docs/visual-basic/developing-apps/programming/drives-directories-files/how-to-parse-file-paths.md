---
title: "Porady: analizowanie ścieżek pliku w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 913fe45cf6fc7afdc6e0f31e028bc18808cecf89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Porady: analizowanie ścieżek pliku w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem> Obiekt oferuje wiele metod przydatne podczas analizowania ścieżki do pliku.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Metoda ma dwie ścieżki i zwraca poprawnie sformatowana połączone ścieżki.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> — Metoda zwraca ścieżkę bezwzględną elementu nadrzędnego podana ścieżka.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Metoda zwraca <xref:System.IO.FileInfo> obiekt, który można wykonać zapytania, aby określić właściwości pliku, takie jak jego nazwa i ścieżka.  
  
 Nie należy wprowadzać decyzje dotyczące zawartości pliku, na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb nie może być plik źródłowy języka Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Aby określić nazwę pliku i ścieżkę  
  
-   Użyj <xref:System.IO.FileInfo.DirectoryName%2A> i <xref:System.IO.FileInfo.Name%2A> właściwości <xref:System.IO.FileInfo> obiektem, aby określić nazwę pliku i ścieżkę. W tym przykładzie określa nazwę i ścieżkę i wyświetla je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Aby połączyć nazwy i katalog, aby utworzyć pełną ścieżkę pliku  
  
-   Użyj `CombinePath` metody dostarczania katalogu i nazwę. W tym przykładzie przyjmuje ciągi `folderPath` i `fileName` utworzony w poprzednim przykładzie, łączy je i wyświetla wyniki.  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [Porady: pobieranie kolekcji plików z katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
