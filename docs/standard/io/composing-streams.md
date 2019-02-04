---
title: Tworzenie strumieni
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 452071e9726a95b4b3d9bb9cefe720d39bbc3e0c
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674350"
---
# <a name="compose-streams"></a>Tworzenie strumieni
A *magazyn zapasowy* się na nośniku, na przykład dysk lub pamięć. Każdy magazyn zapasowy różnych implementuje własne strumienia jako implementacja <xref:System.IO.Stream> klasy. 

Każdy typ strumienia odczytuje i zapisuje bajty od i do jego podanej zapasowego magazynu. Strumienie, łączących się z magazynami kopii są nazywane *podstawowa strumieni*. Podstawowe strumienie mieć konstruktorów z parametrami, które są wymagane do nawiązania strumienia magazyn zapasowy. Na przykład <xref:System.IO.FileStream> ma konstruktorów, które określają parametr ścieżki, która określa, jak plik zostanie udostępniony przez procesy.  

Projekt <xref:System.IO> klasy oferuje uproszczone strumienia kompozycji. Podstawowe strumienie można dołączyć do co najmniej jeden strumień przekazujące, które zapewniają funkcjonalność, którą chcesz. Odczytywania lub zapisywania może dołączać do końca łańcucha, co typy preferowane może odczytać lub zapisywane w prosty sposób.  

Utwórz następujące przykłady kodu **FileStream** wokół istniejącego *mójplik.txt* w kolejności do buforu *mójplik.txt*. Należy pamiętać, że **FileStreams** są buforowane domyślnie.

>[!IMPORTANT]
>W przykładach założono, że plik o nazwie *mójplik.txt* już istnieje w tym samym folderze co aplikacja.  

## <a name="example-use-streamreader"></a>Przykład: Użyj StreamReader
Poniższy przykład tworzy <xref:System.IO.StreamReader> na odczytywanie znaków z **FileStream**, która jest przekazywana do **StreamReader** jako argument konstruktora. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> następnie odczytuje aż <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> znajdzie nie więcej znaków.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Przykład: Użyj BinaryReader
Poniższy przykład tworzy <xref:System.IO.BinaryReader> do odczytywania bajtów z **FileStream**, która jest przekazywana do **BinaryReader** jako argument konstruktora. <xref:System.IO.BinaryReader.ReadByte%2A> następnie odczytuje aż <xref:System.IO.BinaryReader.PeekChar%2A> znajdzie nie większą liczbę bajtów.  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
