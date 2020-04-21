---
title: Czasomierze
description: Dowiedz się, co .NET czasomierze do użycia w środowisku wielowątkowym.
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
ms.openlocfilehash: d463eb2a8d598dc5ba9b2fb51a6fc08c563e6fe4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739488"
---
# <a name="timers"></a>Czasomierze

.NET udostępnia dwa czasomierze do użycia w środowisku wielowątkowym:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, który wykonuje metodę pojedynczego <xref:System.Threading.ThreadPool> wywołania zwrotnego w wątku w regularnych odstępach czasu.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, który domyślnie wywołuje zdarzenie <xref:System.Threading.ThreadPool> w wątku w regularnych odstępach czasu.

> [!NOTE]
> Niektóre implementacje platformy .NET mogą zawierać dodatkowe czasomierze:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: składnik Windows Forms, który uruchamia zdarzenie w regularnych odstępach czasu. Składnik nie ma interfejsu użytkownika i jest przeznaczony do użytku w środowisku jednowątkowym.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: składnik ASP.NET, który wykonuje asynchroniczne lub synchroniczne postbacks strony sieci Web w regularnych odstępach czasu.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: czasomierz, który <xref:System.Windows.Threading.Dispatcher> jest zintegrowany z kolejką, która jest przetwarzana w określonym przedziale czasu i w określonym priorytecie.

## <a name="the-systemthreadingtimer-class"></a>Klasa System.Threading.Timer

Klasa <xref:System.Threading.Timer?displayProperty=nameWithType> umożliwia ciągłe wywoływanie delegata w określonych odstępach czasu. Tej klasy można również użyć do zaplanowania pojedynczego wywołania do pełnomocnika w określonym przedziale czasu. Pełnomocnik jest wykonywany <xref:System.Threading.ThreadPool> w wątku.

Podczas tworzenia <xref:System.Threading.Timer?displayProperty=nameWithType> obiektu, należy <xref:System.Threading.TimerCallback> określić pełnomocnika, który definiuje metodę wywołania zwrotnego, opcjonalny obiekt stanu, który jest przekazywany do wywołania zwrotnego, czas opóźnienia przed pierwszym wywołaniem wywołania zwrotnego i przedział czasu między wywołaniami zwrotnymi. Aby anulować oczekujący czasomierz, należy wywołać <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> metodę.

Poniższy przykład tworzy czasomierz, który wywołuje podane delegata po raz pierwszy po jednej sekundzie (1000 milisekund), a następnie wywołuje go co dwie sekundy. Obiekt stanu w przykładzie jest używany do zliczania, ile razy delegat jest wywoływany. Czasomierz jest zatrzymany, gdy pełnomocnik został wywołany co najmniej 10 razy.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Aby uzyskać więcej informacji <xref:System.Threading.Timer?displayProperty=nameWithType>i przykładów, zobacz .

## <a name="the-systemtimerstimer-class"></a>Klasa System.Timers.Timer

Innym czasomierzem, który może być używany <xref:System.Timers.Timer?displayProperty=nameWithType> w środowisku wielowątkowym jest to, że domyślnie wywołuje zdarzenie w wątku. <xref:System.Threading.ThreadPool>

Podczas tworzenia <xref:System.Timers.Timer?displayProperty=nameWithType> obiektu można określić przedział czasu, w <xref:System.Timers.Timer.Elapsed> którym ma zostać utworzone zdarzenie. Użyj <xref:System.Timers.Timer.Enabled%2A> właściwości, aby wskazać, czy <xref:System.Timers.Timer.Elapsed> czasomierz powinien podnieść zdarzenie. Jeśli chcesz, <xref:System.Timers.Timer.Elapsed> aby zdarzenie zostało podniesione tylko raz po upływie <xref:System.Timers.Timer.AutoReset%2A> określonego `false`interwału, ustaw na . Domyślną wartością <xref:System.Timers.Timer.AutoReset%2A> właściwości `true`jest , <xref:System.Timers.Timer.Elapsed> co oznacza, że zdarzenie jest <xref:System.Timers.Timer.Interval%2A> wywoływane regularnie w przedziale zdefiniowanym przez właściwość.

Aby uzyskać więcej informacji <xref:System.Timers.Timer?displayProperty=nameWithType>i przykładów, zobacz .
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [Wątki obiektów i operacji](threading-objects-and-features.md)
