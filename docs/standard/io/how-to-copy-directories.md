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
# <a name="how-to-copy-directories"></a><span data-ttu-id="45161-102">Porady: kopiowanie katalogów</span><span class="sxs-lookup"><span data-stu-id="45161-102">How to: Copy Directories</span></span>
<span data-ttu-id="45161-103">W tym przykładzie przedstawiono sposób użycia klasy we/wy synchronicznie skopiować zawartość katalogu w innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="45161-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="45161-104">W tym przykładzie użytkownik określić, czy też kopiowanie podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="45161-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="45161-105">Jeśli zostaną skopiowane podkatalogi, w tym rekursywnie przykład metody kopiuje je poprzez wywołanie sam w każdej kolejnych podkatalogu dopóki istnieje nie są już do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="45161-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="45161-106">Na przykład asynchronicznie kopiowania plików, zobacz [asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="45161-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45161-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="45161-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="45161-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45161-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="45161-109">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="45161-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="45161-110">Typowe zadania We/Wy</span><span class="sxs-lookup"><span data-stu-id="45161-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="45161-111">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="45161-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
