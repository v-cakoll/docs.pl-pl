---
title: BackgroundWorker — Informacje o składniku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046109"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker — Informacje o składniku
Istnieje wiele często wykonywanych operacji, których wykonanie może zająć dużo czasu. Na przykład:  
  
- Pobieranie obrazów  
  
- Wywołania usługi sieci Web  
  
- Pobieranie i przekazywanie plików (w tym aplikacji równorzędnych)  
  
- Złożone obliczenia lokalne  
  
- Transakcje bazy danych  
  
- Dostęp do dysku lokalnego z uwzględnieniem wolnej szybkości względem dostępu do pamięci  
  
 Operacje takie jak te mogą spowodować, że interfejs użytkownika będzie zablokowany, gdy są uruchomione. Jeśli potrzebujesz interfejsu użytkownika, który ma duże opóźnienia związane z takimi operacjami, <xref:System.ComponentModel.BackgroundWorker> składnik oferuje wygodne rozwiązanie.  
  
 <xref:System.ComponentModel.BackgroundWorker> Składnik daje możliwość asynchronicznego wykonywania czasochłonnych operacji ("w tle") na wątku innym niż główny wątek interfejsu użytkownika aplikacji. Aby korzystać z <xref:System.ComponentModel.BackgroundWorker>programu, wystarczy wskazać, jakie czasochłonne metody procesu roboczego w tle, a następnie <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> wywołać metodę. Wątek wywołujący nadal działa normalnie, gdy metoda proces roboczy jest uruchamiana asynchronicznie. Gdy metoda zostanie zakończona, <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> wyzwala wywołujący wątek przez wygenerowanie zdarzenia, które opcjonalnie zawiera wyniki operacji.  
  
 Składnik jest dostępny z przybornika na karcie **składniki** . <xref:System.ComponentModel.BackgroundWorker> Aby dodać <xref:System.ComponentModel.BackgroundWorker> do formularza, <xref:System.ComponentModel.BackgroundWorker> przeciągnij składnik na formularz. Pojawia się on na pasku składnika, a jego właściwości są wyświetlane w oknie **Właściwości** .  
  
 Aby rozpocząć operację asynchroniczną, użyj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>przyjmuje opcjonalny `object` parametr, który może służyć do przekazywania argumentów do metody Worker. Klasa ujawnia zdarzenie, do którego <xref:System.ComponentModel.BackgroundWorker.DoWork> wątek roboczy jest dołączany przez procedurę obsługi zdarzeń. <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker>  
  
 Program obsługi <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń <xref:System.ComponentModel.DoWorkEventArgs> przyjmuje<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> parametr, który ma właściwość. Ta właściwość odbiera parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i może zostać przesłany do metody procesu roboczego, która zostanie wywołana <xref:System.ComponentModel.BackgroundWorker.DoWork> w programie obsługi zdarzeń. Poniższy przykład pokazuje, jak przypisać wynik z metody procesu roboczego o nazwie `ComputeFibonacci`. Jest to część większego przykładu, którą można znaleźć w [następujących tematach: Implementowanie formularza korzystającego z operacji](how-to-implement-a-form-that-uses-a-background-operation.md)w tle.  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Aby uzyskać więcej informacji na temat obsługi zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).  
  
> [!CAUTION]
> W przypadku korzystania z wielowątkowości dowolnego sortowania użytkownik może ujawnić sobie bardzo poważne i złożone usterki. Przed zaimplementowaniem dowolnego rozwiązania, które używa wielowątkowości, należy zapoznać się z [zarządzanymi wątkami](../../../standard/threading/managed-threading-best-practices.md) .  
  
 Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker> używania klasy, [zobacz How to: Uruchom operację w tle](how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzane wątki](../../../standard/threading/index.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Instrukcje: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
