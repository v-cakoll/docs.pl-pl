---
title: Projektowanie aplikacji konsoli w programie .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: 1ec65795a7f3d706b2878dd8a8397ae42b61ce7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132865"
---
# <a name="building-console-applications-in-the-net-framework"></a>Projektowanie aplikacji konsoli w programie .NET Framework
Aplikacje w .NET Framework <xref:System.Console?displayProperty=nameWithType> można użyć klasy do odczytu znaków z i zapisu znaków do konsoli. Dane z konsoli są odczytywane ze standardowego strumienia wejściowego, dane do konsoli są zapisywane w standardowym strumieniu wyjściowym, a dane o błędach konsoli są zapisywane w standardowym strumieniu wyjściowym błędów. Te strumienie są automatycznie skojarzone z konsolą podczas <xref:System.Console.In%2A>uruchamiania aplikacji i są przedstawiane odpowiednio jako , <xref:System.Console.Out%2A>i <xref:System.Console.Error%2A> właściwości.  
  
 Wartość <xref:System.Console.In%2A?displayProperty=nameWithType> właściwości jest <xref:System.IO.TextReader?displayProperty=nameWithType> obiektem, podczas gdy wartości <xref:System.Console.Out%2A?displayProperty=nameWithType> <xref:System.Console.Error%2A?displayProperty=nameWithType> i właściwości <xref:System.IO.TextWriter?displayProperty=nameWithType> są obiektami. Te właściwości można skojarzyć ze strumieniami, które nie reprezentują konsoli, umożliwiając wskażenie strumienia do innej lokalizacji dla danych wejściowych lub wyjściowych. Na przykład można przekierować dane wyjściowe do <xref:System.Console.Out%2A?displayProperty=nameWithType> pliku, <xref:System.IO.StreamWriter?displayProperty=nameWithType>ustawiając właściwość na , <xref:System.IO.FileStream?displayProperty=nameWithType> która hermetyzuje a za pomocą <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metody. Właściwości <xref:System.Console.In%2A?displayProperty=nameWithType> <xref:System.Console.Out%2A?displayProperty=nameWithType> i nie muszą odwoływać się do tego samego strumienia.  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat tworzenia aplikacji konsoli, w tym przykłady w języku C#, Visual Basic i C++, zobacz dokumentację <xref:System.Console> dla klasy.  
  
 Jeśli konsola nie istnieje, tak jak w aplikacji opartej na systemie Windows, dane wyjściowe zapisane w standardowym strumieniu wyjściowym nie będą widoczne, ponieważ nie ma konsoli do zapisania informacji. Zapisywanie informacji do niedostępnej konsoli nie powoduje, że wyjątek ma być wywoływany.  
  
 Alternatywnie, aby włączyć konsolę do odczytu i zapisu w aplikacji opartej na systemie Windows, która jest opracowywana przy użyciu programu Visual Studio, otwórz okno dialogowe **Właściwości** projektu, kliknij kartę **Aplikacja** i ustaw **typ aplikacji** na Aplikacja **konsoli**.  
  
 Aplikacje konsoli brak pompy komunikatów, który uruchamia się domyślnie. W związku z tym wywołania konsoli do czasomierzy Microsoft Win32 może zakończyć się niepowodzeniem.  
  
 Klasa **System.Console** ma metody, które mogą odczytywać pojedyncze znaki lub całe wiersze z konsoli. Inne metody konwertują ciągi danych i formatowania, a następnie zapisują sformatowane ciągi do konsoli. Aby uzyskać więcej informacji na temat ciągów formatowania, zobacz [Typy formatowania](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Console?displayProperty=nameWithType>
- [Formatowanie typów](../../docs/standard/base-types/formatting-types.md)
