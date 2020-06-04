---
title: 'Instrukcje: Analizowanie ścieżek plików'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: eb7714a8594c0bce344eb2e48ebc5053dc3bfbb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359945"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Porady: analizowanie ścieżek pliku w Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem>Obiekt oferuje wiele przydatnych metod podczas analizowania ścieżek plików.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>Metoda przyjmuje dwie ścieżki i zwraca prawidłowo sformatowaną ścieżkę połączonej.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A>Metoda zwraca ścieżkę bezwzględną elementu nadrzędnego dla podanej ścieżki.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>Metoda zwraca obiekt, <xref:System.IO.FileInfo> który można zbadać, aby określić właściwości pliku, takie jak jego nazwa i ścieżka.  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Aby określić nazwę i ścieżkę pliku  
  
- Użyj <xref:System.IO.FileInfo.DirectoryName%2A> właściwości i <xref:System.IO.FileInfo.Name%2A> <xref:System.IO.FileInfo> obiektu, aby określić nazwę i ścieżkę pliku. Ten przykład określa nazwę i ścieżkę oraz wyświetla je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Aby połączyć nazwę i katalog pliku w celu utworzenia pełnej ścieżki  
  
- Użyj `CombinePath` metody, podając katalog i nazwę. Ten przykład pobiera ciągi `folderPath` i `fileName` tworzy w poprzednim przykładzie, łączy je i wyświetla wynik.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Instrukcje: Pobieranie kolekcji plików z katalogu](how-to-get-the-collection-of-files-in-a-directory.md)
