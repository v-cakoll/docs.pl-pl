---
title: Jak czytać plik tekstowy po jednym wierszu naraz - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: e4a9ba2da2548991f442c2f5ab09d39243137875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167520"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="77243-102">Jak czytać plik tekstowy po jednym wierszu naraz (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="77243-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="77243-103">W tym przykładzie odczytuje zawartość pliku tekstowego, jeden wiersz na `ReadLine` raz, `StreamReader` do ciągu przy użyciu metody klasy.</span><span class="sxs-lookup"><span data-stu-id="77243-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="77243-104">Każdy wiersz tekstu jest `line` zapisywany w ciągu i wyświetlany na ekranie.</span><span class="sxs-lookup"><span data-stu-id="77243-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77243-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="77243-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="77243-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="77243-106">Compiling the Code</span></span>  
 <span data-ttu-id="77243-107">Skopiuj kod i `Main` wklej go do metody aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="77243-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="77243-108">Zamień `"c:\test.txt"` na rzeczywistą nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="77243-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="77243-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="77243-109">Robust Programming</span></span>  
 <span data-ttu-id="77243-110">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="77243-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="77243-111">Plik może nie istnieć.</span><span class="sxs-lookup"><span data-stu-id="77243-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="77243-112">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="77243-112">.NET Framework Security</span></span>  
 <span data-ttu-id="77243-113">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="77243-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="77243-114">Na przykład plik `myFile.cs` może nie być plikiem źródłowym Języka C#.</span><span class="sxs-lookup"><span data-stu-id="77243-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77243-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77243-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="77243-116">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="77243-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="77243-117">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="77243-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
