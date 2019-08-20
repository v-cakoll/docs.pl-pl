---
title: 'Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: dd32798062dbfc9a10acd27ce51d8d5dd3b164f6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590091"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="87855-102">Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="87855-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="87855-103">W poniższych przykładach pokazano, jak kopiować, przenosić i usuwać <xref:System.IO.File?displayProperty=nameWithType>pliki i foldery w sposób synchroniczny przy użyciu klas <xref:System.IO.FileInfo?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="87855-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="87855-104">Te przykłady nie zapewniają paska postępu ani żadnego innego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="87855-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="87855-105">Jeśli chcesz podać standardowe okno dialogowe postępu, zobacz [How to: Udostępnianie okna dialogowego postępu dla operacji](how-to-provide-a-progress-dialog-box-for-file-operations.md)na plikach.</span><span class="sxs-lookup"><span data-stu-id="87855-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="87855-106">Służy <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> do dostarczania zdarzeń, które umożliwią obliczenie postępu podczas działania na wielu plikach.</span><span class="sxs-lookup"><span data-stu-id="87855-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="87855-107">Innym podejściem jest użycie wywołania platformy w celu wywołania odpowiednich metod związanych z plikiem w powłoce systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="87855-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="87855-108">Aby uzyskać informacje o tym, jak wykonywać te operacje na plikach asynchronicznie, zobacz [asynchroniczne we/wy pliku](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="87855-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87855-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="87855-109">Example</span></span>  
 <span data-ttu-id="87855-110">Poniższy przykład pokazuje, jak kopiować pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="87855-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="87855-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="87855-111">Example</span></span>  
 <span data-ttu-id="87855-112">Poniższy przykład pokazuje, jak przenieść pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="87855-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="87855-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="87855-113">Example</span></span>  
 <span data-ttu-id="87855-114">Poniższy przykład pokazuje, jak usunąć pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="87855-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="87855-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87855-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="87855-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="87855-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="87855-117">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="87855-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="87855-118">Instrukcje: Udostępnianie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="87855-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="87855-119">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="87855-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="87855-120">Typowe zadania We/Wy</span><span class="sxs-lookup"><span data-stu-id="87855-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
