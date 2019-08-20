---
title: 'Instrukcje: Zapisz w pliku tekstowym — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: d08fe23f2dbfe46c0a58084b05610dfe7db3dda9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589920"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="6c0b5-102">Instrukcje: Zapisz w pliku tekstowym (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="6c0b5-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="6c0b5-103">W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="6c0b5-104">Pierwsze dwa przykłady używają statycznych metod dogodnych na <xref:System.IO.File?displayProperty=nameWithType> klasie, aby napisać każdy element dowolnego `IEnumerable<string>` i ciągu do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="6c0b5-105">Przykład 3 pokazuje, jak dodać tekst do pliku, gdy trzeba przetwarzać każdy wiersz indywidualnie podczas zapisu w pliku.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="6c0b5-106">Przykłady 1-3 Zastąp całą istniejącą zawartość pliku, ale przykład 4 pokazuje, jak dołączyć tekst do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="6c0b5-107">Te przykłady umożliwiają zapisanie literałów ciągu do plików.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-107">These examples all write string literals to files.</span></span> <span data-ttu-id="6c0b5-108">Jeśli chcesz sformatować tekst zapisany w pliku, użyj <xref:System.String.Format%2A> funkcji interpolacji metody lub C# [ciągu](../../language-reference/tokens/interpolated.md) .</span><span class="sxs-lookup"><span data-stu-id="6c0b5-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c0b5-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c0b5-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6c0b5-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="6c0b5-110">Robust Programming</span></span>  
 <span data-ttu-id="6c0b5-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="6c0b5-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6c0b5-112">Plik istnieje i jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="6c0b5-113">Nazwa ścieżki może być za długa.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="6c0b5-114">Dysk może być zapełniony.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0b5-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c0b5-115">See also</span></span>

- [<span data-ttu-id="6c0b5-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6c0b5-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6c0b5-117">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="6c0b5-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="6c0b5-118">Northwind Zapisywanie kolekcji w magazynie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6c0b5-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
