---
title: 'Instrukcje: Odczytywanie pliku tekstowego po jednym wierszu (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 75274d93ee29feb5f79dfc29c24109f25fd98a5c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589961"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="edd29-102">Instrukcje: Odczytywanie pliku tekstowego po jednym wierszu (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="edd29-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="edd29-103">Ten przykład odczytuje zawartość pliku tekstowego, jeden wiersz naraz, do ciągu przy użyciu `ReadLine` metody `StreamReader` klasy.</span><span class="sxs-lookup"><span data-stu-id="edd29-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="edd29-104">Każdy wiersz tekstu jest przechowywany w ciągu `line` i wyświetlany na ekranie.</span><span class="sxs-lookup"><span data-stu-id="edd29-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edd29-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="edd29-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="edd29-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="edd29-106">Compiling the Code</span></span>  
 <span data-ttu-id="edd29-107">Skopiuj kod i wklej go do `Main` metody aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="edd29-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="edd29-108">Zamień `"c:\test.txt"` na rzeczywistą nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="edd29-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="edd29-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="edd29-109">Robust Programming</span></span>  
 <span data-ttu-id="edd29-110">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="edd29-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="edd29-111">Plik może nie istnieć.</span><span class="sxs-lookup"><span data-stu-id="edd29-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="edd29-112">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="edd29-112">.NET Framework Security</span></span>  
 <span data-ttu-id="edd29-113">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="edd29-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="edd29-114">Na przykład plik `myFile.cs` nie może być plikiem C# źródłowym.</span><span class="sxs-lookup"><span data-stu-id="edd29-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd29-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edd29-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="edd29-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="edd29-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="edd29-117">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="edd29-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
