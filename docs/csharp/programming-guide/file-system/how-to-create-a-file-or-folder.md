---
title: 'Instrukcje: Utwórz plik lub folder — C# Przewodnik programistyczny'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: c29d0638e2429119020fee5317d40a95b00e40ef
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590106"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="6cca9-102">Instrukcje: Utwórz plik lub folder (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="6cca9-102">How to: Create a File or Folder (C# Programming Guide)</span></span>
<span data-ttu-id="6cca9-103">Można programowo utworzyć folder na komputerze, utworzyć podfolder, utworzyć plik w podfolderze i zapisać dane do pliku.</span><span class="sxs-lookup"><span data-stu-id="6cca9-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cca9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cca9-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="6cca9-105">Jeśli folder już istnieje, <xref:System.IO.Directory.CreateDirectory%2A> nie robi nic i żaden wyjątek nie jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="6cca9-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="6cca9-106"><xref:System.IO.File.Create%2A?displayProperty=nameWithType> Jednak zastępuje istniejący plik nowym plikiem.</span><span class="sxs-lookup"><span data-stu-id="6cca9-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="6cca9-107">W przykładzie używa się `if` - `else` instrukcji, aby zapobiec zastąpieniu istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="6cca9-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="6cca9-108">Wprowadzając następujące zmiany w przykładzie, można określić różne wyniki w zależności od tego, czy plik o określonej nazwie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="6cca9-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="6cca9-109">Jeśli taki plik nie istnieje, kod tworzy jeden.</span><span class="sxs-lookup"><span data-stu-id="6cca9-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="6cca9-110">Jeśli taki plik istnieje, kod dołącza dane do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="6cca9-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="6cca9-111">Określ nielosową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="6cca9-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="6cca9-112">Zastąp instrukcję`using` instrukcją w poniższym kodzie. `else` `if` -</span><span class="sxs-lookup"><span data-stu-id="6cca9-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="6cca9-113">Uruchom przykład kilka razy, aby sprawdzić, czy dane są dodawane do pliku za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="6cca9-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="6cca9-114">Aby uzyskać `FileMode` więcej wartości, które można wypróbować, zobacz. <xref:System.IO.FileMode></span><span class="sxs-lookup"><span data-stu-id="6cca9-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="6cca9-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="6cca9-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6cca9-116">Nazwa folderu jest źle sformułowana.</span><span class="sxs-lookup"><span data-stu-id="6cca9-116">The folder name is malformed.</span></span> <span data-ttu-id="6cca9-117">Na przykład zawiera niedozwolone znaki lub jest tylko białym znakiem (<xref:System.ArgumentException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="6cca9-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="6cca9-118">Użyj klasy <xref:System.IO.Path> , aby utworzyć prawidłowe nazwy ścieżek.</span><span class="sxs-lookup"><span data-stu-id="6cca9-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="6cca9-119">Folder nadrzędny folderu, który ma zostać utworzony, jest tylko do odczytu (<xref:System.IO.IOException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="6cca9-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="6cca9-120">Nazwa folderu to `null` (<xref:System.ArgumentNullException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="6cca9-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="6cca9-121">Nazwa folderu jest za długa (<xref:System.IO.PathTooLongException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="6cca9-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="6cca9-122">Nazwa folderu jest tylko dwukropek, ":" (<xref:System.IO.PathTooLongException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="6cca9-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6cca9-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="6cca9-123">.NET Framework Security</span></span>  
 <span data-ttu-id="6cca9-124">Wystąpienie <xref:System.Security.SecurityException> klasy może być zgłaszane w sytuacjach częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="6cca9-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="6cca9-125">Jeśli nie masz uprawnień do utworzenia folderu, przykład zgłosi wystąpienie <xref:System.UnauthorizedAccessException> klasy.</span><span class="sxs-lookup"><span data-stu-id="6cca9-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cca9-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cca9-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="6cca9-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6cca9-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6cca9-128">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="6cca9-128">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
