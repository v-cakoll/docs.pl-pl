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
ms.openlocfilehash: 4176d1a4cec91c5740b03c10d1a6d2cc263dba28
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45998815"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach
Poniższy przykład kodu demonstruje sposób używania składnika zgodnego [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). W tym przykładzie używa `PrimeNumberCalculator` opisane w części [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Kiedy uruchamiasz projekt, który korzysta z tego przykładu, zostanie wyświetlony formularz "Liczba pierwsza Kalkulator" przy użyciu siatki oraz dwa przyciski: **uruchomienia nowego zadania** i **anulować**. Możesz kliknąć pozycję **uruchomienia nowego zadania** przycisk kilka razy z rzędu, przy każdym kliknięciu operację asynchroniczną zostanie rozpoczęta i obliczeń, aby ustalić, czy liczba testów losowo generowany jest pierwsze. Formularz wyświetli okresowo postęp i wyniki przyrostowe. Każda operacja jest przypisany identyfikator unikatowy zadania. Wynik obliczenia jest wyświetlany w **wynik** kolumny; Jeśli liczba testów nie jest podstawowym, jest oznaczona jako **złożonego,** i pojawi się jego pierwszym dzielnik.  
  
 Żadnych oczekujących operacji może być anulowany, za pomocą **anulować** przycisku. Wielokrotny będzie możliwe.  
  
> [!NOTE]
>  Większość numerów nie będzie Północnej. Jeśli nie znajdziesz liczba pierwsza po kilka operacji zakończonych, po prostu uruchom większej liczby zadań, a ostatecznie znajdziesz niektóre liczby pierwsze.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.AsyncOperation>  
- <xref:System.ComponentModel.AsyncOperationManager>  
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
