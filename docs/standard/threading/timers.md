---
title: Czasomierze
description: Dowiedz się, jakie czasomierzy .NET do użycia w środowisku wielowątkowym.
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
ms.author: ronpet
ms.openlocfilehash: 644ccf5951e9d2556fc697d2fd763f026fd0ebdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617229"
---
# <a name="timers"></a>Czasomierze

.NET oferuje dwa typy czasomierzy do użycia w środowisku wielowątkowym:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, który wykonuje metodę pojedynczego wywołania zwrotnego w <xref:System.Threading.ThreadPool> wątku w regularnych odstępach czasu.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, która domyślnie wywołuje zdarzenie, na <xref:System.Threading.ThreadPool> wątku w regularnych odstępach czasu.

> [!NOTE]
> Niektóre implementacje platformy .NET mogą obejmować czasomierzy dodatkowe:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: składnik Windows Forms, który uruchamia zdarzenie w regularnych odstępach czasu. Składnik nie ma interfejsu użytkownika i jest przeznaczony do użytku w środowisku apartamentem.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: składnik ASP.NET, który wykonuje ogłaszania zwrotnego asynchronicznego lub synchronicznego strony sieci web w regularnych odstępach czasu.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: czasomierz, który jest zintegrowany z <xref:System.Windows.Threading.Dispatcher> kolejki, która jest przetwarzana z określonym interwałem czasu i z priorytetem.

## <a name="the-systemthreadingtimer-class"></a>Klasa System.Threading.Timer

<xref:System.Threading.Timer?displayProperty=nameWithType> Klasy umożliwia ciągłe wywołanie delegata w określonych odstępach czasu. Możesz również użyć tej klasy można zaplanować wywołanie delegata w określonym przedziale czasu. Delegat jest wykonywane na <xref:System.Threading.ThreadPool> wątku.

Po utworzeniu <xref:System.Threading.Timer?displayProperty=nameWithType> obiektu, należy określić <xref:System.Threading.TimerCallback> delegata, który definiuje metody wywołania zwrotnego, obiekt opcjonalne stanu, który jest przekazywany do wywołania zwrotnego, ilość czasu, opóźnienie przed pierwszym wywołaniem wywołania zwrotnego i przedział czasu między wywołania zwrotnego. Aby anulować oczekujące czasomierza, należy wywołać <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> metody.

Poniższy przykład tworzy czasomierz, który wywołuje delegata podane po raz pierwszy po sekundzie (1000 milisekund), a następnie wywołuje on co 2 sekundy. Obiekt stanu, w przykładzie jest używany policzyć ile razy nosi nazwę delegata. Czasomierz został zatrzymany, gdy delegat została wywołana co najmniej 10 razy.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Threading.Timer?displayProperty=nameWithType>.

## <a name="the-systemtimerstimer-class"></a>Klasa System.Timers.Timer

Jest inny czasomierz, które mogą być używane w środowisku wielowątkowym <xref:System.Timers.Timer?displayProperty=nameWithType> która domyślnie wywołuje zdarzenie, na <xref:System.Threading.ThreadPool> wątku.

Po utworzeniu <xref:System.Timers.Timer?displayProperty=nameWithType> obiektu, można określić interwał czasu, w którego zostanie wywołane <xref:System.Timers.Timer.Elapsed> zdarzeń. Użyj <xref:System.Timers.Timer.Enabled%2A> właściwości, aby wskazać, jeśli czasomierz, powinny wywoływać <xref:System.Timers.Timer.Elapsed> zdarzeń. Jeśli potrzebujesz <xref:System.Timers.Timer.Elapsed> zdarzenia tylko jeden raz po upływie określonego interwału, ustaw <xref:System.Timers.Timer.AutoReset%2A> do `false`. Wartość domyślna <xref:System.Timers.Timer.AutoReset%2A> właściwość `true`, co oznacza, że <xref:System.Timers.Timer.Elapsed> zdarzenie jest zgłaszane w regularnie w odstępach czasu zdefiniowanych przez <xref:System.Timers.Timer.Interval%2A> właściwości.

Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Timers.Timer?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
