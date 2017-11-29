---
title: "Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="7b220-102">Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7b220-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="7b220-103">Poniższe przykłady pokazują, jak kopiowanie, przenoszenie i usuwanie plików i folderów w sposób synchronicznego przy użyciu <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> klas z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7b220-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7b220-104">Poniższe przykłady nie zawierają pasek postępu lub inny interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7b220-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="7b220-105">Jeśli chcesz podać okno dialogowe postępu standardowego, zobacz [porady: dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7b220-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="7b220-106">Użyj <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zapewnienie zdarzenia, które umożliwi obliczyć postęp działającego w wielu plików.</span><span class="sxs-lookup"><span data-stu-id="7b220-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="7b220-107">Innym rozwiązaniem jest użycie platformy wywołania do wywołania odpowiednich metod związany z plikami w powłoce systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7b220-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="7b220-108">Aby uzyskać informacje dotyczące sposobu wykonywania tych operacji na plikach asynchronicznie, zobacz [asynchroniczne We/Wy pliku](https://msdn.microsoft.com/library/kztecsys).</span><span class="sxs-lookup"><span data-stu-id="7b220-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b220-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b220-109">Example</span></span>  
 <span data-ttu-id="7b220-110">Poniższy przykład przedstawia sposób kopiowania plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="7b220-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="7b220-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b220-111">Example</span></span>  
 <span data-ttu-id="7b220-112">Poniższy przykład przedstawia sposób przenoszenia plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="7b220-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="7b220-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b220-113">Example</span></span>  
 <span data-ttu-id="7b220-114">Poniższy przykład przedstawia sposób usuwania plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="7b220-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7b220-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b220-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="7b220-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7b220-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7b220-117">System plików i rejestr (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="7b220-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
 [<span data-ttu-id="7b220-118">Porady: dostarczanie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="7b220-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [<span data-ttu-id="7b220-119">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="7b220-119">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
 [<span data-ttu-id="7b220-120">Typowe zadania we/wy</span><span class="sxs-lookup"><span data-stu-id="7b220-120">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)
