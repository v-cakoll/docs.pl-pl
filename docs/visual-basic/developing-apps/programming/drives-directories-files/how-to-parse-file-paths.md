---
title: 'Porady: analizowanie ścieżek pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6a959994be3a57795dc9f7e3447fa54bf075d3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335352"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Porady: analizowanie ścieżek pliku w Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem> Obiekt oferuje wiele przydatnych metod podczas analizowania ścieżek plików.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Metoda przyjmuje dwie ścieżki i zwraca prawidłowo sformatowaną ścieżkę połączonej.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Metoda zwraca ścieżkę bezwzględną elementu nadrzędnego dla podanej ścieżki.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Metoda zwraca <xref:System.IO.FileInfo> obiekt, który można zbadać, aby określić właściwości pliku, takie jak jego nazwa i ścieżka.  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Aby określić nazwę i ścieżkę pliku  
  
- Użyj właściwości <xref:System.IO.FileInfo.DirectoryName%2A> i <xref:System.IO.FileInfo.Name%2A> <xref:System.IO.FileInfo> obiektu, aby określić nazwę i ścieżkę pliku. Ten przykład określa nazwę i ścieżkę oraz wyświetla je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Aby połączyć nazwę i katalog pliku w celu utworzenia pełnej ścieżki  
  
- Użyj `CombinePath` metody, podając katalog i nazwę. Ten przykład pobiera ciągi `folderPath` i `fileName` tworzy w poprzednim przykładzie, łączy je i wyświetla wynik.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Porady: pobieranie kolekcji plików z katalogu w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
