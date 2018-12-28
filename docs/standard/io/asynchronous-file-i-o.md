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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7bfa35b8361f154fcbaa2ea7d7f8ddff5321003d
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610440"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="85612-102">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="85612-102">Asynchronous File I/O</span></span>

<span data-ttu-id="85612-103">Mechanizm operacji asynchronicznych umożliwia wykonywanie operacji We/Wy mocno obciążających zasoby bez blokowania wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="85612-103">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="85612-104">Ten aspekt dotyczący wydajności jest szczególnie ważny w aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] lub aplikacjach [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)], gdzie czasochłonne operacje strumieniowe mogą zablokować wątek interfejsu użytkownika i spowodować, że aplikacja będzie wyglądać, jakby przestała działać.</span><span class="sxs-lookup"><span data-stu-id="85612-104">This performance consideration is particularly important in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app or [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)] app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="85612-105">Począwszy od oprogramowania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] typy We/Wy zawierają metody asynchroniczne, które upraszczają wykonywanie operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="85612-105">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="85612-106">Metoda asynchroniczna ma w nazwie element `Async`, np. <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> lub <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="85612-106">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="85612-107">Te metody asynchroniczne są implementowane w klasach strumieniowych, takich jak <xref:System.IO.Stream>, <xref:System.IO.FileStream> i <xref:System.IO.MemoryStream>, oraz klasach służących do odczytu /zapisu do strumieni, takich jak <xref:System.IO.TextReader> i <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="85612-107">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="85612-108">W programie .NET Framework w wersji 4 i starszych do implementowania asynchronicznych operacji We/Wy należy używać metod takich jak <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A>.</span><span class="sxs-lookup"><span data-stu-id="85612-108">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="85612-109">Metody te są nadal dostępne w programie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do obsługi starszego kodu, natomiast metody asynchroniczne pozwalają znacznie łatwiej implementować asynchroniczne operacje We/Wy.</span><span class="sxs-lookup"><span data-stu-id="85612-109">These methods are still available in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="85612-110">C# i Visual Basic każdego mają dwa słowa kluczowe do programowania asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="85612-110">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="85612-111">Modyfikator `Async` (Visual Basic) lub `async` (C#), który służy do oznaczania metody zawierającej operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="85612-111">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="85612-112">Operator `Await` (Visual Basic) lub `await` (C#), który jest stosowany do wyniku metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="85612-112">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="85612-113">W celu implementowania asynchronicznych operacji We/Wy należy używać tych słów kluczowych w połączeniu z metodami asynchronicznymi, jak pokazano w przykładach poniżej.</span><span class="sxs-lookup"><span data-stu-id="85612-113">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="85612-114">Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z async i await (C#)](../../csharp/programming-guide/concepts/async/index.md) lub [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="85612-114">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="85612-115">W tym przykładzie pokazano, jak za pomocą dwóch obiektów <xref:System.IO.FileStream> skopiować pliki asynchronicznie z jednego katalogu do innego.</span><span class="sxs-lookup"><span data-stu-id="85612-115">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="85612-116">Program obsługi zdarzeń <xref:System.Web.UI.WebControls.Button.Click> kontrolki <xref:System.Windows.Controls.Button> jest oznaczony modyfikatorem `async`, ponieważ wywołuje metodę asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="85612-116">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="85612-117">Następny przykład jest podobny do poprzedniego, tylko obiekty <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> służą do asynchronicznego odczytywania i zapisywania zawartości pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="85612-117">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="85612-118">W kolejnym przykładzie pokazano plik związany z kodem i plik XAML, które służą do otwarcia pliku w postaci klasy <xref:System.IO.Stream> w aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], a następnie odczytania jego zawartości przy użyciu wystąpienia klasy <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="85612-118">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="85612-119">Metoda asynchroniczna umożliwia otwarcie pliku jako strumienia i odczytanie jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="85612-119">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="85612-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85612-120">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="85612-121">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="85612-121">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="85612-122">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="85612-122">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="85612-123">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85612-123">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)