---
title: Jak napisać do pliku tekstowego - C# Programming Guide
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712250"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="5c80f-102">Jak zapisać do pliku tekstowego (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="5c80f-102">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="5c80f-103">W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="5c80f-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="5c80f-104">Pierwsze dwa przykłady używają statycznych <xref:System.IO.File?displayProperty=nameWithType> metod wygody w `IEnumerable<string>` klasie, aby zapisać każdy element dowolnego i ciąg do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="5c80f-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="5c80f-105">W przykładzie 3 pokazano, jak dodać tekst do pliku, gdy trzeba przetwarzać każdy wiersz indywidualnie podczas pisania do pliku.</span><span class="sxs-lookup"><span data-stu-id="5c80f-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="5c80f-106">Przykłady 1-3 zastępują całą istniejącą zawartość w pliku, ale przykład 4 pokazuje, jak dołączać tekst do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="5c80f-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="5c80f-107">Te przykłady wszystkie literały ciągu zapisu do plików.</span><span class="sxs-lookup"><span data-stu-id="5c80f-107">These examples all write string literals to files.</span></span> <span data-ttu-id="5c80f-108">Jeśli chcesz sformatować tekst napisany w <xref:System.String.Format%2A> pliku, użyj funkcji [interpolacji ciągu](../../language-reference/tokens/interpolated.md) C# lub c#.</span><span class="sxs-lookup"><span data-stu-id="5c80f-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c80f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c80f-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5c80f-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5c80f-110">Robust Programming</span></span>  
 <span data-ttu-id="5c80f-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="5c80f-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5c80f-112">Plik istnieje i jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="5c80f-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="5c80f-113">Nazwa ścieżki może być za długa.</span><span class="sxs-lookup"><span data-stu-id="5c80f-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="5c80f-114">Dysk może być zapełniony.</span><span class="sxs-lookup"><span data-stu-id="5c80f-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c80f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c80f-115">See also</span></span>

- [<span data-ttu-id="5c80f-116">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="5c80f-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5c80f-117">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5c80f-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="5c80f-118">Przykład: Zapisywanie kolekcji w magazynie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5c80f-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
