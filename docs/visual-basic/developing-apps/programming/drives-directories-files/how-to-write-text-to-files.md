---
title: 'Instrukcje: Zapisywanie tekstu w plikach'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: f95a0c4df4a2eab0069a6dab0d4c3fa338d1d8ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411541"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Porady: zapisywanie tekstu do plików w Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Metoda może służyć do zapisywania tekstu do plików. Jeśli określony plik nie istnieje, zostanie utworzony.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-write-text-to-a-file"></a>Aby zapisać tekst do pliku  
  
- Użyj `WriteAllText` metody, aby zapisać tekst do pliku, określając plik i tekst do zapisania. Ten przykład zapisuje wiersz `"This is new text."` do pliku o nazwie `test.txt` , dołączając tekst do dowolnego istniejącego tekstu w pliku.  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Aby napisać serię ciągów do pliku  
  
- Pętla w kolekcji ciągów. Użyj `WriteAllText` metody, aby zapisać tekst do pliku, określając docelowy plik i ciąg, który ma zostać dodany i ustawienie `append` `True` .  
  
     Ten przykład zapisuje nazwy plików w `Documents and Settings` katalogu do `FileList.txt` , wstawiając znak powrotu karetki między nimi w celu zwiększenia czytelności.  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- `File`wskazuje ścieżkę, która nie istnieje ( <xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException> ).  
  
- Plik jest używany przez inny proces lub wystąpił błąd we/wy ( <xref:System.IO.IOException> ).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).  
  
- Dysk jest zapełniony i wywołanie metody `WriteAllText` nie powiodło się ( <xref:System.IO.IOException> ).  
  
 Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [Instrukcje: odczyt z plików tekstowych](how-to-read-from-text-files.md)
