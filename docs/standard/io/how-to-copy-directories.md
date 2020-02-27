---
title: 'Instrukcje: kopiowanie katalogów'
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
ms.openlocfilehash: 132ce0b887f7c314311e294567c546bded9a89a0
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627400"
---
# <a name="how-to-copy-directories"></a>Instrukcje: kopiowanie katalogów
W tym temacie pokazano, jak używać klas we/wy do synchronicznego kopiowania zawartości katalogu do innej lokalizacji. 

Aby zapoznać się z przykładem asynchronicznego kopiowania plików, zobacz [asynchroniczne operacje we/wy na plikach](../../../docs/standard/io/asynchronous-file-i-o.md). 

Ten przykład kopiuje podkatalogi przez ustawienie `copySubDirs` metody `DirectoryCopy` do `true`. Metoda `DirectoryCopy` rekurencyjnie kopiuje podkatalogi przez wywołanie ich w każdym podkatalogu, dopóki nie będzie więcej do kopiowania.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
- [Typowe zadania we/wy](../../../docs/standard/io/common-i-o-tasks.md)
- [Asynchroniczne operacje we/wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)
