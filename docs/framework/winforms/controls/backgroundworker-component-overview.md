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
ms.openlocfilehash: d7d99cf87507237b23cb40c58b2308643f7f1056
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138490"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker — Informacje o składniku
Istnieje wiele często wykonywanych operacji, które może zająć dużo czasu wykonania. Na przykład:  
  
-   Pobiera obraz  
  
-   Wywołania usługi sieci Web  
  
-   Plik przekazuje i pobiera (w tym aplikacji peer-to-peer)  
  
-   Złożone obliczenia lokalne  
  
-   Transakcje bazy danych  
  
-   Dysk lokalny dostęp, biorąc pod uwagę jej szybkość powolnego względem dostępu do pamięci  
  
 Operacje, takie jak te może spowodować zawieszenie, gdy są one uruchomione interfejsu użytkownika. Gdy chcesz dynamicznym interfejsem użytkownika i napotykają duże opóźnienia skojarzonych z takich operacji <xref:System.ComponentModel.BackgroundWorker> składnik udostępnia wygodne rozwiązanie.  
  
 <xref:System.ComponentModel.BackgroundWorker> Składnika daje możliwość wykonywania czasochłonne operacje asynchronicznie ("w tle") w wątku, który różni się od głównego wątku interfejsu użytkownika aplikacji. Aby użyć <xref:System.ComponentModel.BackgroundWorker>, wystarczy podać jej metody czasochłonnych procesów roboczych do wykonania w tle, a następnie możesz wywołać <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody. Wątek wywołujący w dalszym ciągu działać normalnie, podczas gdy metodzie wątku roboczego jest uruchamiane asynchronicznie. Po zakończeniu działania metody <xref:System.ComponentModel.BackgroundWorker> alerty wątku wywołującego uruchomieniu którego <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenie, które opcjonalnie zawiera wyniki operacji.  
  
 <xref:System.ComponentModel.BackgroundWorker> Składnik jest dostępny z **przybornika**w **składniki** kartę. Aby dodać <xref:System.ComponentModel.BackgroundWorker> do formularza, przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika do formularza. Wygląda na to, w zasobniku składnika, a jego właściwości są wyświetlane w **właściwości** okna.  
  
 Aby rozpocząć operację asynchroniczną, użyj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> przyjmuje opcjonalny `object` parametr, który może służyć do przekazywania argumentów do metody procesu roboczego. <xref:System.ComponentModel.BackgroundWorker> Klasy ujawnia <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń, do której dołączono wątek procesu roboczego za pomocą <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> Programu obsługi zdarzeń przyjmuje <xref:System.ComponentModel.DoWorkEventArgs> parametr, który ma <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwości. Ta właściwość odbiera parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i może być przekazywany do metody proces roboczy zostanie wywołana w <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń. Poniższy przykład pokazuje, jak przypisać wyniku z metody procesu roboczego o nazwie `ComputeFibonacci`. Jest on częścią większego przykładu można znaleźć w [porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Aby uzyskać więcej informacji na temat korzystania z programów obsługi zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).  
  
> [!CAUTION]
>  Korzystając z wielowątkowością jakiegokolwiek rodzaju, możesz potencjalnie się narazić na bardzo poważne i złożone usterek. Zapoznaj się z [zarządzana wątkowość najlepsze](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem dowolne rozwiązanie, który używa wielowątkowości.  
  
 Aby uzyskać więcej informacji na temat korzystania z <xref:System.ComponentModel.BackgroundWorker> klasy, zobacz [porady: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość](../../../../docs/standard/threading/index.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Instrukcje: implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
