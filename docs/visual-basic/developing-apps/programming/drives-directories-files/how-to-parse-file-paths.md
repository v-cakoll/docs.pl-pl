---
title: 'Instrukcje: Analizowanie ścieżek pliku w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: c089910e3fd5d02b674cfed3062fb15275d91486
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834611"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Instrukcje: Analizowanie ścieżek pliku w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem> Obiektu udostępnia szereg metod przydatne podczas analizowania ścieżki do plików.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Metoda przyjmuje dwie ścieżki i zwraca poprawnie sformatowanym połączonych ścieżkę.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Metoda zwraca ścieżkę bezwzględną podana ścieżka elementu nadrzędnego.  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Metoda zwraca <xref:System.IO.FileInfo> obiektu, który może być odpytywany, aby określić właściwości pliku, takie jak jego nazwa i ścieżka.  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Aby określić nazwę i ścieżkę pliku  
  
-   Użyj <xref:System.IO.FileInfo.DirectoryName%2A> i <xref:System.IO.FileInfo.Name%2A> właściwości <xref:System.IO.FileInfo> obiektu, aby określić nazwę i ścieżkę pliku. W tym przykładzie określa nazwę i ścieżkę i wyświetla je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Aby połączyć nazwę i katalog, aby utworzyć pełną ścieżkę pliku  
  
-   Użyj `CombinePath` metodę dostarczania katalogu i nazwa. W tym przykładzie pobiera ciągi `folderPath` i `fileName` utworzony w poprzednim przykładzie, łączy je i wyświetla wynik.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Instrukcje: Pobieranie kolekcji plików w katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
