---
title: Niestandardowe działanie Hello World
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: fde745fae7470ec763b6b5030a60436a6525e3c0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856855"
---
# <a name="hello-world-custom-activity"></a>Niestandardowe działanie Hello World
Niniejszy przykład pokazuje kilka kluczowych funkcji programu Windows Workflow Foundation (WF), w tym jak utworzyć proste działań niestandardowych. Niektóre funkcje przedstawione w tym przykładzie tworzenia działań niestandardowych w języku C# i za pomocą `in` i `out` argumentów (<xref:System.Activities.InArgument> i <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Tworzenie przepływu pracy w kodzie  
 W tym przykładzie są tworzone dwa działania niestandardowe, przy użyciu kodu C#. Zarówno działań niestandardowych dziedziczyć bezpośrednio lub pośrednio <xref:System.Activities.Activity%601> zwracać pojedynczą wartość. Zaletą używania ogólnego zwracanej wartości, a nie dziedziczy z inną niż ogólna <xref:System.Activities.Activity> klasy, jest to, że niektóre działania (takie jak <xref:System.Activities.Statements.Assign>) mogą uzyskać dostępu wartość zwracana, gdy jest używana jako część złożone działania.  
  
 AppendString  
 To działanie dziedziczy <xref:System.Activities.Activity%601>i wykorzystuje <xref:System.Activities.Statements.Assign> działanie, które łączy ze sobą dwa ciągi.  
  
 Dołącz ciąg  
 To działanie dziedziczy bezpośrednio z <xref:System.Activities.CodeActivity%601>i tworzy funkcje podobne do `AppendString` działania, które używa logiki zaimplementowane w kod, a nie jest złożony z istniejących działań.  
  
 Następujące pliki znajdują się w tym projekcie.  
  
 AppendString.cs  
 Niestandardowe działanie, które dołącza ciągi ze sobą. On przyjmuje ciąg i łączy ją z ciągiem literału tekstowego "— mówi hello world" do formularza komunikat o ukończeniu jako dane wyjściowe.  
  
 PrependString.cs  
 To działanie prefiksy wstępnie zdefiniowane parametry do ciągu wejściowego.  
  
 Sequence1.XAML  
 Przepływ pracy, który używa `AppendString` i `PrependString` działań niestandardowych.  
  
 Program.cs  
 Program, który uruchamia przepływ pracy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania HelloWorld.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.