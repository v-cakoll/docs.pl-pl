---
title: Jak utworzyć plik lub folder - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: cdcc0a375aa1eca29c024d1e0c9008f337d0c772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167560"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="33624-102">Jak utworzyć plik lub folder (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="33624-102">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="33624-103">Można programowo utworzyć folder na komputerze, utworzyć podfolder, utworzyć plik w podfolderze i zapisać dane w pliku.</span><span class="sxs-lookup"><span data-stu-id="33624-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33624-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="33624-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="33624-105">Jeśli folder już <xref:System.IO.Directory.CreateDirectory%2A> istnieje, nic nie robi i nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="33624-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="33624-106">Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik nowym plikiem.</span><span class="sxs-lookup"><span data-stu-id="33624-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="33624-107">W przykładzie `if` - `else` użyto instrukcji, aby zapobiec zastępowaniu istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="33624-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="33624-108">Dokonując następujących zmian w przykładzie, można określić różne wyniki na podstawie tego, czy plik o określonej nazwie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="33624-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="33624-109">Jeśli taki plik nie istnieje, kod go tworzy.</span><span class="sxs-lookup"><span data-stu-id="33624-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="33624-110">Jeśli taki plik istnieje, kod dołącza dane do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="33624-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="33624-111">Określ nielosową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="33624-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="33624-112">Zastąp `if` - `else` instrukcję instrukcją `using` w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="33624-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="33624-113">Uruchom przykład kilka razy, aby sprawdzić, czy dane są dodawane do pliku za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="33624-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="33624-114">Aby `FileMode` uzyskać więcej wartości, <xref:System.IO.FileMode>które można wypróbować, zobacz .</span><span class="sxs-lookup"><span data-stu-id="33624-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="33624-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="33624-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="33624-116">Nazwa folderu jest nieprawidłowo sformułowana.</span><span class="sxs-lookup"><span data-stu-id="33624-116">The folder name is malformed.</span></span> <span data-ttu-id="33624-117">Na przykład zawiera niedozwolone znaki lub<xref:System.ArgumentException> jest tylko biały znak (klasa).</span><span class="sxs-lookup"><span data-stu-id="33624-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="33624-118">Użyj <xref:System.IO.Path> klasy, aby utworzyć prawidłowe nazwy ścieżek.</span><span class="sxs-lookup"><span data-stu-id="33624-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="33624-119">Folder nadrzędny folderu, który ma zostać<xref:System.IO.IOException> utworzony, jest tylko do odczytu (klasa).</span><span class="sxs-lookup"><span data-stu-id="33624-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="33624-120">Nazwa folderu `null` <xref:System.ArgumentNullException> to (klasa).</span><span class="sxs-lookup"><span data-stu-id="33624-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="33624-121">Nazwa folderu jest<xref:System.IO.PathTooLongException> za długa (klasa).</span><span class="sxs-lookup"><span data-stu-id="33624-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="33624-122">Nazwa folderu jest tylko dwukropkiem, ":" (<xref:System.IO.PathTooLongException> klasa).</span><span class="sxs-lookup"><span data-stu-id="33624-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="33624-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="33624-123">.NET Framework Security</span></span>  
 <span data-ttu-id="33624-124">Wystąpienie <xref:System.Security.SecurityException> klasy mogą być generowane w sytuacjach częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="33624-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="33624-125">Jeśli nie masz uprawnień do tworzenia folderu, przykład zgłasza <xref:System.UnauthorizedAccessException> wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="33624-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33624-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33624-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="33624-127">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="33624-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="33624-128">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="33624-128">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
