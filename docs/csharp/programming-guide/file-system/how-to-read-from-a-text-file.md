---
title: 'Instrukcje: Odczytaj z pliku tekstowego — C# Przewodnik programowania'
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
ms.openlocfilehash: 2b98f24da7f13ae752f248eb8f26c75c1d47a824
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923952"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="d9854-102">Instrukcje: Odczytaj z pliku tekstowego (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="d9854-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="d9854-103">Ten przykład odczytuje zawartość pliku tekstowego przy użyciu metod <xref:System.IO.File.ReadAllText%2A> statycznych i <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="d9854-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="d9854-104">Przykład użycia <xref:System.IO.StreamReader>programu można znaleźć w temacie [How to: Odczytaj plik tekstowy jeden wiersz jednocześnie](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="d9854-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9854-105">Pliki, które są używane w tym przykładzie, są tworzone w temacie [How to: Zapisz w pliku](./how-to-write-to-a-text-file.md)tekstowym.</span><span class="sxs-lookup"><span data-stu-id="d9854-105">The files that are used in this example are created in the topic [How to: Write to a Text File](./how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9854-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9854-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d9854-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d9854-107">Compiling the Code</span></span>  
 <span data-ttu-id="d9854-108">Skopiuj kod i wklej go do aplikacji C# konsolowej.</span><span class="sxs-lookup"><span data-stu-id="d9854-108">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="d9854-109">Jeśli nie używasz plików tekstowych z [: Zapisz w pliku](./how-to-write-to-a-text-file.md)tekstowym, Zastąp argument do `ReadAllText` i `ReadAllLines` z odpowiednią ścieżką i nazwą pliku na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d9854-109">If you are not using the text files from [How to: Write to a Text File](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d9854-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d9854-110">Robust Programming</span></span>  
 <span data-ttu-id="d9854-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d9854-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d9854-112">Plik nie istnieje lub nie istnieje w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d9854-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="d9854-113">Sprawdź ścieżkę i pisownię nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="d9854-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d9854-114">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d9854-114">.NET Framework Security</span></span>  
 <span data-ttu-id="d9854-115">Nie należy polegać na nazwie pliku, aby ustalić zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="d9854-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="d9854-116">Na przykład plik `myFile.cs` może nie być plikiem C# źródłowym.</span><span class="sxs-lookup"><span data-stu-id="d9854-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9854-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9854-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="d9854-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d9854-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d9854-119">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="d9854-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
