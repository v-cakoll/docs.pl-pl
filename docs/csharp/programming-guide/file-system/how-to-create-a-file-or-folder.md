---
title: Jak utworzyć plik lub folder — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: e0d0a7fbbc7e6a5c9a0bd00dec1188c5cfdcf896
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705252"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="df853-102">Jak utworzyć plik lub folder (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="df853-102">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="df853-103">Można programowo utworzyć folder na komputerze, utworzyć podfolder, utworzyć plik w podfolderze i zapisać dane do pliku.</span><span class="sxs-lookup"><span data-stu-id="df853-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df853-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="df853-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="df853-105">Jeśli folder już istnieje, <xref:System.IO.Directory.CreateDirectory%2A> nic nie robi i żaden wyjątek nie jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="df853-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="df853-106">Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik nowym plikiem.</span><span class="sxs-lookup"><span data-stu-id="df853-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="df853-107">W przykładzie jest używana instrukcja `if`-`else`, aby zapobiec zastąpieniu istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="df853-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="df853-108">Wprowadzając następujące zmiany w przykładzie, można określić różne wyniki w zależności od tego, czy plik o określonej nazwie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="df853-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="df853-109">Jeśli taki plik nie istnieje, kod tworzy jeden.</span><span class="sxs-lookup"><span data-stu-id="df853-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="df853-110">Jeśli taki plik istnieje, kod dołącza dane do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="df853-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="df853-111">Określ nielosową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="df853-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="df853-112">Zastąp instrukcję `if`-`else` instrukcją `using` w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="df853-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="df853-113">Uruchom przykład kilka razy, aby sprawdzić, czy dane są dodawane do pliku za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="df853-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="df853-114">Aby uzyskać więcej `FileMode` wartości, które można wypróbować, zobacz <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="df853-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="df853-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="df853-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="df853-116">Nazwa folderu jest źle sformułowana.</span><span class="sxs-lookup"><span data-stu-id="df853-116">The folder name is malformed.</span></span> <span data-ttu-id="df853-117">Na przykład zawiera niedozwolone znaki lub jest tylko białym znakiem (<xref:System.ArgumentException> Class).</span><span class="sxs-lookup"><span data-stu-id="df853-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="df853-118">Użyj klasy <xref:System.IO.Path>, aby utworzyć prawidłowe nazwy ścieżek.</span><span class="sxs-lookup"><span data-stu-id="df853-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="df853-119">Folder nadrzędny folderu, który ma zostać utworzony, jest tylko do odczytu (Klasa<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="df853-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="df853-120">Nazwa folderu jest `null` (Klasa<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="df853-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="df853-121">Nazwa folderu jest za długa (Klasa<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="df853-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="df853-122">Nazwa folderu jest tylko dwukropek, ":" (Klasa<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="df853-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="df853-123">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="df853-123">.NET Framework Security</span></span>  
 <span data-ttu-id="df853-124">Wystąpienie klasy <xref:System.Security.SecurityException> może być zgłaszane w sytuacjach częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="df853-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="df853-125">Jeśli nie masz uprawnień do utworzenia folderu, przykład zgłosi wystąpienie klasy <xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="df853-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df853-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df853-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="df853-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="df853-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="df853-128">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="df853-128">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
