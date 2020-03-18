---
title: Czasomierze
description: Dowiedz się, co czasomierzy .NET do użycia w środowisku wielowątkowym.
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.openlocfilehash: d7d1fa13b02fe7425fa9b4cb81ba20297a23fe4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128952"
---
# <a name="timers"></a>Czasomierze

.NET udostępnia dwa timery do użycia w środowisku wielowątkowym:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, który wykonuje jedną metodę wywołania odwróconego w wątku <xref:System.Threading.ThreadPool> w regularnych odstępach czasu.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, który domyślnie wywołuje <xref:System.Threading.ThreadPool> zdarzenie w wątku w regularnych odstępach czasu.

> [!NOTE]
> Niektóre implementacje .NET mogą zawierać dodatkowe czasomierzy:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: składnik Formularzy systemu Windows, który uruchamia zdarzenie w regularnych odstępach czasu. Składnik nie ma interfejsu użytkownika i jest przeznaczony do użytku w środowisku jednowątkowym.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: składnik ASP.NET, który regularnie wykonuje asynchroniczne lub synchroniczne ogłaszania stron internetowych.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: czasoatarka zintegrowana <xref:System.Windows.Threading.Dispatcher> z kolejką, która jest przetwarzana w określonym przedziale czasu i przy określonym priorytecie.

## <a name="the-systemthreadingtimer-class"></a>Klasa System.Threading.Timer

Klasa <xref:System.Threading.Timer?displayProperty=nameWithType> umożliwia ciągłe wywoływanie delegata w określonych odstępach czasu. Ta klasa służy również do planowania pojedynczego wywołania pełnomocnika w określonym przedziale czasu. Delegat jest wykonywany <xref:System.Threading.ThreadPool> w wątku.

Podczas tworzenia <xref:System.Threading.Timer?displayProperty=nameWithType> obiektu należy określić <xref:System.Threading.TimerCallback> pełnomocnika, który definiuje metodę wywołania wywołania, opcjonalny obiekt stanu, który jest przekazywany do wywołania wywołania, czas opóźnienia przed pierwszym wywołaniem wywołania wywołania wywołania wywołania i przedział czasu między wywołaniami wywołania. Aby anulować czasoator <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> oczekujący, wywołaj metodę.

Poniższy przykład tworzy czasodwac, który wywołuje podanych delegata po raz pierwszy po jednej sekundzie (1000 milisekund), a następnie wywołuje go co dwie sekundy. Obiekt stanu w przykładzie służy do zliczania, ile razy pełnomocnik jest wywoływany. Czasowat jest zatrzymywany, gdy pełnomocnik został wywołany co najmniej 10 razy.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Aby uzyskać więcej informacji <xref:System.Threading.Timer?displayProperty=nameWithType>i przykładów, zobacz .

## <a name="the-systemtimerstimer-class"></a>Klasa System.Timers.Timer

Innym czasoatorem, który może być <xref:System.Timers.Timer?displayProperty=nameWithType> używany w środowisku wielowątkowym jest to, że domyślnie wywołuje zdarzenie w wątku. <xref:System.Threading.ThreadPool>

Podczas tworzenia <xref:System.Timers.Timer?displayProperty=nameWithType> obiektu można określić przedział czasu, w <xref:System.Timers.Timer.Elapsed> którym ma zostać wywołane zdarzenie. Użyj <xref:System.Timers.Timer.Enabled%2A> właściwości, aby wskazać, czy <xref:System.Timers.Timer.Elapsed> czasowcy powinny wywołać zdarzenie. Jeśli konieczne <xref:System.Timers.Timer.Elapsed> jest, aby zdarzenie zostało podniesione tylko raz po upływie <xref:System.Timers.Timer.AutoReset%2A> `false`określonego interwału, ustaw wartość . Domyślną wartością <xref:System.Timers.Timer.AutoReset%2A> właściwości `true`jest , <xref:System.Timers.Timer.Elapsed> co oznacza, że zdarzenie jest wywoływane regularnie w interwale zdefiniowanym <xref:System.Timers.Timer.Interval%2A> przez właściwość.

Aby uzyskać więcej informacji <xref:System.Timers.Timer?displayProperty=nameWithType>i przykładów, zobacz .
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [Wątkowe obiekty i operacje](threading-objects-and-features.md)
