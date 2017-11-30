---
title: "Wątku puli (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b89d261aa2d038926f8c7e1832436b0cd34019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-visual-basic"></a>Wątku puli (Visual Basic)
A *puli wątków* jest kolekcją wątków, które można wykonać kilka zadań w tle. (Zobacz [wątki (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) informacje uzupełniające.) Spowoduje to pozostawienie podstawowy wątek wolnego asynchronicznie wykonywanie innych zadań.  
  
 Pule wątków są często stosowanych w aplikacji serwera. Każde żądanie przychodzące jest przypisany do wątku z puli wątków, aby żądania były przetwarzane asynchronicznie, bez zajmowania podstawowy wątku lub opóźnienia przetwarzanie kolejnych żądań.  
  
 Po zakończeniu działania zadań jego wątków w puli jest zwracany do kolejki wątków oczekujących, gdzie mogą być ponownie. Ponownemu ten umożliwia aplikacjom uniknąć kosztów tworzenia nowego wątku dla każdego zadania.  
  
 Pule wątków zwykle mają maksymalną liczbę wątków. Jeśli wszystkie wątki są zajęte, dopóki nie może być obsługiwany jako wątków staną się dostępne dodatkowe zadania są umieszczane w kolejce.  
  
 Można zaimplementować pulę wątków, ale jest łatwiejsze w puli wątków dostarczane przez program .NET Framework za pomocą <xref:System.Threading.ThreadPool> klasy.  
  
 Z puli wątków, należy wywołać <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> metody z delegata w procedurze, który chcesz uruchomić i Visual Basic tworzy wątku i uruchamia procedury.  
  
## <a name="thread-pooling-example"></a>Przykład Pula wątków  
 Poniższy przykład przedstawia sposób korzystania z wątku puli można uruchomić kilka zadań.  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 Jedną z zalet korzystanie z puli wątków jest, że można przekazywać argumenty w obiekcie stanu do procedury zadań. Jeśli procedury to wywołanie wymaga więcej niż jeden argument, można rzutować strukturą lub wystąpienia klasy do `Object` — typ danych.  
  
## <a name="thread-pool-parameters-and-return-values"></a>Wątek puli parametrów i zwracanych wartości  
 Zwracanie wartości z wątku puli wątków nie jest proste. Standardowy sposób zwracania wartości z wywołania funkcji jest niedozwolona, ponieważ `Sub` procedury są jedynym typem procedury, które mogą być umieszczone w kolejce do puli wątków. Jednym ze sposobów można podać parametry i zwracać wartości jest zawijania parametrów zwracanych wartości i metody w otoce klasy zgodnie z opisem w [parametry i zwracać wartości dla procedur wielowątkowości (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 Sposób easer Podaj parametry i wartości zwracane jest przy użyciu opcjonalnego `ByVal` zmiennej obiektu stanu z <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody. Jeśli używasz tej zmiennej do przekazania odwołania do wystąpienia klasy elementów członkowskich wystąpienia można modyfikować w wątku puli wątków i używane jako wartości zwracanych.  
  
 Na początku może nie być oczywista, modyfikowania obiektu odwołuje się do zmiennej, która jest przekazywany przez wartość. Można to zrobić, ponieważ tylko odwołanie do obiektu jest przekazywany przez wartość. Po wprowadzeniu zmian do elementów członkowskich obiektu odwołuje się odwołanie do obiektu zmiany dotyczą wystąpienie klasy rzeczywistych.  
  
 Struktury nie można zwrócić wartości wewnątrz obiekty stanu. Ponieważ struktury są typy wartości, zmiany, które powoduje, że proces asynchroniczny nie należy zmieniać członkami oryginalnej struktury. Użyj struktury, aby podać parametry zwracane wartości nie są potrzebne.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Porady: Korzystanie z puli wątków (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [Wątkowość (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [Aplikacje wielowątkowe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Synchronizacja wątku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
