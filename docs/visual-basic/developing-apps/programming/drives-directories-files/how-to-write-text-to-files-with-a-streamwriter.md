---
title: 'Porady: zapisywanie tekstu do plików za pomocą StreamWriter'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334497"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic

Ten przykład otwiera obiekt <xref:System.IO.StreamWriter> przy użyciu metody `My.Computer.FileSystem.OpenTextFileWriter` i używa jej do pisania ciągu do pliku tekstowego z metodą <xref:System.IO.TextWriter.WriteLine%2A> klasy <xref:System.IO.StreamWriter>.  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).  
  
- Dysk jest pełny (<xref:System.IO.IOException>).  
  
- Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  

 Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja wymaga `Create` dostępu do folderu. Jeśli plik już istnieje, aplikacja wymaga tylko `Write` dostępu, ale ma mniejsze uprawnienia. Jeśli to możliwe, bezpieczniejsze jest tworzenie plików podczas wdrażania i udzielanie `Read` dostęp do pojedynczego pliku, a nie `Create` dostępu do folderu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Instrukcje: odczyt z plików tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
