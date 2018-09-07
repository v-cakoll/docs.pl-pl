---
title: 'Porady: odczyt i zapis we właśnie utworzonym pliku danych'
ms.date: 03/30/2017
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
ms.openlocfilehash: 65c56a11531f705b7e047e435ec575969d39a616
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071378"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Porady: odczyt i zapis we właśnie utworzonym pliku danych
<xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader?displayProperty=nameWithType> klasy są używane do zapisywania i odczytywania danych, a nie ciągi znaków. Poniższy przykład pokazuje, jak zapisywać danych i odczytywanie danych ze strumienia nowy, pusty plik o nazwie `Test.data`. Po utworzeniu pliku danych w bieżącym katalogu skojarzonego <xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader> są tworzone obiekty i <xref:System.IO.BinaryWriter> obiekt jest używany do zapisywania liczby całkowite 0 do 10, aby `Test.data`, która pozostawia na końcu wskaźnika pliku plik. Po ustawieniu wskaźnika pliku z powrotem do źródła, <xref:System.IO.BinaryReader> obiektu odczytuje się określonej zawartości.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli `Test.data` już istnieje w bieżącym katalogu <xref:System.IO.IOException> wyjątku. Użyj opcji Tryb pliku <xref:System.IO.FileMode.Create?displayProperty=nameWithType> podczas inicjowania strumienia pliku, aby zawsze tworzyć nowy plik bez zgłoszenia wyjątku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Instrukcje: wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Instrukcje: zapisywanie tekstu w pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Instrukcje: zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
