---
title: Jak czytać plik tekstowy jeden wiersz w przewodniku programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241776"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="4f880-102">Jak czytać plik tekstowy po jednym wierszu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4f880-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="4f880-103">Ten przykład odczytuje zawartość pliku tekstowego, jeden wiersz naraz, do ciągu przy użyciu `ReadLine` metody `StreamReader` klasy.</span><span class="sxs-lookup"><span data-stu-id="4f880-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="4f880-104">Każdy wiersz tekstu jest przechowywany w ciągu `line` i wyświetlany na ekranie.</span><span class="sxs-lookup"><span data-stu-id="4f880-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f880-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f880-105">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f880-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4f880-106">Compiling the Code</span></span>  
 <span data-ttu-id="4f880-107">Skopiuj kod i wklej go do `Main` metody aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="4f880-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="4f880-108">Zamień `"c:\test.txt"` na rzeczywistą nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="4f880-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4f880-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="4f880-109">Robust Programming</span></span>  
 <span data-ttu-id="4f880-110">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="4f880-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4f880-111">Plik może nie istnieć.</span><span class="sxs-lookup"><span data-stu-id="4f880-111">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="4f880-112">Zabezpieczenia platformy .NET</span><span class="sxs-lookup"><span data-stu-id="4f880-112">.NET Security</span></span>  
 <span data-ttu-id="4f880-113">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4f880-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="4f880-114">Na przykład plik `myFile.cs` nie może być plikiem źródłowym języka C#.</span><span class="sxs-lookup"><span data-stu-id="4f880-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f880-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f880-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="4f880-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4f880-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4f880-117">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4f880-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
