---
title: 'Instrukcje: Odczyt z pliku tekstowego — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 67e98750af589a3deb5e9d0d51f8b1204fdaad84
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240310"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="e7f67-102">Instrukcje: Odczyt z pliku tekstowego (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e7f67-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="e7f67-103">Ten przykład odczytuje zawartość pliku tekstowego przy użyciu metod statycznych <xref:System.IO.File.ReadAllText%2A> i <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="e7f67-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="e7f67-104">Aby uzyskać przykład, który używa <xref:System.IO.StreamReader>, zobacz [jak: Odczyt pliku jednego wiersza tekstu w danym momencie](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="e7f67-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7f67-105">Pliki, które są używane w tym przykładzie są tworzone w temacie [jak: Zapis do pliku tekstowego](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="e7f67-105">The files that are used in this example are created in the topic [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7f67-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7f67-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7f67-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e7f67-107">Compiling the Code</span></span>  
 <span data-ttu-id="e7f67-108">Skopiuj kod i wklej go w aplikacji konsolowej C#.</span><span class="sxs-lookup"><span data-stu-id="e7f67-108">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="e7f67-109">Jeśli nie używasz plików tekstowych z [jak: Zapis do pliku tekstowego](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), Zastąp argument `ReadAllText` i `ReadAllLines` z odpowiednią ścieżkę i nazwę pliku na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e7f67-109">If you are not using the text files from [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e7f67-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e7f67-110">Robust Programming</span></span>  
 <span data-ttu-id="e7f67-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e7f67-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e7f67-112">Plik nie istnieje lub nie istnieje w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e7f67-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="e7f67-113">Sprawdź ścieżkę i pisownię nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="e7f67-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e7f67-114">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e7f67-114">.NET Framework Security</span></span>  
 <span data-ttu-id="e7f67-115">Nie należy polegać na nazwę pliku, aby określić zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="e7f67-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="e7f67-116">Na przykład plik `myFile.cs` może nie być plik źródłowy C#.</span><span class="sxs-lookup"><span data-stu-id="e7f67-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f67-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7f67-117">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="e7f67-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e7f67-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e7f67-119">System plików i rejestr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e7f67-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
