---
title: 'Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 4cb589125286082b9c7d5886a51b0ef8d998474e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583347"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic
W tym przykładzie otwiera <xref:System.IO.StreamWriter> obiekt z `My.Computer.FileSystem.OpenTextFileWriter` — metoda i używa go do zapisu do pliku tekstowego z ciągiem <xref:System.IO.TextWriter.WriteLine%2A> metody <xref:System.IO.StreamWriter> klasy.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).  
  
-   Dysk jest pełny (<xref:System.IO.IOException>).  
  
-   Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje. Jeśli aplikacja musi utworzyć plik, że aplikacja musi `Create` dostępu do folderu. Jeśli plik już istnieje, aplikacja musi tylko `Write` dostępu niższego poziomu uprawnień. Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` dostęp do jednego pliku, a nie `Create` dostępu dla folderu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [Porady: Odczyt z plików tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
