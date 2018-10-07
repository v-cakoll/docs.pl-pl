---
title: Tworzenie strumieni
ms.date: 03/30/2017
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
ms.openlocfilehash: 5e52b827f337892c33ec61b9affa1cc646a759c5
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841180"
---
# <a name="composing-streams"></a>Tworzenie strumieni
Magazyn zapasowy jest na nośniku, na przykład dysk lub pamięć. Każdy magazyn zapasowy różnych implementuje własne strumienia jako implementacja <xref:System.IO.Stream> klasy. Każdy typ strumienia odczytuje i zapisuje bajty od i do jego podanej zapasowego magazynu. Strumienie, łączących się z magazynami kopii są nazywane podstawowe strumienie. Podstawowe strumienie ma konstruktorów, które mają parametry, które są wymagane do nawiązania strumienia magazyn zapasowy. Na przykład <xref:System.IO.FileStream> ma konstruktorów, które określają parametr ścieżki, która określa, jak plik zostanie udostępniony przez procesy i tak dalej.  
  
 Projekt <xref:System.IO> klasy oferuje uproszczone strumienia redagowania. Podstawowe strumienie można dołączyć do co najmniej jeden strumień przekazujące, które zapewniają funkcjonalność, którą chcesz. Odczytywania lub zapisywania można dołączyć do końca łańcucha tak, aby typy preferowane może odczytać lub zapisywane w prosty sposób.  
  
 Poniższy przykład kodu tworzy **FileStream** wokół istniejącego `MyFile.txt` w kolejności do buforu `MyFile.txt`. (Należy pamiętać, że **FileStreams** są buforowane domyślnie.) Następnie <xref:System.IO.StreamReader> jest tworzony na odczytywanie znaków z **FileStream**, która jest przekazywana do **StreamReader** jako argument konstruktora. <xref:System.IO.StreamReader.ReadLine%2A> odczytuje do momentu <xref:System.IO.StreamReader.Peek%2A> znajdzie nie więcej znaków.  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 Poniższy przykład kodu tworzy **FileStream** wokół istniejącego `MyFile.txt` w kolejności do buforu `MyFile.txt`. (Należy pamiętać, że **FileStreams** są buforowane domyślnie.) Następnie **BinaryReader** służy do odczytywania bajtów z **FileStream**, która jest przekazywana do **BinaryReader** jako argument konstruktora. <xref:System.IO.BinaryReader.ReadByte%2A> odczytuje do momentu <xref:System.IO.BinaryReader.PeekChar%2A> znajdzie nie większą liczbę bajtów.  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
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
