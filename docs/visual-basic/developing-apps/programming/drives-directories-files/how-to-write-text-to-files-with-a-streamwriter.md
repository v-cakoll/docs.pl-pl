---
title: 'Instrukcje: Zapisywanie tekstu w plikach za pomocą StreamWriter'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 373f3bd07ea61263ddd81037d8cbbb06f789e599
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411580"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic

Ten przykład otwiera <xref:System.IO.StreamWriter> obiekt z `My.Computer.FileSystem.OpenTextFileWriter` metodą i używa go do pisania ciągu do pliku tekstowego z <xref:System.IO.TextWriter.WriteLine%2A> metodą <xref:System.IO.StreamWriter> klasy.  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Plik istnieje i jest tylko do odczytu ( <xref:System.IO.IOException> ).  
  
- Dysk jest pełny ( <xref:System.IO.IOException> ).  
  
- Nazwa ścieżki jest za długa ( <xref:System.IO.PathTooLongException> ).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, aplikacja musi `Create` mieć dostęp do tego folderu. Jeśli plik już istnieje, aplikacja wymaga tylko `Write` dostępu, ale ma mniejsze uprawnienia. Jeśli to możliwe, bezpieczniejsze jest tworzenie pliku podczas wdrażania i udzielanie `Read` dostępu do pojedynczego pliku, a nie `Create` dostęp do folderu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Instrukcje: odczyt z plików tekstowych](how-to-read-from-text-files.md)
- [Zapisywanie w plikach](writing-to-files.md)
