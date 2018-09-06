---
title: 'Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: a9c5b1dc35878ac2e50a7c4ec72251885704fea6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858346"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="c61a2-102">Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c61a2-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="c61a2-103">W poniższych przykładach pokazano, jak skopiować, przenieść i usunąć pliki i foldery w sposób synchronicznego przy użyciu <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> klasy z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c61a2-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c61a2-104">Te przykłady nie zapewniają pasek postępu lub innych interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c61a2-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="c61a2-105">Jeśli chcesz udostępnić okno dialogowe postępu standardowego, zobacz [porady: dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c61a2-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="c61a2-106">Użyj <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zapewnienie zdarzenia, które umożliwią obliczania postępu podczas pracy w wielu plikach.</span><span class="sxs-lookup"><span data-stu-id="c61a2-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="c61a2-107">Innym rozwiązaniem jest użycie platformy wywołania do wywoływania odpowiednich metod związanych z plikami w usłudze Windows Shell.</span><span class="sxs-lookup"><span data-stu-id="c61a2-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="c61a2-108">Aby uzyskać informacji dotyczących sposobu wykonywania tych operacji na plikach asynchronicznie, zobacz [asynchroniczne We/Wy](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="c61a2-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c61a2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c61a2-109">Example</span></span>  
 <span data-ttu-id="c61a2-110">Poniższy przykład pokazuje, jak skopiować pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="c61a2-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c61a2-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c61a2-111">Example</span></span>  
 <span data-ttu-id="c61a2-112">Poniższy przykład pokazuje, jak przenieść pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="c61a2-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="c61a2-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c61a2-113">Example</span></span>  
 <span data-ttu-id="c61a2-114">Poniższy przykład pokazuje, jak usuwać pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="c61a2-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c61a2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c61a2-115">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="c61a2-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c61a2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c61a2-117">System plików i rejestr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="c61a2-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
- [<span data-ttu-id="c61a2-118">Instrukcje: dostarczanie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="c61a2-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
- [<span data-ttu-id="c61a2-119">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="c61a2-119">File and Stream I/O</span></span>](../../../standard/io/index.md)  
- [<span data-ttu-id="c61a2-120">Typowe zadania We/Wy</span><span class="sxs-lookup"><span data-stu-id="c61a2-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
