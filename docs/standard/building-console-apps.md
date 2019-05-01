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
ms.openlocfilehash: 135decebcd071c611cf6e72835fee33d49088070
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772583"
---
# <a name="building-console-applications-in-the-net-framework"></a>Projektowanie aplikacji konsoli w programie .NET Framework
Aplikacje w programie .NET Framework mogą używać <xref:System.Console?displayProperty=nameWithType> klasy znaków z do odczytywania i zapisywania znaków konsoli. Dane z konsoli są odczytywane ze standardowego strumienia wejściowego, dane w konsoli są zapisywane do strumienia wyjścia standardowego i dane o błędach w konsoli są zapisywane do błędu standardowego strumienia wyjściowego. Te strumienie są automatycznie kojarzone z konsoli, po uruchomieniu aplikacji i są widoczne jako <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, i <xref:System.Console.Error%2A> właściwości, odpowiednio.  
  
 Wartość <xref:System.Console.In%2A?displayProperty=nameWithType> właściwość <xref:System.IO.TextReader?displayProperty=nameWithType> obiektu, natomiast wartości <xref:System.Console.Out%2A?displayProperty=nameWithType> i <xref:System.Console.Error%2A?displayProperty=nameWithType> właściwości są <xref:System.IO.TextWriter?displayProperty=nameWithType> obiektów. Te właściwości można skojarzyć z strumieni, które reprezentują konsoli, co umożliwia wskazać inną lokalizację dla danych wejściowych lub wyjściowych w strumieniu. Na przykład przekierować dane wyjściowe do pliku, ustawiając <xref:System.Console.Out%2A?displayProperty=nameWithType> właściwości <xref:System.IO.StreamWriter?displayProperty=nameWithType>, która hermetyzuje <xref:System.IO.FileStream?displayProperty=nameWithType> poprzez <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metody. <xref:System.Console.In%2A?displayProperty=nameWithType> i <xref:System.Console.Out%2A?displayProperty=nameWithType> właściwości nie są do odwoływania się do tego samego strumienia.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat tworzenia aplikacji konsoli, wraz z przykładami w języku C#, Visual Basic i C++, zobacz dokumentację dla <xref:System.Console> klasy.  
  
 Jeśli konsola nie istnieje, tak jak w przypadku aplikacji z Windows zapisywane do strumienia wyjścia standardowego wyjścia nie będą widoczne, ponieważ konsola nie mogła zapisać informacji do. Zapisywanie informacji o niedostępny konsoli nie powoduje wyjątek.  
  
 Alternatywnie, aby włączyć konsoli do odczytu i zapisu w ramach aplikacji opartych na Windows utworzonego za pomocą programu Visual Studio, otwórz projektu **właściwości** okno dialogowe, kliknij przycisk **aplikacji** a następnie ustaw **typ aplikacji** do **aplikację Konsolową**.  
  
 Aplikacje konsoli braku pompy komunikatów, który uruchamia się domyślnie. W związku z tym wywołania konsoli czasomierzy Microsoft Win32 może zakończyć się niepowodzeniem.  
  
 **System.Console** klasa zawiera metody, które można czytać pojedyncze znaki lub całe wiersze z konsoli. Inne metody konwersji danych i format ciągów znaków, a następnie wpisz sformatowane ciągi do konsoli. Aby uzyskać więcej informacji na temat formatowania ciągów, zobacz [typy formatowania](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Console?displayProperty=nameWithType>
- [Formatowanie typów](../../docs/standard/base-types/formatting-types.md)
