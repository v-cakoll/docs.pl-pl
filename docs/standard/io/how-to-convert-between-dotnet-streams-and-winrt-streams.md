---
title: 'Porady: konwersja strumieni platformy .NET Framework i strumieni środowiska wykonawczego systemu Windows'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3cfaf4cf22bba445d774c653ff7797d535bcde2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398968"
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Porady: konwersja strumieni platformy .NET Framework i strumieni środowiska wykonawczego systemu Windows

Program .NET Framework dla aplikacji do Sklepu Windows to podzestaw funkcji pełnego programu .NET Framework. Ze względu na zabezpieczenia i inne wymagania aplikacji do Sklepu Windows nie można używać pełnego zestawu interfejsów API programu .NET Framework w celu otwierania i odczytywania plików. Aby uzyskać więcej informacji, zobacz [Omówienie aplikacji .NET dla Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Jednak może być wymagane użycie interfejsów API programu .NET Framework w celu wykonywania innych operacji na strumieniach. Do manipulowania te strumienie, może okazać się niezbędne do konwersji między typem strumienia środowiska .NET Framework, takich jak <xref:System.IO.MemoryStream> lub <xref:System.IO.FileStream>i strumieni środowiska wykonawczego Windows, takich jak <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>, lub <xref:Windows.Storage.Streams.IRandomAccessStream>.

[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) klasa zawiera metody ułatwiające wykonanie takiej konwersji jest łatwe. Istnieją jednak podstawowe różnice między strumieniami w programie .NET Framework i środowisku wykonawczym systemu Windows, które mają wpływ na wyniki użycia tych metod. Szczegóły opisano w poniższych sekcjach.

## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Konwertowanie strumienia środowiska wykonawczego systemu Windows na strumień programu .NET Framework

Można przekonwertować strumień środowiska wykonawczego Windows na strumień programu .NET Framework przy użyciu jednej z następujących [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) metody:

[System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx)  
Konwertuje strumień o dostępie losowym w środowisku wykonawczym systemu Windows na zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows.

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx)  
Konwertuje strumień wyjściowy w środowisku wykonawczym systemu Windows na zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows.

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx)  
Konwertuje strumień wejściowy w środowisku wykonawczym systemu Windows na zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows.

Środowisko wykonawcze systemu Windows oferuje typy strumieni obsługujących tylko odczyt, tylko zapis oraz odczyt i zapis, a te możliwości są zachowywane podczas konwersji strumienia środowiska wykonawczego systemu Windows na strumień programu .NET Framework. Co więcej, po przekonwertowaniu strumienia środowiska wykonawczego systemu Windows na strumień programu .NET Framework i z powrotem jest przywracane oryginalne wystąpienie strumienia środowiska wykonawczego systemu Windows. Najlepszym rozwiązaniem jest użycie metody konwersji pasującej do możliwości konwertowanego strumienia środowiska wykonawczego systemu Windows. Jednak ponieważ <xref:Windows.Storage.Streams.IRandomAccessStream> jest Odczytywalny i zapisywalny (implementuje interfejsy <xref:Windows.Storage.Streams.IOutputStream> i <xref:Windows.Storage.Streams.IInputStream>, możesz użyć dowolnej metody konwersji i możliwości oryginalnego strumienia są zachowywane. Na przykład za pomocą [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) przekonwertować <xref:Windows.Storage.Streams.IRandomAccessStream> nie spowoduje ograniczenia przekonwertowanego strumienia środowiska .NET Framework tylko do odczytu; pozostanie on także zapisu.

### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Aby przekonwertować strumień o dostępie losowym środowiska wykonawczego systemu Windows na strumień programu .NET Framework

- Użyj [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) metody.

  W poniższym przykładzie kodu pokazano, jak monitować użytkownika o wybranie pliku, otworzyć ten plik za pomocą interfejsów API środowiska wykonawczego systemu Windows, a następnie przekonwertować go na strumień programu .NET Framework, który zostanie odczytany i umieszczony w bloku tekstu. W tym scenariuszu typowe operacje na strumieniu będą wykonywane przy użyciu interfejsów API programu .NET Framework, po czym zostaną zwrócone wyniki.

  Aby uruchomić ten przykład, należy utworzyć aplikację Windows Store XAML, która zawiera blok tekstu o nazwie `TextBlock1` i przycisk o nazwie `Button1`. Przycisk kliknij zdarzenie musi być skojarzone z `button1_Click` metoda pokazano w przykładzie.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]

## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Konwertowanie strumienia programu .NET Framework na strumień środowiska wykonawczego systemu Windows

Można przekonwertować programu .NET Framework na strumień środowiska wykonawczego Windows przy użyciu jednej z następujących [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) metody:

[System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) konwertuje zarządzany strumień podzestawu programu .NET dla Windows Store aplikacji na strumień wejściowy środowiska wykonawczego Windows.

[System.IO.WindowsRuntimeStreamExtensions.AsOutputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asoutputstream.aspx) konwertuje zarządzany strumień podzestawu programu .NET dla Windows Store aplikacji na strumień wyjściowy środowiska wykonawczego Windows.

[AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) konwertuje zarządzany strumień podzestawu programu .NET dla Windows Store aplikacji na strumień o dostępie losowym, na który może służyć do odczytu lub zapisu ze środowiska wykonawczego Windows.

W przypadku konwersji strumienia programu .NET Framework na strumień środowiska wykonawczego systemu Windows możliwości konwertowanego strumienia będą zależeć od oryginalnego strumienia. Na przykład, jeśli oryginalny strumień obsługuje Odczyt i zapis i wywołania[System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) celu przekonwertowania strumienia, zwracanym typem będzie `IRandomAccessStream`, która implementuje `IInputStream` i `IOutputStream`i obsługuje Odczyt i zapis.

Strumienie programu .NET Framework nie obsługują klonowania, nawet po konwersji. Oznacza to, że po konwersji strumień programu .NET Framework na strumień środowiska wykonawczego Windows, a wywołanie <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> lub <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, która wywołuje metodę <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> lub zadzwoń <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> bezpośrednio, wystąpi wyjątek.

### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Aby przekonwertować strumień programu .NET Framework na strumień o dostępie losowym środowiska wykonawczego systemu Windows

- Użyj [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) metodzie, jak pokazano w poniższym przykładzie:

  > [!IMPORTANT]
  > Upewnij się, że strumień programu .NET Framework, którego używasz, obsługuje przeszukiwanie lub skopiuj go do strumienia, który obsługuje przeszukiwanie. Możesz użyć <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> właściwości.

  Aby uruchomić ten przykład, należy utworzyć aplikację Windows Store XAML, który jest przeznaczony dla .NET Framework 4.5.1 i zawierała blok tekstu o nazwie `TextBlock2` i przycisk o nazwie `Button2`. Przycisk kliknij zdarzenie musi być skojarzone z `button2_Click` metod przedstawionych w tym przykładzie.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]

## <a name="see-also"></a>Zobacz też

[Szybki Start: Odczyt i zapis pliku (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
[Omówienie aplikacji .NET dla Windows Store](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
[Aplikacje .NET for Windows Store — obsługiwane interfejsy API](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)  