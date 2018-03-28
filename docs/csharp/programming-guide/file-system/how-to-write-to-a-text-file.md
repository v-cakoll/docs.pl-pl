---
title: 'Porady: wpisywanie do pliku tekstowego (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fa6de76e3981e0f05b5b192045043422a8a912aa
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="ddcc8-102">Porady: wpisywanie do pliku tekstowego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ddcc8-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="ddcc8-103">W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="ddcc8-104">Pierwsze dwa przykłady użycia metod statycznych wygody na <xref:System.IO.File?displayProperty=nameWithType> klasa umożliwiająca zapisanie każdy element dowolnego `IEnumerable<string>` i ciąg do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="ddcc8-105">Przykład 3 przedstawiono sposób dodawania tekstu do pliku, jeśli masz Przetwarzaj każdego wiersza indywidualnie zapis do pliku.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="ddcc8-106">Przykłady 1 – 3 zastąpić istniejącą zawartość pliku, ale przykład 4 przedstawiono sposób dołączać tekstu do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="ddcc8-107">Te przykłady dają zapis literałów ciągów w plikach.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-107">These examples all write string literals to files.</span></span> <span data-ttu-id="ddcc8-108">Jeśli chcesz sformatować zapisywane w pliku tekstowym, użyj <xref:System.String.Format%2A> metody lub C# [ciągu interpolacji](../../../csharp/language-reference/tokens/interpolated.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../../csharp/language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcc8-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddcc8-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ddcc8-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ddcc8-110">Robust Programming</span></span>  
 <span data-ttu-id="ddcc8-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="ddcc8-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ddcc8-112">Plik istnieje i jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-112">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="ddcc8-113">Nazwa ścieżki może być za długa.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-113">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="ddcc8-114">Dysk może być zapełniony.</span><span class="sxs-lookup"><span data-stu-id="ddcc8-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcc8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddcc8-115">See Also</span></span>  
 [<span data-ttu-id="ddcc8-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ddcc8-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ddcc8-117">System plików i rejestr (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="ddcc8-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="ddcc8-118">Przykład: Zapisz kolekcję do przechowywania danych aplikacji</span><span class="sxs-lookup"><span data-stu-id="ddcc8-118">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
