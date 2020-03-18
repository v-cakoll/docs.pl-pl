---
title: Jak kopiować, usuwać i przenosić pliki i foldery - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712276"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="8d394-102">Jak kopiować, usuwać i przenosić pliki i foldery (Przewodnik po programowaniu języka C#)</span><span class="sxs-lookup"><span data-stu-id="8d394-102">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>
<span data-ttu-id="8d394-103">W poniższych przykładach przedstawiono sposób kopiowania, przenoszenia i usuwania plików <xref:System.IO.File?displayProperty=nameWithType>i <xref:System.IO.Directory?displayProperty=nameWithType> <xref:System.IO.FileInfo?displayProperty=nameWithType>folderów <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> w <xref:System.IO?displayProperty=nameWithType> sposób synchroniczny przy użyciu programu , , i klas z obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="8d394-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8d394-104">Te przykłady nie zapewniają paska postępu ani żadnego innego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8d394-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="8d394-105">Jeśli chcesz podać standardowe okno dialogowe postępu, zobacz [Jak udostępnić okno dialogowe postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8d394-105">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="8d394-106">Służy <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> do dostarczania zdarzeń, które umożliwią obliczenie postępu podczas pracy na wielu plikach.</span><span class="sxs-lookup"><span data-stu-id="8d394-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="8d394-107">Innym podejściem jest użycie wywołania platformy do wywołania odpowiednich metod związanych z plikami w powłoce systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8d394-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="8d394-108">Aby uzyskać informacje dotyczące asynchronicznego wykonywania tych operacji plików, zobacz [Asynchroniczne we/wy pliku](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="8d394-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d394-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d394-109">Example</span></span>  
 <span data-ttu-id="8d394-110">W poniższym przykładzie pokazano, jak kopiować pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="8d394-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="8d394-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d394-111">Example</span></span>  
 <span data-ttu-id="8d394-112">W poniższym przykładzie pokazano, jak przenosić pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="8d394-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="8d394-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d394-113">Example</span></span>  
 <span data-ttu-id="8d394-114">W poniższym przykładzie pokazano, jak usunąć pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="8d394-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="8d394-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d394-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="8d394-116">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="8d394-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8d394-117">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8d394-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="8d394-118">Dostarczanie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="8d394-118">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="8d394-119">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="8d394-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="8d394-120">Typowe zadania We/Wy</span><span class="sxs-lookup"><span data-stu-id="8d394-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
