---
title: 'Instrukcje: Konwertowanie .NET Framework i środowiska wykonawczego Windows strumieni (tylko Windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22cf168c660349bda16c59aec4824e3283430807
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877936"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Instrukcje: Konwertowanie .NET Framework i środowiska wykonawczego Windows strumieni (tylko Windows)

Program .NET Framework dla aplikacji platformy uniwersalnej systemu Windows jest podzestawem pełnego .NET Framework. Ze względu na bezpieczeństwo i inne wymagania dotyczące aplikacji platformy uniwersalnej systemu Windows nie można używać pełnego zestawu interfejsów API programu .NET Framework do otwierania i odczytywania plików. Aby uzyskać więcej informacji, zobacz [.NET, aby uzyskać omówienie aplikacji platformy uniwersalnej systemu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Jednak może być wymagane użycie interfejsów API programu .NET Framework w celu wykonywania innych operacji na strumieniach. Do manipulowania te strumienie, można wykonywać konwersje między typ strumienia środowiska .NET Framework takich jak <xref:System.IO.MemoryStream> lub <xref:System.IO.FileStream>i strumieni środowiska wykonawczego Windows, takich jak <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>, lub <xref:Windows.Storage.Streams.IRandomAccessStream>.

<xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> Klasa zawiera metody ułatwiające wykonanie takiej konwersji jest łatwe. Jednak podstawowych różnic między strumieniami środowiska .NET Framework i środowiska wykonawczego Windows wpłynąć na wyniki użycia tych metod, zgodnie z opisem w poniższych sekcjach:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Konwertowanie środowiska uruchomieniowego Windows na strumień programu .NET Framework
Aby przekonwertować strumień środowiska wykonawczego Windows na strumień programu .NET Framework, użyj jednej z następujących <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> metody:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> Konwertuje strumień o dostępie losowym w taki sposób, w środowisku uruchomieniowym Windows na zarządzany strumień programu .NET dla aplikacji platformy uniwersalnej systemu Windows.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType> Konwertuje strumień wyjściowy środowiska wykonawczego Windows na zarządzany strumień programu .NET dla aplikacji platformy uniwersalnej systemu Windows.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> Konwertuje strumień wejściowy środowiska wykonawczego Windows na zarządzany strumień programu .NET dla aplikacji platformy uniwersalnej systemu Windows.

Środowisko wykonawcze Windows oferuje typy strumieni obsługujących tylko do czytania, zapisywania, oraz Odczyt i zapis. Te możliwości są zachowywane podczas konwersji strumienia środowiska wykonawczego Windows na strumień programu .NET Framework. Co więcej, po przekonwertowaniu strumienia środowiska wykonawczego systemu Windows na strumień programu .NET Framework i z powrotem jest przywracane oryginalne wystąpienie strumienia środowiska wykonawczego systemu Windows. 

Jest najlepszym rozwiązaniem jest użycie metody konwersji pasującej do możliwości strumienia środowiska wykonawczego Windows, który ma zostać przekonwertowany. Jednak ponieważ <xref:Windows.Storage.Streams.IRandomAccessStream> jest Odczytywalny i zapisywalny (implementuje interfejsy <xref:Windows.Storage.Streams.IOutputStream> i <xref:Windows.Storage.Streams.IInputStream>), metody konwersji Obsługa możliwości oryginalnego strumienia. Na przykład za pomocą <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> przekonwertować <xref:Windows.Storage.Streams.IRandomAccessStream> konwertowanego strumienia środowiska .NET Framework do odczytu nie są ograniczone. Jest również zapisu.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Przykład: Konwertuj dostępie losowym środowiska wykonawczego Windows na strumień .NET Framework
Aby dokonać konwersji strumienia dostępie losowym środowiska wykonawczego Windows na strumień programu .NET Framework, należy użyć <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> metody.

Poniższy kod wyświetli monit o wybranie pliku, otworzy go za pomocą interfejsów API środowiska wykonawczego Windows i następnie konwertuje go na strumień programu .NET Framework. Odczytuje strumień i umieszcza go w bloku tekstu. Użytkownik będzie strumieniu za pomocą interfejsów API programu .NET Framework przed zostaną zwrócone wyniki.

Aby uruchomić ten przykład, utworzyć aplikację XAML platformy uniwersalnej systemu Windows, która zawierała blok tekstu o nazwie `TextBlock1` i przycisk o nazwie `Button1`. Skojarz przycisk kliknij zdarzenie z `button1_Click` metoda pokazano w przykładzie.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Konwertowanie z .NET Framework na strumień środowiska wykonawczego Windows
Aby przekonwertować z .NET Framework na strumień środowiska wykonawczego Windows, użyj jednej z następujących <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> metody:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> Konwertuje zarządzany strumień programu .NET dla aplikacji platformy uniwersalnej systemu Windows na strumień wejściowy środowiska wykonawczego Windows.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType> Konwertuje zarządzany strumień programu .NET dla aplikacji platformy uniwersalnej systemu Windows na strumień wyjściowy środowiska wykonawczego Windows.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A?displayProperty=nameWithType> Konwertuje zarządzany strumień programu .NET dla aplikacji platformy uniwersalnej systemu Windows na strumień o dostępie losowym, do używanego przez środowisko wykonawcze Windows do odczytu lub zapisu.

Po przekonwertowaniu strumień programu .NET Framework na strumień środowiska wykonawczego Windows możliwości konwertowanego strumienia zależą od oryginalnego strumienia. Na przykład, jeśli oryginalny strumień obsługuje Odczyt i zapis i wywołania <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> celu przekonwertowania strumienia, jest zwracany typ `IRandomAccessStream`. `IRandomAccessStream` implementuje `IInputStream` i `IOutputStream`i obsługuje Odczyt i zapis.

Strumieniami programu .NET framework nie obsługują klonowania, nawet po konwersji. Po konwersji strumień programu .NET Framework na strumień środowiska wykonawczego Windows, a wywołanie <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> lub <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, która wywołuje metodę <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>, lub jeśli wywołasz <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> bezpośrednio, wystąpi wyjątek.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Przykład: Konwertuj .NET Framework na strumień o dostępie losowym środowiska wykonawczego Windows

Aby przekonwertować programu .NET Framework na strumień środowiska wykonawczego Windows-strumień o dostępie losowym, należy użyć <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A> metodzie, jak pokazano w poniższym przykładzie:

> [!IMPORTANT]
> Upewnij się, że strumień programu .NET Framework, którego używasz, obsługuje wyszukiwanie lub skopiuj go do strumienia, który obsługuje. Możesz użyć <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> właściwości.

Aby uruchomić ten przykład, tworzenie aplikacji platformy uniwersalnej systemu Windows, XAML, który jest przeznaczony dla .NET Framework 4.5.1 i zawierała blok tekstu o nazwie `TextBlock2` i przycisk o nazwie `Button2`. Skojarz przycisk kliknij zdarzenie z `button2_Click` metoda pokazano w przykładzie.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Zobacz także

- [Szybki start: Odczyt i zapis pliku (Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464978(v=win.10))  
- [Omówienie aplikacji .NET dla Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))  
- [Platforma .NET dla interfejsów API aplikacji Windows Store](https://docs.microsoft.com/previous-versions/br230232(v=vs.120))  
