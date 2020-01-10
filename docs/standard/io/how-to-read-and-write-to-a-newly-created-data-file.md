---
title: 'Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
ms.openlocfilehash: 0bb06f42542d6acb3214fd4a1a3ca5c54f7caab2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706702"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych
Klasy <xref:System.IO.BinaryWriter?displayProperty=nameWithType> i <xref:System.IO.BinaryReader?displayProperty=nameWithType> są używane do zapisywania i odczytywania danych innych niż ciągi znaków. Poniższy przykład pokazuje, jak utworzyć pusty strumień plików, zapisać w nim dane i odczytać z niego dane. 

Przykład tworzy plik danych o nazwie *test. Data* w bieżącym katalogu, tworzy skojarzone <xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader> obiektów, a następnie używa obiektu <xref:System.IO.BinaryWriter>, aby napisać liczbę całkowitą od 0 do 10 w celu *przetestowania. dane*, co pozostawia wskaźnik pliku na końcu pliku. Obiekt <xref:System.IO.BinaryReader> następnie ustawia wskaźnik pliku z powrotem do źródła i odczytuje określoną zawartość.  
  
> [!NOTE]
> Jeśli *test. Data* już istnieje w bieżącym katalogu, zostanie zgłoszony wyjątek <xref:System.IO.IOException>. Użyj opcji Tryb plików <xref:System.IO.FileMode.Create?displayProperty=nameWithType>, a nie <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType>, aby zawsze tworzyć nowy plik bez zgłaszania wyjątku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Instrukcje: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Instrukcje: wpisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Instrukcje: Wpisywanie znaków do ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
