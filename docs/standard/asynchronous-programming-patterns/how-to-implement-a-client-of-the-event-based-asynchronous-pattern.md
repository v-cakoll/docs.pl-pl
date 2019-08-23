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
ms.openlocfilehash: 50aa36d2caf774638ad20323813f0de3703aab2f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950717"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach
Poniższy przykład kodu ilustruje sposób użycia składnika, który jest zgodny z [omówieniem asynchronicznego wzorca opartego](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)na zdarzeniach. W formularzu dla tego przykładu zostanie `PrimeNumberCalculator` użyty składnik opisany [w temacie How to: Implementacja składnika obsługującego wzorzec](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)asynchroniczny oparty na zdarzeniach.  
  
 Gdy uruchamiasz projekt, który używa tego przykładu, zobaczysz formularz "Kalkulator numeru głównego" z siatką i dwoma przyciskami: **Rozpocznij nowe zadanie** i **Anuluj operację**. Możesz kliknąć przycisk **Rozpocznij nowe zadanie** kilka razy, a dla każdego kliknięcia, operacja asynchroniczna rozpocznie obliczenia, aby określić, czy losowo wygenerowany numer testu jest podstawowy. Formularz będzie okresowo wyświetlał postęp i wyniki przyrostowe. Każda operacja ma przypisany unikatowy identyfikator zadania. Wynik obliczeń jest wyświetlany w kolumnie **wynik** ; Jeśli numer testu nie jest znakiem, jest oznaczony jako kompozytowy i zostanie wyświetlony pierwszy dzielnik.  
  
 Wszystkie oczekujące operacje można anulować przy użyciu przycisku **Anuluj** . Można wprowadzić wiele zaznaczeń.  
  
> [!NOTE]
> Większość cyfr nie będzie podstawowa. Jeśli nie odnaleziono numeru początkowego po kilku ukończonych operacjach, wystarczy uruchomić więcej zadań i ostatecznie znaleźć liczby podstawowe.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
