---
title: Tworzenie strumieni
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d49661e93675b80bcd579a6cd341b3dc88a688c2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="composing-streams"></a>Tworzenie strumieni
Magazynu zapasowego jest nośniku, takie jak dysk lub pamięci. Każdy magazyn zapasowy różnych implementuje własną strumienia jako implementacja <xref:System.IO.Stream> klasy. Każdy typ strumienia odczytuje i zapisuje bajty od i do jego magazynu zapasowego danego. Strumienie łączący się tworzenie kopii magazynów są nazywane podstawowe strumienie. Podstawowe strumienie mieć konstruktorów, które mają parametry niezbędne do nawiązania połączenia magazynu zapasowego strumienia. Na przykład <xref:System.IO.FileStream> ma konstruktorów określić parametr path, która określa, jak plik zostanie udostępniony przez procesy i tak dalej.  
  
 Projekt <xref:System.IO> klasy zawiera redagowania uproszczony strumienia. Podstawowe strumienie może zostać dołączona do co najmniej jeden strumieni przekazujące, które udostępniają funkcje, które mają. Odczytywania lub zapisywania może zostać dołączona na końcu łańcucha, tak aby typy preferowane można odczytu lub zapisu w prosty sposób.  
  
 Poniższy przykład kodu tworzy **FileStream** wokół istniejące `MyFile.txt` w kolejności do buforu `MyFile.txt`. (Należy pamiętać, że **FileStreams** są buforowane domyślnie.) Następnie <xref:System.IO.StreamReader> utworzeniu znaków z **FileStream**, przekazywany do **StreamReader** jako jej argument konstruktora. <xref:System.IO.StreamReader.ReadLine%2A>odczytuje do <xref:System.IO.StreamReader.Peek%2A> znajdzie nie więcej znaków.  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 Poniższy przykład kodu tworzy **FileStream** wokół istniejące `MyFile.txt` w kolejności do buforu `MyFile.txt`. (Należy pamiętać, że **FileStreams** są buforowane domyślnie.) Dalej **BinaryReader** służy do odczytywania bajtów z **FileStream**, która jest przekazywana do **BinaryReader** jako jej argument konstruktora. <xref:System.IO.BinaryReader.ReadByte%2A>odczytuje do <xref:System.IO.BinaryReader.PeekChar%2A> znajdzie nie większej liczby bajtów.  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
