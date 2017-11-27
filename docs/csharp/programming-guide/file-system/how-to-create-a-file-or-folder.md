---
title: "Porady: utworzenie pliku lub folderu (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f7eb2c6386a8433c025a9f2abea4b03f6ab271d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="646e7-102">Porady: utworzenie pliku lub folderu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="646e7-102">How to: Create a File or Folder (C# Programming Guide)</span></span>
<span data-ttu-id="646e7-103">Można programowo Utwórz folder na komputerze, utwórz podfolder, Utwórz plik w podfolderze i zapisywania danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="646e7-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="646e7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="646e7-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 <span data-ttu-id="646e7-105">Jeśli folder już istnieje, <xref:System.IO.Directory.CreateDirectory%2A> ma nothing i żaden wyjątek zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="646e7-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="646e7-106">Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik przy użyciu nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="646e7-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="646e7-107">W przykładzie użyto `if` - `else` instrukcji, aby zapobiec zastąpienia istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="646e7-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="646e7-108">Wprowadzając następujące zmiany w tym przykładzie, można określić różne wyniki według tego, czy plik niektórych nazwą już istnieje.</span><span class="sxs-lookup"><span data-stu-id="646e7-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="646e7-109">Jeśli taki plik nie istnieje, kod tworzy go.</span><span class="sxs-lookup"><span data-stu-id="646e7-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="646e7-110">Jeśli plik jest dostępny, kod dołącza dane do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="646e7-110">If such a file exists, the code appends data to that file.</span></span>  
  
-   <span data-ttu-id="646e7-111">Określ nazwę pliku losowych.</span><span class="sxs-lookup"><span data-stu-id="646e7-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   <span data-ttu-id="646e7-112">Zastąp `if` - `else` instrukcji z `using` instrukcji w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="646e7-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="646e7-113">Uruchom kilka razy w przykładzie do Sprawdź, czy dane są dodawane do pliku zawsze.</span><span class="sxs-lookup"><span data-stu-id="646e7-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="646e7-114">Aby uzyskać więcej `FileMode` wartości, których można spróbować, zobacz <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="646e7-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="646e7-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="646e7-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="646e7-116">Nazwa folderu jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="646e7-116">The folder name is malformed.</span></span> <span data-ttu-id="646e7-117">Na przykład zawiera niedozwolone znaki lub jest tylko znak odstępu (<xref:System.ArgumentException> klasy).</span><span class="sxs-lookup"><span data-stu-id="646e7-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="646e7-118">Użyj <xref:System.IO.Path> klasy w celu utworzenia nazwy prawidłową ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="646e7-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
-   <span data-ttu-id="646e7-119">Folder, który ma zostać utworzony folder nadrzędny jest tylko do odczytu (<xref:System.IO.IOException> klasy).</span><span class="sxs-lookup"><span data-stu-id="646e7-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="646e7-120">Nazwa folderu jest `null` (<xref:System.ArgumentNullException> klasy).</span><span class="sxs-lookup"><span data-stu-id="646e7-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="646e7-121">Nazwa folderu jest za długa (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="646e7-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="646e7-122">Nazwa folderu jest tylko dwukropka ":" (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="646e7-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="646e7-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="646e7-123">.NET Framework Security</span></span>  
 <span data-ttu-id="646e7-124">Wystąpienie <xref:System.Security.SecurityException> klasa może zostać zgłoszony w sytuacjach częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="646e7-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="646e7-125">Jeśli nie masz uprawnień do tworzenia folderu przykładzie zgłasza wystąpienia <xref:System.UnauthorizedAccessException> klasy.</span><span class="sxs-lookup"><span data-stu-id="646e7-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646e7-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="646e7-126">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="646e7-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="646e7-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="646e7-128">System plików i rejestr (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="646e7-128">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
