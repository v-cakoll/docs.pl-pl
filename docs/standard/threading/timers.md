---
title: Czasomierze
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 478484651bf839f842148f0b4164c9387db3b98a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584960"
---
# <a name="timers"></a>Czasomierze
Czasomierze są lekkie obiekty, które umożliwiają określenie delegata do wywołania w określonym czasie. Wątek w puli wątków wykonuje operację oczekiwania.  
  
 Przy użyciu <xref:System.Threading.Timer?displayProperty=nameWithType> klasy jest prosta. Możesz utworzyć **czasomierza**, przechodzącą <xref:System.Threading.TimerCallback> delegowany do metody wywołania zwrotnego, obiekt reprezentujący stan, który zostanie przekazany do wywołania zwrotnego, zgłoś początkowej czas i czas reprezentujący w okresie między wywołania zwrotnego. Aby anulować oczekujące czasomierza, należy wywołać **Timer.Dispose** funkcji.  
  
> [!NOTE]
>  Istnieją dwa inne klasy czasomierza. <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Klasy jest formant, który działa za pomocą wizualnych projektantów i ma być używany w kontekstach interfejsu użytkownika; zgłasza zdarzenia w wątku interfejsu użytkownika. <xref:System.Timers.Timer?displayProperty=nameWithType> Pochodną klasy <xref:System.ComponentModel.Component>, dlatego może służyć za pomocą wizualnych projektantów; zgłasza zdarzeń, ale uruchamia je na <xref:System.Threading.ThreadPool> wątku. <xref:System.Threading.Timer?displayProperty=nameWithType> Klasy nawiązuje wywołania zwrotne <xref:System.Threading.ThreadPool> wątku i nie używa modelu zdarzeń w ogóle. Umożliwia także obiekt stanu do metody wywołania zwrotnego, które nie zawierają innych czasomierzy. Jest bardzo uproszczonego.  
  
 Poniższy przykładowy kod uruchamia czasomierz, która rozpoczyna się po jednej sekundy (1000 milisekund) i znaczniki co sekundę, dopóki nie zostanie naciśnięty klawisz **Enter** klucza. Zmienna zawierające odwołania do czasomierz jest polem poziomie klasy, aby upewnić się, że Czasomierz nie podlega wyrzucanie elementów bezużytecznych podczas nadal działa. Aby uzyskać więcej informacji na agresywne wyrzucanie elementów bezużytecznych, zobacz <xref:System.GC.KeepAlive%2A>.  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Timer>  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
