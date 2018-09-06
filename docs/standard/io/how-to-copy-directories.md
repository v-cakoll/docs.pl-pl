---
title: 'Porady: kopiowanie katalogów'
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f2c2fbd58b10af80a2a233cbd4211befe2dbd33
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874813"
---
# <a name="how-to-copy-directories"></a>Porady: kopiowanie katalogów
W tym przykładzie pokazano, jak używać klas we/wy synchronicznie skopiować zawartość katalogu do innej lokalizacji. W tym przykładzie użytkownik może określić, czy ma być również kopiowany podkatalogów. Podkatalogi są kopiowane, w tym rekursywnie przykład metody kopiuje je poprzez wywołanie sam w poszczególnych podkatalogach kolejne, aż nie wystąpią już do skopiowania.  
  
 Na przykład skopiować pliki asynchronicznie zobacz [asynchroniczne We/Wy](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.FileInfo>  
- <xref:System.IO.DirectoryInfo>  
- <xref:System.IO.FileStream>  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)  
- [Typowe zadania We/Wy](../../../docs/standard/io/common-i-o-tasks.md)  
- [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)
