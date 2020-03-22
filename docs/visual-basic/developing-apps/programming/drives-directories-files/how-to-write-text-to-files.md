---
title: 'Porady: zapisywanie tekstu do plików'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: ce1ee59ba71af6bb13e05a5bce37a2f7eee37712
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334472"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Porady: zapisywanie tekstu do plików w Visual Basic

Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> może służyć do pisania tekstu do plików. Jeśli określony plik nie istnieje, jest tworzony.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-write-text-to-a-file"></a>Aby napisać tekst do pliku  
  
- Użyj `WriteAllText` metody do pisania tekstu do pliku, określając plik i tekst do zapisania. W tym przykładzie `"This is new text."` zapisuje `test.txt`wiersz do pliku o nazwie , dołączając tekst do dowolnego istniejącego tekstu w pliku.  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Aby napisać serię ciągów do pliku  
  
- Pętla za pośrednictwem kolekcji ciągów. Użyj `WriteAllText` metody do pisania tekstu do pliku, określając plik docelowy `append` i `True`ciąg do dodania i ustawienie .  
  
     W tym przykładzie zapisuje nazwy `Documents and Settings` plików `FileList.txt`w katalogu do , wstawiając powrót karetki między każdym dla lepszej czytelności.  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- `File`wskazuje ścieżkę, która nie<xref:System.IO.FileNotFoundException> <xref:System.IO.DirectoryNotFoundException>istnieje ( lub ).  
  
- Plik jest używany przez inny proces lub występuje błąd<xref:System.IO.IOException>we/wy ( ).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).  
  
- Dysk jest zapełniony, `WriteAllText` a<xref:System.IO.IOException>wywołanie nie powiedzie się ( ).  
  
 Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [Jak: Odczyt z plików tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
