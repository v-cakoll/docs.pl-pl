---
title: 'Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach'
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
ms.openlocfilehash: 8d2825ff738ffc50ba9a438024db27aff5686a0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870347"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach
Poniższy przykład kodu demonstruje sposób używania składnika zgodnego [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). W tym przykładzie używa `PrimeNumberCalculator` opisane w części [jak: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Kiedy uruchamiasz projekt, który korzysta z tego przykładu, zostanie wyświetlony formularz "Liczba pierwsza Kalkulator" z siatki oraz dwa przyciski: **Uruchom nowe zadanie** i **anulować**. Możesz kliknąć pozycję **uruchomienia nowego zadania** przycisk kilka razy z rzędu, przy każdym kliknięciu operację asynchroniczną zostanie rozpoczęta i obliczeń, aby ustalić, czy liczba testów losowo generowany jest pierwsze. Formularz wyświetli okresowo postęp i wyniki przyrostowe. Każda operacja jest przypisany identyfikator unikatowy zadania. Wynik obliczenia jest wyświetlany w **wynik** kolumny; Jeśli liczba testów nie jest podstawowym, jest oznaczona jako **złożonego,** i pojawi się jego pierwszym dzielnik.  
  
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
