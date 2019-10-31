---
title: Czasomierze
description: Dowiedz się, jakie czasomierze .NET mają być używane w środowisku wielowątkowym.
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128952"
---
# <a name="timers"></a>Czasomierze

Platforma .NET oferuje dwa czasomierze do użycia w środowisku wielowątkowym:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, która wykonuje pojedyncze metody wywołania zwrotnego w wątku <xref:System.Threading.ThreadPool> w regularnych odstępach czasu.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, które domyślnie wywołuje zdarzenie w wątku <xref:System.Threading.ThreadPool> w regularnych odstępach czasu.

> [!NOTE]
> Niektóre implementacje platformy .NET mogą obejmować dodatkowe czasomierze:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: składnik Windows Forms, który uruchamia zdarzenie w regularnych odstępach czasu. Składnik nie ma interfejsu użytkownika i jest przeznaczony do użytku w środowisku jednowątkowym.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: składnik ASP.NET, który wykonuje asynchroniczne lub synchroniczne ogłaszanie stron sieci Web w regularnych odstępach czasu.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: czasomierz, który jest zintegrowany z kolejką <xref:System.Windows.Threading.Dispatcher>, która jest przetwarzana w określonym przedziale czasu i o określonym priorytecie.

## <a name="the-systemthreadingtimer-class"></a>Klasa System. Threading. Timer

Klasa <xref:System.Threading.Timer?displayProperty=nameWithType> umożliwia ciągłe wywoływanie delegata w określonych przedziałach czasowych. Tej klasy można również użyć do zaplanowania pojedynczego wywołania delegata w określonym przedziale czasu. Delegat jest wykonywany na wątku <xref:System.Threading.ThreadPool>.

Podczas tworzenia obiektu <xref:System.Threading.Timer?displayProperty=nameWithType> należy określić delegata <xref:System.Threading.TimerCallback>, który definiuje metodę wywołania zwrotnego, opcjonalny obiekt stanu, który jest przesyłany do wywołania zwrotnego, ilość czasu do opóźnienia przed pierwszym wywołaniem wywołania zwrotnego i przedział czasu między wywołania zwrotne. Aby anulować oczekujący czasomierz, wywołaj metodę <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType>.

Poniższy przykład tworzy czasomierz, który wywołuje dostarczony delegat po raz pierwszy po jednej sekundzie (1000 milisekund), a następnie wywołuje ją co dwie sekundy. Obiekt State w przykładzie służy do zliczania, ile razy obiekt delegowany jest wywoływany. Czasomierz jest zatrzymany, gdy delegat został wywołany co najmniej 10 razy.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Threading.Timer?displayProperty=nameWithType>.

## <a name="the-systemtimerstimer-class"></a>Klasa System. Timers. czasomierz

Innym czasomierzem, który może być używany w środowisku wielowątkowym, jest <xref:System.Timers.Timer?displayProperty=nameWithType>, że domyślnie wywołuje zdarzenie w wątku <xref:System.Threading.ThreadPool>.

Podczas tworzenia obiektu <xref:System.Timers.Timer?displayProperty=nameWithType> można określić przedział czasu, w którym ma zostać zgłoszone zdarzenie <xref:System.Timers.Timer.Elapsed>. Użyj właściwości <xref:System.Timers.Timer.Enabled%2A>, aby określić, czy czasomierz powinien zgłosić zdarzenie <xref:System.Timers.Timer.Elapsed>. Jeśli potrzebujesz zdarzenia <xref:System.Timers.Timer.Elapsed>, które ma zostać zgłoszone tylko raz po upływie określonego interwału, ustaw <xref:System.Timers.Timer.AutoReset%2A> do `false`. Wartość domyślna właściwości <xref:System.Timers.Timer.AutoReset%2A> jest `true`, co oznacza, że zdarzenie <xref:System.Timers.Timer.Elapsed> jest regularnie zgłaszane w interwale zdefiniowanym przez właściwość <xref:System.Timers.Timer.Interval%2A>.

Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Timers.Timer?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
