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
ms.openlocfilehash: 18f44af81a38a48da3115d2082ef45af39f06529
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291815"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych
<xref:System.IO.BinaryWriter?displayProperty=nameWithType>Klasy i <xref:System.IO.BinaryReader?displayProperty=nameWithType> są używane do zapisywania i odczytywania danych innych niż ciągi znaków. Poniższy przykład pokazuje, jak utworzyć pusty strumień plików, zapisać w nim dane i odczytać z niego dane.

Przykład tworzy plik danych o nazwie *test. Data* w bieżącym katalogu, tworzy skojarzone <xref:System.IO.BinaryWriter> <xref:System.IO.BinaryReader> obiekty i używa <xref:System.IO.BinaryWriter> obiektu, aby napisać liczbę całkowitą od 0 do 10 w celu *przetestowania. dane*, co pozostawia wskaźnik pliku na końcu pliku. <xref:System.IO.BinaryReader>Następnie obiekt ustawia wskaźnik pliku z powrotem do źródła i odczytuje określoną zawartość.  
  
> [!NOTE]
> Jeśli *test. Data* już istnieje w bieżącym katalogu, <xref:System.IO.IOException> zgłaszany jest wyjątek. Użyj opcji Tryb plików <xref:System.IO.FileMode.Create?displayProperty=nameWithType> zamiast tego, <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> Aby zawsze tworzyć nowy plik bez zgłaszania wyjątku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Instrukcje: Wyliczanie katalogów i plików](how-to-enumerate-directories-and-files.md)  
- [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](how-to-open-and-append-to-a-log-file.md)  
- [Instrukcje: odczytywanie tekstu z pliku](how-to-read-text-from-a-file.md)  
- [Instrukcje: wpisywanie tekstu do pliku](how-to-write-text-to-a-file.md)  
- [Instrukcje: odczytywanie znaków z ciągu](how-to-read-characters-from-a-string.md)  
- [Instrukcje: Wpisywanie znaków do ciągu](how-to-write-characters-to-a-string.md)  
- [We/wy plików i strumieni](index.md)
