---
title: "Porady: wpisywanie do pliku tekstowego (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="aa39a-102">Porady: wpisywanie do pliku tekstowego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="aa39a-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="aa39a-103">W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="aa39a-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="aa39a-104">Pierwsze dwa przykłady użycia metod statycznych wygody na <xref:System.IO.File?displayProperty=nameWithType> klasa umożliwiająca zapisanie każdy element żadnych IEnumerable\<ciągu > i ciąg do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="aa39a-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="aa39a-105">Przykład 3 przedstawiono sposób dodawania tekstu do pliku, jeśli masz Przetwarzaj każdego wiersza indywidualnie zapis do pliku.</span><span class="sxs-lookup"><span data-stu-id="aa39a-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="aa39a-106">Przykłady 1 – 3 zastąpić istniejącą zawartość pliku, ale przykład 4 przedstawiono sposób dołączać tekstu do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="aa39a-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="aa39a-107">Te przykłady dają zapis literałów ciągów w plikach, ale najprawdopodobniej można użyć <xref:System.String.Format%2A> metodę, która ma wiele formantów do pisania różnych typów wartości wyrównane do lewej lub w prawo w polu z lub bez uzupełniania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="aa39a-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="aa39a-108">Można również użyć języka C# [ciągu interpolacji](../../../csharp/language-reference/keywords/interpolated-strings.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa39a-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa39a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa39a-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 <span data-ttu-id="aa39a-110">Te przykłady dają zapis literałów ciągów w plikach, ale najprawdopodobniej można użyć <xref:System.String.Format%2A> metodę, która ma wiele formantów do pisania różnych typów wartości wyrównane do lewej lub w prawo w polu z lub bez uzupełniania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="aa39a-110">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="aa39a-111">Można również użyć języka C# [ciągu interpolacji](../../../csharp/language-reference/keywords/interpolated-strings.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa39a-111">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="aa39a-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="aa39a-112">Robust Programming</span></span>  
 <span data-ttu-id="aa39a-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="aa39a-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="aa39a-114">Plik istnieje i jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="aa39a-114">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="aa39a-115">Nazwa ścieżki może być za długa.</span><span class="sxs-lookup"><span data-stu-id="aa39a-115">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="aa39a-116">Dysk może być zapełniony.</span><span class="sxs-lookup"><span data-stu-id="aa39a-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa39a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa39a-117">See Also</span></span>  
 [<span data-ttu-id="aa39a-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="aa39a-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aa39a-119">System plików i rejestr (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="aa39a-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="aa39a-120">Przykład: Zapisz kolekcję do przechowywania danych aplikacji</span><span class="sxs-lookup"><span data-stu-id="aa39a-120">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
