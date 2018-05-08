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
ms.openlocfilehash: 1cfe07af216da1c35b093a1ca23e4d48c60a7bfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-copy-directories"></a>Porady: kopiowanie katalogów
W tym przykładzie przedstawiono sposób użycia klasy we/wy synchronicznie skopiować zawartość katalogu w innej lokalizacji. W tym przykładzie użytkownik określić, czy też kopiowanie podkatalogów. Jeśli zostaną skopiowane podkatalogi, w tym rekursywnie przykład metody kopiuje je poprzez wywołanie sam w każdej kolejnych podkatalogu dopóki istnieje nie są już do skopiowania.  
  
 Na przykład asynchronicznie kopiowania plików, zobacz [asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [We/Wy plików i strumieni](../../../docs/standard/io/index.md)  
 [Typowe zadania We/Wy](../../../docs/standard/io/common-i-o-tasks.md)  
 [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)
