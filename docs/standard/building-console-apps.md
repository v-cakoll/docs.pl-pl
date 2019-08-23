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
ms.openlocfilehash: 5c1658f27b66d9447d191d23801eba2d659ce9c2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933900"
---
# <a name="building-console-applications-in-the-net-framework"></a>Projektowanie aplikacji konsoli w programie .NET Framework
Aplikacje w .NET Framework mogą używać <xref:System.Console?displayProperty=nameWithType> klasy, aby odczytywać znaki z i pisać znaki w konsoli. Dane z konsoli są odczytywane ze standardowego strumienia wejściowego, dane do konsoli są zapisywane w standardowym strumieniu wyjściowym, a dane błędów do konsoli są zapisywane w standardowym strumieniu wyjściowym błędu. Te strumienie są automatycznie kojarzone z konsolą programu <xref:System.Console.In%2A>, gdy aplikacja jest uruchamiana i są prezentowane odpowiednio jako właściwości, <xref:System.Console.Out%2A>i <xref:System.Console.Error%2A> .  
  
 <xref:System.Console.In%2A?displayProperty=nameWithType> Wartość właściwości <xref:System.Console.Out%2A?displayProperty=nameWithType> <xref:System.IO.TextWriter?displayProperty=nameWithType> jest obiektem, natomiast wartości właściwości i <xref:System.Console.Error%2A?displayProperty=nameWithType> są obiektami. <xref:System.IO.TextReader?displayProperty=nameWithType> Można skojarzyć te właściwości ze strumieniami, które nie reprezentują konsoli, dzięki czemu można wskazywać strumień do innej lokalizacji dla danych wejściowych lub wyjściowych. Na przykład można przekierować dane wyjściowe do <xref:System.Console.Out%2A?displayProperty=nameWithType> pliku przez ustawienie właściwości <xref:System.IO.StreamWriter?displayProperty=nameWithType>na <xref:System.IO.FileStream?displayProperty=nameWithType> , która hermetyzuje za <xref:System.Console.SetOut%2A?displayProperty=nameWithType> pomocą metody. Właściwości <xref:System.Console.In%2A?displayProperty=nameWithType> i<xref:System.Console.Out%2A?displayProperty=nameWithType> nie muszą odwoływać się do tego samego strumienia.  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat tworzenia aplikacji konsolowych, C#w tym przykładów w C++, Visual Basic i, zobacz <xref:System.Console> dokumentację klasy.  
  
 Jeśli konsola programu nie istnieje, podobnie jak w aplikacji opartej na systemie Windows, dane wyjściowe zapisane w standardowym strumieniu wyjściowym nie będą widoczne, ponieważ nie ma konsoli do zapisywania informacji. Zapisanie informacji w konsoli niedostępnej nie powoduje wystąpienia wyjątku.  
  
 Alternatywnie, aby włączyć konsolę do odczytu i zapisu w aplikacji opartej na systemie Windows, która jest opracowywana przy użyciu programu Visual Studio, Otwórz okno dialogowe **Właściwości** projektu, kliknij kartę **aplikacja** i ustaw **Typ aplikacji** do **aplikacji konsolowej**.  
  
 Aplikacje konsolowe nie posiadają pompy komunikatów, która jest domyślnie uruchamiana. W związku z tym, wywołania konsoli do czasomierzy Win32 firmy Microsoft mogą zakończyć się niepowodzeniem.  
  
 Klasa **System. Console** ma metody, które mogą odczytywać poszczególne znaki lub wszystkie wiersze z konsoli. Inne metody konwertują dane i ciągi formatowania, a następnie zapisują sformatowane ciągi do konsoli. Aby uzyskać więcej informacji na temat formatowania ciągów, zobacz [Typy formatowania](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Console?displayProperty=nameWithType>
- [Formatowanie typów](../../docs/standard/base-types/formatting-types.md)
