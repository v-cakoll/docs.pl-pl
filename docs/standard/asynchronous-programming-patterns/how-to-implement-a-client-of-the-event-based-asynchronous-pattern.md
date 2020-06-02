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
ms.openlocfilehash: f834ce4a0ec2208eee80ce8c3ffebfa6fdeeb5b1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289411"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach
Poniższy przykład kodu ilustruje sposób użycia składnika, który jest zgodny z [omówieniem asynchronicznego wzorca opartego na zdarzeniach](event-based-asynchronous-pattern-overview.md). Formularz do tego przykładu używa `PrimeNumberCalculator` składnika opisanego w temacie [How to: Implementuj składnik, który obsługuje wzorzec asynchroniczny oparty na zdarzeniach](component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Po uruchomieniu projektu, który używa tego przykładu, zobaczysz formularz "Kalkulator numeru początkowego" z siatką i dwoma przyciskami: **Uruchom nowe zadanie** i **Anuluj**. Możesz kliknąć przycisk **Rozpocznij nowe zadanie** kilka razy, a dla każdego kliknięcia, operacja asynchroniczna rozpocznie obliczenia, aby określić, czy losowo wygenerowany numer testu jest podstawowy. Formularz będzie okresowo wyświetlał postęp i wyniki przyrostowe. Każda operacja ma przypisany unikatowy identyfikator zadania. Wynik obliczeń jest wyświetlany w kolumnie **wynik** ; Jeśli numer testu nie jest znakiem, jest oznaczony jako **kompozytowy** i zostanie wyświetlony pierwszy dzielnik.  
  
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
