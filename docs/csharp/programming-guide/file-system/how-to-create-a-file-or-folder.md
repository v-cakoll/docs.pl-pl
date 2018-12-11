---
title: 'Instrukcje: Utwórz plik lub Folder — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: aa5c6782b11ac89b418ac84faafaa8409ad65049
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240206"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="e8739-102">Instrukcje: Utworzenie pliku lub folderu (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e8739-102">How to: Create a File or Folder (C# Programming Guide)</span></span>
<span data-ttu-id="e8739-103">Można programowo utworzyć folder na komputerze, utwórz podfolder, Utwórz plik w podfolderze i zapisać dane do pliku.</span><span class="sxs-lookup"><span data-stu-id="e8739-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8739-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8739-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 <span data-ttu-id="e8739-105">Jeśli folder już istnieje, <xref:System.IO.Directory.CreateDirectory%2A> robi nic, a żaden wyjątek jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="e8739-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="e8739-106">Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik nowym plikiem.</span><span class="sxs-lookup"><span data-stu-id="e8739-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="e8739-107">W przykładzie użyto `if` - `else` instrukcję, aby uniemożliwić zastąpienia istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="e8739-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="e8739-108">Wprowadzając następujące zmiany w przykładzie, można określić różne wyniki oparte na tego, czy plik o określonej nazwie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="e8739-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="e8739-109">Jeśli taki plik nie istnieje, kod tworzy go.</span><span class="sxs-lookup"><span data-stu-id="e8739-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="e8739-110">Jeśli taki plik istnieje, kod dołącza dane do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="e8739-110">If such a file exists, the code appends data to that file.</span></span>  
  
-   <span data-ttu-id="e8739-111">Określ nielosową nazwę.</span><span class="sxs-lookup"><span data-stu-id="e8739-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   <span data-ttu-id="e8739-112">Zastąp `if` - `else` instrukcję, określając `using` instrukcji w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8739-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="e8739-113">Uruchom przykład kilka razy, aby sprawdzić, czy dane są dodawane do pliku każdorazowo.</span><span class="sxs-lookup"><span data-stu-id="e8739-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="e8739-114">Aby uzyskać więcej informacji `FileMode` wartości, które można wypróbować, zobacz <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="e8739-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="e8739-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e8739-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e8739-116">Nazwa folderu jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="e8739-116">The folder name is malformed.</span></span> <span data-ttu-id="e8739-117">Na przykład zawiera niedozwolone znaki lub jest tylko spacją (<xref:System.ArgumentException> klasy).</span><span class="sxs-lookup"><span data-stu-id="e8739-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="e8739-118">Użyj <xref:System.IO.Path> klasy, aby utworzyć prawidłowe ścieżki nazw.</span><span class="sxs-lookup"><span data-stu-id="e8739-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
-   <span data-ttu-id="e8739-119">Folderem nadrzędnym folderu, który ma zostać utworzony jest tylko do odczytu (<xref:System.IO.IOException> klasy).</span><span class="sxs-lookup"><span data-stu-id="e8739-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="e8739-120">Nazwa folderu jest `null` (<xref:System.ArgumentNullException> klasy).</span><span class="sxs-lookup"><span data-stu-id="e8739-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="e8739-121">Nazwa folderu jest zbyt długa (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="e8739-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="e8739-122">Nazwa folderu jest tylko dwukropek, ":" (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="e8739-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e8739-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e8739-123">.NET Framework Security</span></span>  
 <span data-ttu-id="e8739-124">Wystąpienie <xref:System.Security.SecurityException> klasy mogą być generowane w sytuacjach częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="e8739-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="e8739-125">Jeśli nie masz uprawnień do utworzenia folderu, przykład generuje wystąpienie <xref:System.UnauthorizedAccessException> klasy.</span><span class="sxs-lookup"><span data-stu-id="e8739-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8739-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8739-126">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="e8739-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e8739-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e8739-128">System plików i rejestr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e8739-128">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
