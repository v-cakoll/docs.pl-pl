---
title: Asynchroniczne We/Wy pliku
description: Przeczytaj o asynchronicznym we/wy pliku na platformie .NET. Poznaj metody asynchroniczne, aby uprościć asynchroniczne operacje, takie jak ReadAsync, WriteAsync i inne.
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
ms.openlocfilehash: 9506a366b6f1e363ec13550e5ed68c7176dd4d0a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598622"
---
# <a name="asynchronous-file-io"></a>Asynchroniczne We/Wy pliku

Mechanizm operacji asynchronicznych umożliwia wykonywanie operacji We/Wy mocno obciążających zasoby bez blokowania wątku głównego. Ten wpływ na wydajność jest szczególnie istotny w aplikacji do sklepu Windows 8. x lub aplikacji klasycznej, w której czasochłonna operacja przesyłania strumieniowego może blokować wątek interfejsu użytkownika i sprawiać, że aplikacja wygląda tak, jakby nie działała.

Począwszy od .NET Framework 4,5, typy we/wy obejmują metody asynchroniczne upraszczające asynchroniczne operacje. Metoda asynchroniczna ma w nazwie element `Async`, np. <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> lub <xref:System.IO.TextReader.ReadToEndAsync%2A>. Te metody asynchroniczne są implementowane w klasach strumieniowych, takich jak <xref:System.IO.Stream>, <xref:System.IO.FileStream> i <xref:System.IO.MemoryStream>, oraz klasach służących do odczytu /zapisu do strumieni, takich jak <xref:System.IO.TextReader> i <xref:System.IO.TextWriter>.

W programie .NET Framework w wersji 4 i starszych do implementowania asynchronicznych operacji We/Wy należy używać metod takich jak <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A>. Te metody są nadal dostępne w .NET Framework 4,5 do obsługi starszego kodu; jednak metody asynchroniczne umożliwiają łatwiejsze implementowanie asynchronicznych operacji we/wy.

W języku C# i Visual Basic każdy z nich ma dwa słowa kluczowe do programowania asynchronicznego:

- Modyfikator `Async` (Visual Basic) lub `async` (C#), który służy do oznaczania metody zawierającej operację asynchroniczną.

- Operator `Await` (Visual Basic) lub `await` (C#), który jest stosowany do wyniku metody asynchronicznej.

W celu implementowania asynchronicznych operacji We/Wy należy używać tych słów kluczowych w połączeniu z metodami asynchronicznymi, jak pokazano w przykładach poniżej. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z Async i Await (C#)](../../csharp/programming-guide/concepts/async/index.md) lub [asynchroniczne programowanie z asynchroniczne i Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).

W tym przykładzie pokazano, jak za pomocą dwóch obiektów <xref:System.IO.FileStream> skopiować pliki asynchronicznie z jednego katalogu do innego. Program obsługi zdarzeń <xref:System.Web.UI.WebControls.Button.Click> kontrolki <xref:System.Windows.Controls.Button> jest oznaczony modyfikatorem `async`, ponieważ wywołuje metodę asynchroniczną.

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

Następny przykład jest podobny do poprzedniego, tylko obiekty <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> służą do asynchronicznego odczytywania i zapisywania zawartości pliku tekstowego.

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

W następnym przykładzie przedstawiono plik związany z kodem i plik XAML, który służy do otwierania pliku jako <xref:System.IO.Stream> w aplikacji ze sklepu Windows 8. x i odczytywania jego zawartości przy użyciu wystąpienia <xref:System.IO.StreamReader> klasy. Metoda asynchroniczna umożliwia otwarcie pliku jako strumienia i odczytanie jego zawartości.

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.Stream>
- [We/wy plików i strumieni](index.md)
- [Programowanie asynchroniczne z Async i Await (C#)](../../csharp/programming-guide/concepts/async/index.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
