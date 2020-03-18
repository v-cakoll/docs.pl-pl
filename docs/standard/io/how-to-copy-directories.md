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
# <a name="how-to-copy-directories"></a><span data-ttu-id="30246-102">Jak: Kopiowanie katalogów</span><span class="sxs-lookup"><span data-stu-id="30246-102">How to: Copy directories</span></span>
<span data-ttu-id="30246-103">W tym temacie pokazano, jak używać klas we/wy do synchronicznie kopiować zawartość katalogu do innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="30246-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="30246-104">Na przykład asynchronicznej kopii pliku zobacz [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="30246-104">For an example of asynchronous file copy, see [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="30246-105">W tym przykładzie kopiuje `copySubDirs` podkatalogi, ustawiając `DirectoryCopy` metodę na `true`.</span><span class="sxs-lookup"><span data-stu-id="30246-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="30246-106">Metoda `DirectoryCopy` rekurencyjne kopiowanie podkatalogów przez wywołanie się na każdym podkatalogu, dopóki nie ma więcej do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="30246-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30246-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="30246-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="30246-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30246-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="30246-109">Plik i strumień we/wy</span><span class="sxs-lookup"><span data-stu-id="30246-109">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="30246-110">Typowe zadania we/wy</span><span class="sxs-lookup"><span data-stu-id="30246-110">Common I/O tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)
- [<span data-ttu-id="30246-111">We/Wy pliku asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="30246-111">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
