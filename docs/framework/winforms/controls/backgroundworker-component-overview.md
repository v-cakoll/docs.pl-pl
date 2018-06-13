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
ms.openlocfilehash: 32d9bc19e9112fc9b518a68060f9f84e0e04fa16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528860"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker — Informacje o składniku
Istnieje wiele często wykonywanych operacji, które może zająć dużo czasu na wykonanie. Na przykład:  
  
-   Pobiera obraz  
  
-   Wywołania usługi sieci Web  
  
-   Plik i pobiera (w tym przypadku peer-to-peer aplikacji)  
  
-   Złożone obliczenia lokalnego  
  
-   Transakcji bazy danych  
  
-   Dostęp do dysku lokalnego, podane jego szybkość powolnego względem dostęp do pamięci  
  
 Operacje, takie jak te mogą spowodować zawieszenie uruchomieniu interfejsu użytkownika. Gdy reakcje interfejsu użytkownika i muszą stawiać czoła o długie opóźnienia skojarzone z takich operacji <xref:System.ComponentModel.BackgroundWorker> stanowi wygodną rozwiązania.  
  
 <xref:System.ComponentModel.BackgroundWorker> Składnika daje możliwość wykonania czas operacji asynchronicznie ("w tle"), na przez wątek inny niż główny wątek interfejsu użytkownika aplikacji. Aby użyć <xref:System.ComponentModel.BackgroundWorker>, po prostu go metodę czasochłonny proces roboczy do wykonania w tle, a następnie wywołać <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody. Twoje wątek wywołujący w dalszym ciągu działać normalnie podczas asynchronicznie metodę procesu roboczego. Po zakończeniu działania metody <xref:System.ComponentModel.BackgroundWorker> alerty wątek wywołujący uruchamiania <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń, która opcjonalnie zawiera wyniki operacji.  
  
 <xref:System.ComponentModel.BackgroundWorker> Składnik jest dostępny z **przybornika**w **składniki** kartę. Aby dodać <xref:System.ComponentModel.BackgroundWorker> do formularza, przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika w formularzu. Wygląda na to, na pasku składnika i jego właściwości są wyświetlane w **właściwości** okna.  
  
 Aby uruchomić operację asynchroniczną, użyj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> przyjmuje opcjonalny `object` parametr, który może służyć do argument jest przekazywany do metody pracownika. <xref:System.ComponentModel.BackgroundWorker> Klasy ujawnia <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń, do której z wątku roboczego jest dołączona do <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń.  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> Przyjmuje obsługi zdarzeń <xref:System.ComponentModel.DoWorkEventArgs> parametr, który ma <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwości. Ta właściwość odbiera parametru z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i mogą zostać przekazane do metody pracownika, która będzie wywoływana w <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń. Poniższy przykład przedstawia sposób Przypisz wynik z metody procesu roboczego o nazwie `ComputeFibonacci`. Nie jest częścią większego przykładu można znaleźć w [porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Aby uzyskać więcej informacji na temat używania programów obsługi zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).  
  
> [!CAUTION]
>  Korzystając z wielowątkowość jakiegokolwiek, możesz narażając samodzielnie do usterki bardzo poważne i złożone. Zapoznaj się [zarządzanych wątków najlepsze rozwiązania w zakresie](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem rozwiązania, w którym używane wielowątkowości.  
  
 Aby uzyskać więcej informacji na temat używania <xref:System.ComponentModel.BackgroundWorker> , zobacz [porady: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Zobacz też  
 [NIE w kompilacji: Wielowątkowość w języku Visual Basic](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
