---
title: Asynchroniczne We/Wy pliku
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
ms.openlocfilehash: 66e7d01f37a1119b9d2076a9131aa40f26d15625
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708194"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="15a0e-102">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="15a0e-102">Asynchronous File I/O</span></span>

<span data-ttu-id="15a0e-103">Mechanizm operacji asynchronicznych umożliwia wykonywanie operacji We/Wy mocno obciążających zasoby bez blokowania wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="15a0e-103">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="15a0e-104">Ta kwestia wydajności jest szczególnie ważna w aplikacji ze Sklepu Windows 8.x lub aplikacji klasycznej, gdzie czasochłonna operacja strumienia może zablokować wątek interfejsu użytkownika i sprawić, że aplikacja będzie wyświetlana tak, jakby nie działała.</span><span class="sxs-lookup"><span data-stu-id="15a0e-104">This performance consideration is particularly important in a Windows 8.x Store app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="15a0e-105">Począwszy od .NET Framework 4.5 typy we/wy zawierają metody asynchroniczne w celu uproszczenia operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="15a0e-105">Starting with the .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="15a0e-106">Metoda asynchroniczna ma w nazwie element `Async`, np. <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> lub <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="15a0e-106">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="15a0e-107">Te metody asynchroniczne są implementowane w klasach strumieniowych, takich jak <xref:System.IO.Stream>, <xref:System.IO.FileStream> i <xref:System.IO.MemoryStream>, oraz klasach służących do odczytu /zapisu do strumieni, takich jak <xref:System.IO.TextReader> i <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="15a0e-107">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="15a0e-108">W programie .NET Framework w wersji 4 i starszych do implementowania asynchronicznych operacji We/Wy należy używać metod takich jak <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A>.</span><span class="sxs-lookup"><span data-stu-id="15a0e-108">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="15a0e-109">Te metody są nadal dostępne w .NET Framework 4.5 do obsługi starszego kodu; Jednak metody asynchroniczne ułatwiają implementowanie operacji we/wy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="15a0e-109">These methods are still available in the .NET Framework 4.5 to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="15a0e-110">C# i Visual Basic mają dwa słowa kluczowe do programowania asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="15a0e-110">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="15a0e-111">Modyfikator `Async` (Visual Basic) lub `async` (C#), który służy do oznaczania metody zawierającej operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="15a0e-111">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="15a0e-112">Operator `Await` (Visual Basic) lub `await` (C#), który jest stosowany do wyniku metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="15a0e-112">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="15a0e-113">W celu implementowania asynchronicznych operacji We/Wy należy używać tych słów kluczowych w połączeniu z metodami asynchronicznymi, jak pokazano w przykładach poniżej.</span><span class="sxs-lookup"><span data-stu-id="15a0e-113">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="15a0e-114">Aby uzyskać więcej informacji, zobacz [Programowanie asynchroniczne z async i await (C#)](../../csharp/programming-guide/concepts/async/index.md) lub [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="15a0e-114">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="15a0e-115">W tym przykładzie pokazano, jak za pomocą dwóch obiektów <xref:System.IO.FileStream> skopiować pliki asynchronicznie z jednego katalogu do innego.</span><span class="sxs-lookup"><span data-stu-id="15a0e-115">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="15a0e-116">Program obsługi zdarzeń <xref:System.Web.UI.WebControls.Button.Click> kontrolki <xref:System.Windows.Controls.Button> jest oznaczony modyfikatorem `async`, ponieważ wywołuje metodę asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="15a0e-116">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="15a0e-117">Następny przykład jest podobny do poprzedniego, tylko obiekty <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> służą do asynchronicznego odczytywania i zapisywania zawartości pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="15a0e-117">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="15a0e-118">W następnym przykładzie przedstawiono plik związany z kodem i plik XAML, które są używane do otwierania pliku jako aplikacji ze Sklepu <xref:System.IO.Stream> Windows 8.x i odczytywania jego zawartości przy użyciu wystąpienia <xref:System.IO.StreamReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="15a0e-118">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a Windows 8.x Store app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="15a0e-119">Metoda asynchroniczna umożliwia otwarcie pliku jako strumienia i odczytanie jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="15a0e-119">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="15a0e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15a0e-120">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="15a0e-121">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="15a0e-121">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="15a0e-122">Asynchroniczne programowanie z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="15a0e-122">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="15a0e-123">Programowanie asynchroniczne z asynchroniczną i oczekiwaną (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15a0e-123">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
