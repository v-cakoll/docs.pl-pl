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
ms.openlocfilehash: f67f88cd7f690e56664fa45878d1c9ac1f8a6b6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577564"
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Porady: konwersja strumieni platformy .NET Framework i strumieni środowiska wykonawczego systemu Windows
Program .NET Framework dla aplikacji do Sklepu Windows to podzestaw funkcji pełnego programu .NET Framework. Ze względu na zabezpieczenia i inne wymagania aplikacji do Sklepu Windows nie można używać pełnego zestawu interfejsów API programu .NET Framework w celu otwierania i odczytywania plików. Aby uzyskać więcej informacji, zobacz [Omówienie aplikacji .NET dla Sklepu Windows](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). Jednak może być wymagane użycie interfejsów API programu .NET Framework w celu wykonywania innych operacji na strumieniach. Do manipulowania tych strumieni, może być konieczne konwersji między typem strumienia .NET Framework takie jak <xref:System.IO.MemoryStream> lub <xref:System.IO.FileStream>, a strumień środowiska wykonawczego systemu Windows, takich jak [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx), [IOutputStream ](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx), lub [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx).  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` Klasa zawiera metody, które umożliwiają łatwe tych konwersji. Istnieją jednak podstawowe różnice między strumieniami w programie .NET Framework i środowisku wykonawczym systemu Windows, które mają wpływ na wyniki użycia tych metod. Szczegóły opisano w poniższych sekcjach.  
  
<a name="BKMK_ConvertingfromaWindowsRuntimestreamtoaNETFrameworkstream"></a>   
## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Konwertowanie strumienia środowiska wykonawczego systemu Windows na strumień programu .NET Framework  
 Można przekonwertować ze strumienia środowiska wykonawczego systemu Windows na strumieniu .NET Framework za pomocą jednej z następujących <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` metod:  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream`  
 Konwertuje strumień o dostępie losowym w środowisku wykonawczym systemu Windows na zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite`
 Konwertuje strumień wyjściowy w środowisku wykonawczym systemu Windows na zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead`  
 Konwertuje strumień wejściowy w środowisku wykonawczym systemu Windows na zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows.  
  
 Środowisko wykonawcze systemu Windows oferuje typy strumieni obsługujących tylko odczyt, tylko zapis oraz odczyt i zapis, a te możliwości są zachowywane podczas konwersji strumienia środowiska wykonawczego systemu Windows na strumień programu .NET Framework. Co więcej, po przekonwertowaniu strumienia środowiska wykonawczego systemu Windows na strumień programu .NET Framework i z powrotem jest przywracane oryginalne wystąpienie strumienia środowiska wykonawczego systemu Windows. Najlepszym rozwiązaniem jest użycie metody konwersji pasującej do możliwości konwertowanego strumienia środowiska wykonawczego systemu Windows. Ponieważ jednak [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) jest do odczytu i zapisu (zarówno implementuje [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx) i [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx)), można użyć dowolnej z metod konwersji i możliwości oryginalnego strumienia są obsługiwane. Na przykład za pomocą <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead` przekonwertować [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) nie ograniczy przekonwertowanego strumienia .NET Framework jest tylko do odczytu; również być zapisywalny.  
  
#### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Aby przekonwertować strumień o dostępie losowym środowiska wykonawczego systemu Windows na strumień programu .NET Framework  
  
-   Użyj <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream` metody.  
  
     W poniższym przykładzie kodu pokazano, jak monitować użytkownika o wybranie pliku, otworzyć ten plik za pomocą interfejsów API środowiska wykonawczego systemu Windows, a następnie przekonwertować go na strumień programu .NET Framework, który zostanie odczytany i umieszczony w bloku tekstu. W tym scenariuszu typowe operacje na strumieniu będą wykonywane przy użyciu interfejsów API programu .NET Framework, po czym zostaną zwrócone wyniki.  
  
     Aby uruchomić ten przykład, należy utworzyć aplikacji Sklepu Windows w języku XAML, który zawiera blok tekstowy o nazwie `TextBlock1` i przycisk o nazwie `Button1`. Kliknij przycisk zdarzenia musi być skojarzone z `button1_Click` metody pokazano w przykładzie.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]  
  
<a name="BKMK_ConvertingfromaNETFrameworkstreamtoaWindowsRuntimestream"></a>   
## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Konwertowanie strumienia programu .NET Framework na strumień środowiska wykonawczego systemu Windows  
 Można przekonwertować strumienia .NET Framework do strumienia środowiska wykonawczego systemu Windows przy użyciu jednej z następujących <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` metod:  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream`  
 Konwertuje zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows na strumień wejściowy środowiska wykonawczego systemu Windows.  
  
<!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A>  --> `System.IO.WindowsRuntimeStreamExtensions.AsOutputStream`
 Konwertuje zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows na strumień wyjściowy środowiska wykonawczego systemu Windows.  
  
 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md)  
 Konwertuje zarządzany strumień podzestawu programu .NET dla aplikacji do Sklepu Windows na strumień o dostępie losowym, którego można używać do odczytu lub zapisu w środowisku wykonawczym systemu Windows.  
  
 W przypadku konwersji strumienia programu .NET Framework na strumień środowiska wykonawczego systemu Windows możliwości konwertowanego strumienia będą zależeć od oryginalnego strumienia. Na przykład, jeśli oryginalny strumienia obsługuje odczytywanie i zapisywanie i wywołania <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream` przekonwertować strumienia, będzie zwrócony typ `IRandomAccessStream`, który implementuje `IInputStream` i `IOutputStream`i obsługuje Odczyt i Zapisywanie  
  
 Strumienie programu .NET Framework nie obsługują klonowania, nawet po konwersji. Oznacza to, że jeśli Konwertuj strumienia .NET Framework na strumień środowiska wykonawczego systemu Windows i wywołanie [GetInputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.inmemoryrandomaccessstream.getinputstreamat.aspx) lub [GetOutputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.getoutputstreamat.aspx), którego wywołanie [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) lub wywołania [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) bezpośrednio, wystąpi wyjątek.  
  
#### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Aby przekonwertować strumień programu .NET Framework na strumień o dostępie losowym środowiska wykonawczego systemu Windows  
  
-   Użyj [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) metody, jak pokazano w poniższym przykładzie.  
  
    > [!IMPORTANT]
    >  Upewnij się, że strumień programu .NET Framework, którego używasz, obsługuje przeszukiwanie lub skopiuj go do strumienia, który obsługuje przeszukiwanie. Można użyć <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> właściwości, aby ustalić tę liczbę.  
  
     Aby uruchomić ten przykład, należy utworzyć aplikacji Sklepu Windows w języku XAML, który jest przeznaczony dla programu .NET Framework 4.5.1 i zawiera blok tekstowy o nazwie `TextBlock2` i przycisk o nazwie `Button2`. Kliknij przycisk zdarzenia musi być skojarzone z `button2_Click` metod przedstawionych w tym przykładzie.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki Start: Odczytywanie i zapisywanie pliku (system Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
 [Omówienie aplikacji .NET dla Sklepu Windows](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [.NET dla Sklepu Windows apps — obsługiwanych interfejsów API](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)
