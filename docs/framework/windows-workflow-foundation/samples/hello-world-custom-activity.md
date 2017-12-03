---
title: "Witaj świecie niestandardowego działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b717a5448a32eea3957e1e7e45c4dfc2f8801775
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="hello-world-custom-activity"></a>Witaj świecie niestandardowego działania
W tym przykładzie pokazano kilka kluczowych funkcji [!INCLUDE[wf](../../../../includes/wf-md.md)], łącznie ze sposobem tworzenia prostych działań niestandardowych. Niektóre funkcje zostało to pokazane w tym przykładzie tworzenia działań niestandardowych w języku C# i za pomocą `in` i `out` argumentów (<xref:System.Activities.InArgument> i <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Tworzenie przepływu pracy w kodzie  
 W tym przykładzie dwa działania niestandardowe są tworzone przy użyciu kodu C#. Zarówno działań niestandardowych dziedziczy pośrednio ani bezpośrednio po <xref:System.Activities.Activity%601> aby zwracać pojedynczą wartość. Zaletą używania ogólnego zwracanej wartości, zamiast dziedziczenia z nieogólnego <xref:System.Activities.Activity> klasa, jest to, że niektóre działania (takie jak <xref:System.Activities.Statements.Assign>) mogą uzyskiwać dostęp wartość zwracana, gdy jest używany jako część składa działania.  
  
 AppendString  
 To działanie dziedziczy <xref:System.Activities.Activity%601>i używa <xref:System.Activities.Statements.Assign> działanie, które łączy dwa ciągi ze sobą.  
  
 Dołączenie wartości ciągu  
 To działanie dziedziczy bezpośrednio <xref:System.Activities.CodeActivity%601>i tworzy podobne funkcje `AppendString` działalność, która używa logiki zaimplementowano w kodzie nie eksportami istniejące działania.  
  
 Następujące pliki znajdują się w tym projekcie.  
  
 AppendString.cs  
 Niestandardowe działanie, które dołącza ciągi ze sobą. On przyjmuje w ciągu i łączy go z ciągiem literału tekst "hello world mówi" do formularza pełny komunikat jako dane wyjściowe.  
  
 PrependString.cs  
 To działanie prefiksy wstępnie zdefiniowanych ciąg wejściowy ciąg.  
  
 Sequence1.XAML  
 Przepływ pracy, który używa `AppendString` i `PrependString` działań niestandardowych.  
  
 Plik program.CS  
 Program, który uruchamia przepływ pracy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania HelloWorld.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.