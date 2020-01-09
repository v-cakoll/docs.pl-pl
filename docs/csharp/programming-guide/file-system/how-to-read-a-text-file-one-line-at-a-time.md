---
title: Jak odczytać plik tekstowy po jednym wierszu w przewodniku C# programowania w czasie
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: a6af48cdacd836465d776a3fd4e1d17aa0298b77
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635343"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="2fb4a-102">Jak czytać plik tekstowy po jednym wierszu (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="2fb4a-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="2fb4a-103">Ten przykład odczytuje zawartość pliku tekstowego, po jednym wierszu w czasie, do ciągu przy użyciu metody `ReadLine` klasy `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="2fb4a-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="2fb4a-104">Każdy wiersz tekstu jest przechowywany w ciągu `line` i wyświetlany na ekranie.</span><span class="sxs-lookup"><span data-stu-id="2fb4a-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fb4a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fb4a-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="2fb4a-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2fb4a-106">Compiling the Code</span></span>  
 <span data-ttu-id="2fb4a-107">Skopiuj kod i wklej go do metody `Main` aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="2fb4a-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="2fb4a-108">Zastąp `"c:\test.txt"` rzeczywistą nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="2fb4a-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2fb4a-109">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="2fb4a-109">Robust Programming</span></span>  
 <span data-ttu-id="2fb4a-110">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2fb4a-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2fb4a-111">Plik może nie istnieć.</span><span class="sxs-lookup"><span data-stu-id="2fb4a-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2fb4a-112">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2fb4a-112">.NET Framework Security</span></span>  
 <span data-ttu-id="2fb4a-113">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="2fb4a-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="2fb4a-114">Na przykład plik `myFile.cs` nie może być plikiem C# źródłowym.</span><span class="sxs-lookup"><span data-stu-id="2fb4a-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb4a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2fb4a-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="2fb4a-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2fb4a-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2fb4a-117">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="2fb4a-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
