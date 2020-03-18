---
title: 'Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych'
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
ms.openlocfilehash: 3772aeeb25d1251a13fde2a0e51a913e5e39eabc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155753"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych
I <xref:System.IO.BinaryWriter?displayProperty=nameWithType> <xref:System.IO.BinaryReader?displayProperty=nameWithType> klasy są używane do zapisywania i odczytywania danych innych niż ciągi znaków. W poniższym przykładzie pokazano, jak utworzyć pusty strumień plików, zapisać do niego dane i odczytać z niego dane.

Przykład tworzy plik danych o nazwie *Test.data* w <xref:System.IO.BinaryWriter> bieżącym <xref:System.IO.BinaryReader> katalogu, tworzy <xref:System.IO.BinaryWriter> skojarzone i obiekty i używa obiektu do zapisu liczb całkowitych od 0 do 10 do *Test.data*, który pozostawia wskaźnik pliku na końcu pliku. Następnie <xref:System.IO.BinaryReader> obiekt ustawia wskaźnik pliku z powrotem do początku i odczytuje określoną zawartość.  
  
> [!NOTE]
> Jeśli *Test.data* już istnieje w <xref:System.IO.IOException> bieżącym katalogu, wyjątek. Użyj opcji <xref:System.IO.FileMode.Create?displayProperty=nameWithType> trybu pliku, <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> a nie zawsze utworzyć nowy plik bez zgłaszania wyjątku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Jak: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Jak: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Jak: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Jak: Napisać tekst do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Jak: Odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Jak: Zapisywać znaki do ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Plik i strumień we/wy](../../../docs/standard/io/index.md)
