---
title: 'Instrukcje: Dołączanie do plików tekstowych'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 53b2e4c9030e9d1dd81a4121ad3f92aad796e3e1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359958"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Porady: łączenie się plikami tekstowymi w Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Metoda może służyć do dołączania do pliku tekstowego przez określenie, że `append` parametr jest ustawiony na `True` .  
  
### <a name="to-append-to-a-text-file"></a>Aby dołączyć do pliku tekstowego  
  
- Użyj `WriteAllText` metody, określając docelowy plik i ciąg do dołączenia, a następnie ustaw `append` parametr na `True` .  
  
     Ten przykład zapisuje ciąg `"This is a test string."` do pliku o nazwie `Testfile.txt` .  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- `File`wskazuje ścieżkę, która nie istnieje ( <xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException> ).  
  
- Plik jest używany przez inny proces lub wystąpił błąd we/wy ( <xref:System.IO.IOException> ).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Zapisywanie w plikach](writing-to-files.md)
