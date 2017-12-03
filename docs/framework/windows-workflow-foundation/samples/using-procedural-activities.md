---
title: "Przy użyciu procedur działań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d0aeafeaf78e25f612ededf2f6a15061ec280a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-procedural-activities"></a>Przy użyciu procedur działań
W przykładzie użyto <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, i <xref:System.Activities.Statements.WriteLine> działań do wykonania odgadnięcie gier. Gry guessing wybiera liczbę losową i odtwarzacz ma odgadnąć ten numer. Gdy odtwarzacz wyśle nieprawidłowy wynik, przepływ pracy podpowiada czy odgadnąć wyższy lub niższy. Jeśli odtwarzacz liczba prób numer w mniej niż 7 prób, Gratulujemy specjalne jest wyświetlana użytkownikowi.  
  
## <a name="custom-activities-in-this-sample"></a>Niestandardowe działania w tym przykładzie  
  
### <a name="readline"></a>ReadLine  
 Odczytuje wiersz tekstu z konsoli. To działanie jest pochodną <xref:System.Activities.NativeActivity> klasy i tworzy zakładki, która zostanie wznowione przez aplikację konsoli, jeśli wiersz jest do odczytu.  
  
### <a name="promptint"></a>PromptInt  
 Monituje użytkownika o wpisz numer i odczytuje go z okna konsoli. Działanie jest pochodną <xref:System.Activities.Activity%601> i używa <xref:System.Activities.Statements.WriteLine> i `ReadLine` działań.  
  
##### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania GuessingGame.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`