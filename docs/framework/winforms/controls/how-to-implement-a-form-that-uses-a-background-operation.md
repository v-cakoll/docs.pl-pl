---
title: "Porady: implementowanie formularza korzystającego z operacji w tle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2172611fc92257490cfe4ed0b020270aefb3638
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Porady: implementowanie formularza korzystającego z operacji w tle
Następujący przykład program tworzy formularz, który oblicza Fibonacci cyfry. Obliczenie jest uruchamiane w wątku, który jest oddzielony od wątku interfejsu użytkownika, więc interfejsu użytkownika w dalszym ciągu działać bez opóźnień w trakcie wykonywania obliczeń.  
  
 Brak kompleksową obsługę tego zadania w programie Visual Studio.  
  
 Zobacz też [wskazówki: Wdrażanie formularza korzystającego z operacji w tle](http://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
> [!CAUTION]
>  Korzystając z wielowątkowość jakiegokolwiek, możesz narażając samodzielnie do usterki bardzo poważne i złożone. Zapoznaj się [zarządzanych wątków najlepsze rozwiązania w zakresie](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem rozwiązania, w którym używane wielowątkowości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../../docs/standard/threading/managed-threading-best-practices.md)
