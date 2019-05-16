---
title: 'Instrukcje: Kopiowanie katalogów'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a7fa901d887701e0fa41a0887b363adec07dba2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644681"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="fa639-102">Instrukcje: Kopiowanie katalogów</span><span class="sxs-lookup"><span data-stu-id="fa639-102">How to: Copy directories</span></span>
<span data-ttu-id="fa639-103">W tym temacie pokazano, jak używać klas we/wy synchronicznie skopiować zawartość katalogu do innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="fa639-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> 

<span data-ttu-id="fa639-104">Na przykład kopiowanie plików asynchronicznego Zobacz [asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="fa639-104">For an example of asynchronous file copy, see [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span> 

<span data-ttu-id="fa639-105">W tym przykładzie kopiuje podkatalogi, ustawiając `copySubDirs` z `DirectoryCopy` metody `true`.</span><span class="sxs-lookup"><span data-stu-id="fa639-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="fa639-106">`DirectoryCopy` Rekursywnie metoda kopiuje podkatalogi poprzez wywołanie sam w poszczególnych podkatalogach, dopóki nie będą wyświetlane nie do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="fa639-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa639-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa639-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fa639-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa639-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="fa639-109">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="fa639-109">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="fa639-110">Typowe zadania we/wy</span><span class="sxs-lookup"><span data-stu-id="fa639-110">Common I/O tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)
- [<span data-ttu-id="fa639-111">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="fa639-111">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
