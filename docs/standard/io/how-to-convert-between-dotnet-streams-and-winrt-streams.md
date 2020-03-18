---
title: 'Jak: Konwertować między .NET Framework i strumieniśrodowiska uruchomieniowego systemu Windows (tylko windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
ms.openlocfilehash: 7413c3fae7d7189ec8dca43b0c77f6b56158f416
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159471"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Jak: Konwertować między .NET Framework i strumieniśrodowiska uruchomieniowego systemu Windows (tylko windows)

Program .NET Framework dla aplikacji platformy Windows jest podzbiorem pełnej platformy .NET Framework. Ze względu na zabezpieczenia i inne wymagania dotyczące aplikacji platformy Windows, nie można użyć pełnego zestawu interfejsów API platformy .NET Framework do otwierania i odczytywania plików. Aby uzyskać więcej informacji, zobacz [omówienie aplikacji programu .NET dla programu WindowsP](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Jednak może być wymagane użycie interfejsów API programu .NET Framework w celu wykonywania innych operacji na strumieniach. Aby manipulować tymi strumieniami, można konwertować między <xref:System.IO.MemoryStream> typem strumienia .NET Framework, takim jak lub <xref:System.IO.FileStream>, a strumieniem środowiska uruchomieniowego systemu Windows, takim jak <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>lub <xref:Windows.Storage.Streams.IRandomAccessStream>.

Klasa <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> zawiera metody, które ułatwiają te konwersje. Jednak podstawowe różnice między .NET Framework i strumieniśrodowiska uruchomieniowego systemu Windows wpływają na wyniki korzystania z tych metod, zgodnie z opisem w następujących sekcjach:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Konwertowanie ze środowiska uruchomieniowego systemu Windows na strumień programu .NET Framework
Aby przekonwertować strumień środowiska uruchomieniowego systemu Windows na strumień <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> programu .NET Framework, należy użyć jednej z następujących metod:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType>Konwertuje strumień dostępu losowego w środowiskach środowiska uruchomieniowego systemu Windows do strumienia zarządzanego w programie .NET dla aplikacji systemu Windows.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType>Konwertuje strumień wyjściowy w czasie wykonywania systemu Windows do strumienia zarządzanego w programie .NET dla aplikacji systemu Windows.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType>Konwertuje strumień wejściowy w czasie wykonywania systemu Windows do strumienia zarządzanego w programie .NET dla aplikacji systemu Windows.

Środowisko uruchomieniowe systemu Windows oferuje typy strumienia, które obsługują tylko czytanie, pisanie lub czytanie i pisanie. Te funkcje są obsługiwane podczas konwertowania strumienia środowiska uruchomieniowego systemu Windows do strumienia .NET Framework. Co więcej, po przekonwertowaniu strumienia środowiska wykonawczego systemu Windows na strumień programu .NET Framework i z powrotem jest przywracane oryginalne wystąpienie strumienia środowiska wykonawczego systemu Windows.

Najlepszym rozwiązaniem jest użycie metody konwersji, która odpowiada możliwościom strumienia środowiska uruchomieniowego systemu Windows, który chcesz przekonwertować. Jednak ponieważ <xref:Windows.Storage.Streams.IRandomAccessStream> jest czytelny i zapisywalny <xref:Windows.Storage.Streams.IOutputStream> <xref:Windows.Storage.Streams.IInputStream>(implementuje oba i ), metody konwersji zachowują możliwości oryginalnego strumienia. Na przykład <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> za pomocą <xref:Windows.Storage.Streams.IRandomAccessStream> do konwersji nie ogranicza przekonwertowany strumień .NET Framework do czytelny. Jest również zapisywalny.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Przykład: Konwertowanie losowego dostępu środowiska uruchomieniowego systemu Windows do strumienia programu .NET Framework
Aby przekonwertować strumień losowego dostępu do środowiska uruchomieniowego <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> systemu Windows do strumienia .NET Framework, użyj tej metody.

Poniższy przykład kodu monituje o wybranie pliku, otwiera go za pomocą interfejsów API środowiska uruchomieniowego systemu Windows, a następnie konwertuje go do strumienia .NET Framework. Odczytuje strumień i wyprowadza go do bloku tekstu. Zazwyczaj można manipulować strumienia za pomocą interfejsów API platformy .NET Framework przed wypuszczeniem wyników.

Aby uruchomić ten przykład, utwórz aplikację XAML programu `TextBlock1` UWP `Button1`zawierającą blok tekstowy o nazwie i przycisk o nazwie . Skojarz zdarzenie kliknięcia `button1_Click` przycisku z metodą pokazaną w przykładzie.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Konwertowanie z programu .NET Framework na strumień środowiska uruchomieniowego systemu Windows
Aby przekonwertować strumień programu .NET Framework na strumień środowiska <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> uruchomieniowego systemu Windows, należy użyć jednej z następujących metod:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType>Konwertuje strumień zarządzany w programie .NET dla aplikacji systemu Windows na strumień wejściowy w czasie wykonywania systemu Windows.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType>Konwertuje strumień zarządzany w programie .NET dla aplikacji systemu Windows na strumień wyjściowy w czasie wykonywania systemu Windows.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A?displayProperty=nameWithType>Konwertuje strumień zarządzany w programie .NET dla aplikacji systemu Windows na strumień dostępu losowego, którego środowisko uruchomieniowe systemu Windows może używać do odczytu lub zapisu.

Podczas konwertowania strumienia programu .NET Framework na strumień środowiska uruchomieniowego systemu Windows możliwości przekonwertowanego strumienia zależą od oryginalnego strumienia. Na przykład jeśli oryginalny strumień obsługuje zarówno odczytu <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> i zapisu, a wywołanie `IRandomAccessStream`do konwersji strumienia, zwracany typ jest . `IRandomAccessStream`implementuje `IInputStream` `IOutputStream`i , i obsługuje czytanie i pisanie.

Strumienie .NET Framework nie obsługują klonowania, nawet po konwersji. W przypadku konwersji strumienia programu .NET Framework <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> na <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>strumień <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>środowiska uruchomieniowego <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> systemu Windows i wywołanie lub , które wywołanie lub wywołanie bezpośrednio, występuje wyjątek.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Przykład: Konwertowanie programu .NET Framework na strumień dostępu losowego w środowiskach środowiska uruchomieniowego systemu Windows

Aby przekonwertować ze strumienia programu .NET Framework na <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A> strumień losowego dostępu środowiska uruchomieniowego systemu Windows, należy użyć tej metody, jak pokazano w poniższym przykładzie:

> [!IMPORTANT]
> Upewnij się, że strumień .NET Framework, którego używasz obsługuje szukania lub skopiować go do strumienia, który nie. Można użyć <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> właściwości, aby to ustalić.

Aby uruchomić ten przykład, utwórz aplikację XAML platformy UWP, która jest przeznaczona dla programu .NET Framework 4.5.1 i zawiera blok tekstowy o nazwie `TextBlock2` i przycisk o nazwie `Button2`. Skojarz zdarzenie kliknięcia `button2_Click` przycisku z metodą pokazaną w przykładzie.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Zobacz też

- [Szybki start: Odczytywanie i zapisywanie pliku (Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464978(v=win.10))  
- [Omówienie aplikacji .NET dla Sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))  
- [Interfejsy API aplikacji .NET dla aplikacji ze Sklepu Windows](https://docs.microsoft.com/previous-versions/br230232(v=vs.120))  
