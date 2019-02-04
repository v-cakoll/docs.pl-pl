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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 065907ae0d4a38ff2ef68de6025251e28220ee96
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674623"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych
<xref:System.IO.BinaryWriter?displayProperty=nameWithType> i <xref:System.IO.BinaryReader?displayProperty=nameWithType> klasy są używane do zapisywania i odczytywania danych innych niż ciągi znaków. Poniższy przykład pokazuje, jak utworzyć pusty plik strumienia w nim zapisywać dane i odczytywać dane. 

Przykład tworzy plik danych o nazwie *Test.data* w bieżącym katalogu, tworzy skojarzonego <xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader> obiektów i używa <xref:System.IO.BinaryWriter> obiektu do zapisania liczbami całkowitymi od 0 do 10 na *Test.data*, dlatego wskaźnikiem pliku, na końcu pliku. <xref:System.IO.BinaryReader> Obiektu następnie ustawia wskaźnik pliku źródła i odczytuje się określonej zawartości.  
  
> [!NOTE]
> Jeśli *Test.data* już istnieje w bieżącym katalogu <xref:System.IO.IOException> wyjątku. Użyj opcji Tryb pliku <xref:System.IO.FileMode.Create?displayProperty=nameWithType> zamiast <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> zawsze utworzyć nowy plik bez zgłoszenia wyjątku.  
  
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
- [Instrukcje: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Instrukcje: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Instrukcje: Zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: Odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Instrukcje: Zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
