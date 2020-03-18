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
ms.openlocfilehash: 50aa36d2caf774638ad20323813f0de3703aab2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "69950717"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach
W poniższym przykładzie kodu pokazano, jak używać składnika, który jest zgodny z [omówieniem asynchronicznego wzorca opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). Formularz w tym przykładzie `PrimeNumberCalculator` używa składnika opisanego w [jak: Implementowanie składnika, który obsługuje asynchroniczny wzorzec oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Po uruchomieniu projektu, który używa tego przykładu, zostanie wyświetlony formularz "Kalkulator liczb pierwszych" z siatką i dwoma przyciskami: **Rozpocznij nowe zadanie** i **Anuluj**. Można kliknąć przycisk **Rozpocznij nowe zadanie** kilka razy z rzędu, a dla każdego kliknięcia operacja asynchroniczna rozpocznie obliczenia, aby ustalić, czy losowo wygenerowany numer testu jest pierwszorzędny. Formularz będzie okresowo wyświetlał postęp i wyniki przyrostowe. Każdej operacji przypisywany jest unikatowy identyfikator zadania. Wynik obliczeń jest wyświetlany w **kolumnie Wynik;** jeśli numer testowy nie jest pierwszy, jest oznaczony jako **Composite,** a jego pierwszy dzielnik jest wyświetlany.  
  
 Każdą oczekującą operację można anulować za pomocą przycisku **Anuluj.** Można dokonywać wielu selekcji.  
  
> [!NOTE]
> Większość liczb nie będzie pierwszorzędna. Jeśli po kilku zakończonych operacjach nie znaleziono liczby pierwszej, po prostu uruchom więcej zadań, a ostatecznie znajdziesz kilka liczb pierwszych.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
