---
title: 'Porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: a6363bc5900c797ebd3422430f368bf2668d3364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567279"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach
Poniższy przykład kodu pokazuje sposób użycia składnika zgodną [oparty na zdarzeniach asynchroniczny wzorzec — Przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). W tym przykładzie używa `PrimeNumberCalculator` opisanych w części [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Po uruchomieniu projektu, który korzysta z tego przykładu, zobaczysz formularz "Liczba pierwsza Kalkulator" z siatki i dwa przyciski: **Rozpocznij nowe zadanie** i **anulować**. Możesz kliknąć **Rozpocznij nowe zadanie** przycisk kilka razy pod rząd, przy każdym kliknięciu operację asynchroniczną zostanie rozpoczęta i obliczeń, aby określić, czy liczba losowo wygenerowany test jest pierwsze. Formularz okresowo wyświetli się postęp i wyniki przyrostowe. Każda operacja jest przypisana zadań Unikatowy identyfikator. Wynikiem obliczenia jest wyświetlany w **wynik** kolumny; Jeśli kod testu nie jest podstawowym, jest oznaczone jako **złożonego,** i jego pierwszy dzielnik jest wyświetlany.  
  
 Oczekujących operacji mogą zostać anulowane z **anulować** przycisku. Wielokrotny będzie możliwe.  
  
> [!NOTE]
>  Większość numerów nie jest pierwsze. Jeśli nie znajdziesz liczba pierwsza po kilku ukończone operacje, wystarczy uruchomić więcej zadań, a ostatecznie można znaleźć niektórych liczb pierwszych.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
