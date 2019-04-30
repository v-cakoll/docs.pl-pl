---
title: 'Instrukcje: Zapis do pliku tekstowego — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: da1526afe48a0d4bda63274380dcf59ee30c480e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710787"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="2a677-102">Instrukcje: Zapis do pliku tekstowego (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="2a677-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="2a677-103">W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="2a677-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="2a677-104">Pierwszych dwóch przykładach użyto metody statycznej wygody na <xref:System.IO.File?displayProperty=nameWithType> klasę umożliwiającą zapisanie każdy element dowolnego `IEnumerable<string>` i ciąg do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="2a677-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="2a677-105">Przykład 3 pokazuje, jak dodać tekst do pliku, gdy trzeba osobno przetworzyć każdy wiersz zapisać do pliku.</span><span class="sxs-lookup"><span data-stu-id="2a677-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="2a677-106">W przykładach 1 – 3 zastępowana cała istniejąca zawartość w pliku, ale w przykładzie 4 pokazano, jak dołączyć tekst do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="2a677-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="2a677-107">Wszystkie te przykłady zapisują literały ciągów znaków do plików.</span><span class="sxs-lookup"><span data-stu-id="2a677-107">These examples all write string literals to files.</span></span> <span data-ttu-id="2a677-108">Aby sformatować tekst zapisany do pliku, należy użyć <xref:System.String.Format%2A> metody lub C# [Interpolacja ciągów](../../../csharp/language-reference/tokens/interpolated.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="2a677-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../../csharp/language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a677-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a677-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2a677-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="2a677-110">Robust Programming</span></span>  
 <span data-ttu-id="2a677-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2a677-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2a677-112">Plik istnieje i jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="2a677-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="2a677-113">Nazwa ścieżki może być za długa.</span><span class="sxs-lookup"><span data-stu-id="2a677-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="2a677-114">Dysk może być zapełniony.</span><span class="sxs-lookup"><span data-stu-id="2a677-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a677-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a677-115">See also</span></span>

- [<span data-ttu-id="2a677-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2a677-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2a677-117">System plików i rejestr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="2a677-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
- [<span data-ttu-id="2a677-118">Przykład: Zapisywanie kolekcji do przechowywania danych aplikacji</span><span class="sxs-lookup"><span data-stu-id="2a677-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
