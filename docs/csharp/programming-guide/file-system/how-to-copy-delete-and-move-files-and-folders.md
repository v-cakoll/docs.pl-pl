---
title: 'Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 5debb2cbfa5ada45447e280169b9fe66d1a15a53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="a36c5-102">Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a36c5-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="a36c5-103">Poniższe przykłady pokazują, jak kopiowanie, przenoszenie i usuwanie plików i folderów w sposób synchronicznego przy użyciu <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> klas z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a36c5-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="a36c5-104">Poniższe przykłady nie zawierają pasek postępu lub inny interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a36c5-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="a36c5-105">Jeśli chcesz podać okno dialogowe postępu standardowego, zobacz [porady: dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a36c5-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="a36c5-106">Użyj <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zapewnienie zdarzenia, które umożliwi obliczyć postęp działającego w wielu plików.</span><span class="sxs-lookup"><span data-stu-id="a36c5-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="a36c5-107">Innym rozwiązaniem jest użycie platformy wywołania do wywołania odpowiednich metod związany z plikami w powłoce systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a36c5-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="a36c5-108">Aby uzyskać informacje dotyczące sposobu wykonywania tych operacji na plikach asynchronicznie, zobacz [asynchroniczne We/Wy pliku](https://msdn.microsoft.com/library/kztecsys).</span><span class="sxs-lookup"><span data-stu-id="a36c5-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a36c5-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="a36c5-109">Example</span></span>  
 <span data-ttu-id="a36c5-110">Poniższy przykład przedstawia sposób kopiowania plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="a36c5-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="a36c5-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a36c5-111">Example</span></span>  
 <span data-ttu-id="a36c5-112">Poniższy przykład przedstawia sposób przenoszenia plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="a36c5-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="a36c5-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a36c5-113">Example</span></span>  
 <span data-ttu-id="a36c5-114">Poniższy przykład przedstawia sposób usuwania plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="a36c5-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a36c5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a36c5-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="a36c5-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a36c5-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a36c5-117">System plików i rejestr (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="a36c5-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
 [<span data-ttu-id="a36c5-118">Instrukcje: dostarczanie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="a36c5-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [<span data-ttu-id="a36c5-119">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="a36c5-119">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
 [<span data-ttu-id="a36c5-120">Typowe zadania We/Wy</span><span class="sxs-lookup"><span data-stu-id="a36c5-120">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)
