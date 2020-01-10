---
title: Jak napisać plik tekstowy — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712250"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="d453e-102">Jak zapisać w pliku tekstowym (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="d453e-102">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="d453e-103">W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="d453e-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="d453e-104">Pierwsze dwa przykłady używają statycznych metod wygodnej klasy <xref:System.IO.File?displayProperty=nameWithType>, aby napisać każdy element dowolnego `IEnumerable<string>` i ciągu do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="d453e-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="d453e-105">Przykład 3 pokazuje, jak dodać tekst do pliku, gdy trzeba przetwarzać każdy wiersz indywidualnie podczas zapisu w pliku.</span><span class="sxs-lookup"><span data-stu-id="d453e-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="d453e-106">Przykłady 1-3 Zastąp całą istniejącą zawartość pliku, ale przykład 4 pokazuje, jak dołączyć tekst do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="d453e-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="d453e-107">Te przykłady umożliwiają zapisanie literałów ciągu do plików.</span><span class="sxs-lookup"><span data-stu-id="d453e-107">These examples all write string literals to files.</span></span> <span data-ttu-id="d453e-108">Jeśli chcesz sformatować tekst zapisany w pliku, użyj metody <xref:System.String.Format%2A> lub C# [interpolacji ciągów](../../language-reference/tokens/interpolated.md) .</span><span class="sxs-lookup"><span data-stu-id="d453e-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d453e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d453e-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d453e-110">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="d453e-110">Robust Programming</span></span>  
 <span data-ttu-id="d453e-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d453e-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d453e-112">Plik istnieje i jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d453e-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="d453e-113">Nazwa ścieżki może być za długa.</span><span class="sxs-lookup"><span data-stu-id="d453e-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="d453e-114">Dysk może być zapełniony.</span><span class="sxs-lookup"><span data-stu-id="d453e-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d453e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d453e-115">See also</span></span>

- [<span data-ttu-id="d453e-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d453e-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d453e-117">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="d453e-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="d453e-118">Przykład: zapisywanie kolekcji w magazynie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d453e-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
