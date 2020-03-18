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
ms.openlocfilehash: 3f18712793254f4942c092c87a3e64c73b492ae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160108"
---
# <a name="compose-streams"></a>Tworzenie strumieni
*Magazyn zapasowy* jest nośnikiem pamięci masowej, takim jak dysk lub pamięć. Każdy inny magazyn zapasowy implementuje swój własny <xref:System.IO.Stream> strumień jako implementację klasy.

Każdy typ strumienia odczytuje i zapisuje bajty z i do danego magazynu zapasowego. Strumienie, które łączą się z magazynami zapasowymi, są nazywane *strumieniami bazowymi*. Strumienie bazowe mają konstruktorów z parametrami niezbędnymi do połączenia strumienia do magazynu kopii zapasowych. Na przykład <xref:System.IO.FileStream> ma konstruktorów, które określają parametr ścieżki, który określa, jak plik będzie współużytkowany przez procesy.  

Projekt klas <xref:System.IO> zapewnia uproszczony skład strumienia. Strumienie podstawowe można dołączyć do jednego lub większej liczby strumieni przekazu, które zapewniają żądaną funkcjonalność. Czytnik lub moduł zapisujący można dołączyć do końca łańcucha, dzięki czemu preferowane typy można łatwo odczytać lub zapisać.  

Poniższe przykłady kodu tworzą **FileStream** wokół istniejącego *pliku MyFile.txt* w celu buforowania *pliku MyFile.txt*. Należy zauważyć, że **FileStreams** są buforowane domyślnie.

>[!IMPORTANT]
>W przykładach przyjęto założenie, że plik o nazwie *MyFile.txt* już istnieje w tym samym folderze co aplikacja.  

## <a name="example-use-streamreader"></a>Przykład: Korzystanie z streamreadera
Poniższy przykład tworzy <xref:System.IO.StreamReader> do odczytu znaków z **FileStream**, który jest przekazywany do **StreamReader** jako argument konstruktora. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>następnie odczytuje, dopóki <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nie znajdzie więcej znaków.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Przykład: Użyj czytnika binarnego
Poniższy przykład tworzy <xref:System.IO.BinaryReader> do odczytu bajtów z **FileStream**, który jest przekazywany do **BinaryReader** jako argument konstruktora. <xref:System.IO.BinaryReader.ReadByte%2A>następnie odczytuje, dopóki <xref:System.IO.BinaryReader.PeekChar%2A> nie znajdzie więcej bajtów.  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
