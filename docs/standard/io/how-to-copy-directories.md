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
ms.openlocfilehash: 223e83a5ff6a73825985ec4e3b6b601fb196fe5e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707903"
---
# <a name="how-to-copy-directories"></a>Instrukcje: kopiowanie katalogów
W tym temacie pokazano, jak używać klas we/wy do synchronicznego kopiowania zawartości katalogu do innej lokalizacji. 

Aby zapoznać się z przykładem asynchronicznego kopiowania plików, zobacz [asynchroniczne operacje we/wy na plikach](../../../docs/standard/io/asynchronous-file-i-o.md). 

Ten przykład kopiuje podkatalogi przez ustawienie `copySubDirs` metody `DirectoryCopy` do `true`. Metoda `DirectoryCopy` rekurencyjnie kopiuje podkatalogi przez wywołanie ich w każdym podkatalogu, dopóki nie będzie więcej do kopiowania.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
- [Typowe zadania we/wy](../../../docs/standard/io/common-i-o-tasks.md)
- [Asynchroniczne operacje we/wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)
