---
title: Projektowanie aplikacji konsoli w programie .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79005c69e8c125e78573a44f34740632676faf59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="building-console-applications-in-the-net-framework"></a>Projektowanie aplikacji konsoli w programie .NET Framework
Aplikacje w programie .NET Framework mogą używać <xref:System.Console?displayProperty=nameWithType> klasy odczytywanie znaków z i zapisywanie znaków do konsoli. Dane z konsoli są odczytywane z Standardowy strumień wejściowy, dane w konsoli są zapisywane do standardowego strumienia wyjściowego, a dane błąd w konsoli są zapisywane do strumienia wyjściowego błąd standardowy. Tych strumieni są automatycznie kojarzone z konsoli po uruchomieniu aplikacji i są widoczne jako <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, i <xref:System.Console.Error%2A> właściwości, odpowiednio.  
  
 Wartość <xref:System.Console.In%2A?displayProperty=nameWithType> właściwość jest <xref:System.IO.TextReader?displayProperty=nameWithType> obiektu, natomiast wartości <xref:System.Console.Out%2A?displayProperty=nameWithType> i <xref:System.Console.Error%2A?displayProperty=nameWithType> właściwości są <xref:System.IO.TextWriter?displayProperty=nameWithType> obiektów. Te właściwości można skojarzyć z strumieni, które nie reprezentują konsoli, umożliwiając punktu strumienia do innej lokalizacji dla danych wejściowych lub wyjściowych. Na przykład przekierować dane wyjściowe do pliku przez ustawienie <xref:System.Console.Out%2A?displayProperty=nameWithType> właściwości <xref:System.IO.StreamWriter?displayProperty=nameWithType>, który hermetyzuje <xref:System.IO.FileStream?displayProperty=nameWithType> za pomocą klasy <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metody. <xref:System.Console.In%2A?displayProperty=nameWithType> i <xref:System.Console.Out%2A?displayProperty=nameWithType> właściwości nie muszą odwoływać się do tego samego strumienia.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji dotyczących tworzenia aplikacji konsoli, w tym przykłady w języku C#, Visual Basic i C++, zobacz dokumentację <xref:System.Console> klasy.  
  
 Jeśli konsola nie istnieje, tak jak aplikacji systemu Windows, dane wyjściowe zapisywane do standardowego strumienia wyjściowego nie będą widoczne, ponieważ nie mogła zapisać informacji do konsoli. Zapisywanie informacji o niedostępny konsoli nie powoduje wygenerowany wyjątek.  
  
 Aby włączyć konsoli do odczytywania i zapisywania w aplikacji systemu Windows, który został utworzony przy użyciu programu Visual Studio, otwórz projekt **właściwości** okno dialogowe, kliknij przycisk **aplikacji** a następnie ustaw **typu aplikacji** do **aplikacji konsoli**.  
  
 Aplikacje konsoli nie mają przekazywanie komunikatów, który uruchamia się domyślnie. W związku z tym wywołania konsoli Microsoft Win32 czasomierze może zakończyć się niepowodzeniem.  
  
 **System.Console** klasa zawiera metody, które mogą odczytywać znaki lub całe wiersze z konsoli. Inne metody Konwertowanie ciągów danych i format, a następnie wpisz ciągi sformatowane do konsoli. Aby uzyskać więcej informacji na ciągach formatowania, zobacz [typy formatowania](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Console?displayProperty=nameWithType>  
 [Formatowanie typów](../../docs/standard/base-types/formatting-types.md)
