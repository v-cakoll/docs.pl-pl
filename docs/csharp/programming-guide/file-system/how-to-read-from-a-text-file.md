---
title: Jak czytać z pliku tekstowego - Przewodnik po programowaniu C#
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705018"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="23e7c-102">Jak czytać z pliku tekstowego (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="23e7c-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="23e7c-103">W tym przykładzie odczytuje zawartość pliku tekstowego <xref:System.IO.File.ReadAllText%2A> przy <xref:System.IO.File.ReadAllLines%2A> użyciu <xref:System.IO.File?displayProperty=nameWithType> metod statycznych i z klasy.</span><span class="sxs-lookup"><span data-stu-id="23e7c-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="23e7c-104">Na przykład, <xref:System.IO.StreamReader>który używa , zobacz [Jak czytać plik tekstowy po jednym wierszu naraz](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="23e7c-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="23e7c-105">Pliki, które są używane w tym przykładzie są tworzone w temacie [Jak napisać do pliku tekstowego](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="23e7c-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="23e7c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="23e7c-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23e7c-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="23e7c-107">Compiling the Code</span></span>  
 <span data-ttu-id="23e7c-108">Skopiuj kod i wklej go do aplikacji konsoli C#.</span><span class="sxs-lookup"><span data-stu-id="23e7c-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="23e7c-109">Jeśli nie używasz plików tekstowych z [Jak zapisać do pliku tekstowego,](./how-to-write-to-a-text-file.md)zastąp argument do `ReadAllText` i `ReadAllLines` z odpowiednią ścieżką i nazwą pliku na komputerze.</span><span class="sxs-lookup"><span data-stu-id="23e7c-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="23e7c-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="23e7c-110">Robust Programming</span></span>  
 <span data-ttu-id="23e7c-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="23e7c-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="23e7c-112">Plik nie istnieje lub nie istnieje w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="23e7c-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="23e7c-113">Sprawdź ścieżkę i pisownię nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="23e7c-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="23e7c-114">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="23e7c-114">.NET Framework Security</span></span>  
 <span data-ttu-id="23e7c-115">Nie należy polegać na nazwie pliku, aby określić zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="23e7c-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="23e7c-116">Na przykład plik `myFile.cs` może nie być plikiem źródłowym Języka C#.</span><span class="sxs-lookup"><span data-stu-id="23e7c-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e7c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23e7c-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="23e7c-118">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="23e7c-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="23e7c-119">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="23e7c-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
