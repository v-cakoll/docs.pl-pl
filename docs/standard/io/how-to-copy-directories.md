---
title: 'Jak: Kopiowanie katalogów'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 5d40db7f902dac8bd6bbdc1510be8e56a321be30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159458"
---
# <a name="how-to-copy-directories"></a>Jak: Kopiowanie katalogów
W tym temacie pokazano, jak używać klas we/wy do synchronicznie kopiować zawartość katalogu do innej lokalizacji.

Na przykład asynchronicznej kopii pliku zobacz [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).

W tym przykładzie kopiuje `copySubDirs` podkatalogi, ustawiając `DirectoryCopy` metodę na `true`. Metoda `DirectoryCopy` rekurencyjne kopiowanie podkatalogów przez wywołanie się na każdym podkatalogu, dopóki nie ma więcej do skopiowania.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [Plik i strumień we/wy](../../../docs/standard/io/index.md)
- [Typowe zadania we/wy](../../../docs/standard/io/common-i-o-tasks.md)
- [We/Wy pliku asynchronicznego](../../../docs/standard/io/asynchronous-file-i-o.md)
