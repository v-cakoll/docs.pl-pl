---
title: "Tworzenie w czasie wykonywania z DynamicActivity działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c984d235521a86c9657630d7ace3341c68f806ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Tworzenie w czasie wykonywania z DynamicActivity działania
<xref:System.Activities.DynamicActivity>jest klasą konkretną, sealed z publicznym konstruktorem. <xref:System.Activities.DynamicActivity>można użyć do włączenia funkcji działania w czasie wykonywania za pomocą działania modelu DOM.  
  
## <a name="dynamicactivity-features"></a>Funkcje DynamicActivity  
 <xref:System.Activities.DynamicActivity>ma dostęp do właściwości wykonania, argumentów i zmienne, ale brak dostępu do usługi czasu wykonywania, takie jak planowania działań podrzędnych lub śledzenia.  
  
 Można ustawić właściwości najwyższego poziomu za pomocą przepływu pracy <xref:System.Activities.Argument> obiektów. W kodzie imperatywnych tych argumentów są tworzone przy użyciu właściwości CLR dla nowego typu. W języku XAML, są one uznane za pomocą `x:Class` i `x:Member` tagów.  
  
 Działania utworzone za pomocą <xref:System.Activities.DynamicActivity> interfejsu przy użyciu projektanta <xref:System.ComponentModel.ICustomTypeDescriptor>. Działania utworzone w Projektancie mogą być ładowane dynamicznie za pomocą <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak to pokazano w poniższej procedurze.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Aby utworzyć działanie w czasie wykonywania za pomocą kodu imperatywne  
  
1.  Otwórz[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Wybierz **pliku**, **nowe**, **projektu**. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **sekwencyjnych Aplikacja konsoli przepływu pracy** w **szablony** okna. Nazwa nowego projektu DynamicActivitySample.  
  
3.  Kliknij prawym przyciskiem myszy Workflow1.xaml w projekcie HelloActivity i wybierz **usunąć**.  
  
4.  Otwórz plik Program.cs. Dodaj następujące dyrektywy do początku pliku.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  Zastąp zawartość `Main` metodę z następującym kodem, który tworzy <xref:System.Activities.Statements.Sequence> działania, która zawiera jedną <xref:System.Activities.Statements.WriteLine> działania i przypisuje go do <xref:System.Activities.DynamicActivity.Implementation%2A> właściwości dynamicznych nowe działanie.  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  Uruchom aplikację. Okno konsoli na tekst "Hello World!" Wyświetla.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Aby utworzyć działanie w środowisku uruchomieniowym przy użyciu kodu XAML  
  
1.  Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Wybierz **pliku**, **nowe**, **projektu**. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **Aplikacja konsoli przepływu pracy** w **szablony** okna. Nazwa nowego projektu DynamicActivitySample.  
  
3.  Otwórz Workflow1.xaml w projekcie HelloActivity. Kliknij przycisk **argumenty** opcji w dolnej części projektanta. Utwórz nową `In` argument o nazwie `TextToWrite` typu `String`.  
  
4.  Przeciągnij **WriteLine** działania z **podstawowych** sekcji przybornika na powierzchnię projektanta. Przypisuje wartość `TextToWrite` do **tekst** właściwości działania.  
  
5.  Otwórz plik Program.cs. Dodaj następujące dyrektywy do początku pliku.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  Zastąp zawartość `Main` metodę z następującym kodem.  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  Uruchom aplikację. Okno konsoli na tekst "Hello World!" zostanie wyświetlone.  
  
8.  Kliknij prawym przyciskiem myszy plik Workflow1.xaml **Eksploratora rozwiązań** i wybierz **kod widoku**. Należy pamiętać, że klasa działania jest tworzona z `x:Class` i właściwość zostanie utworzona z `x:Property`.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie przepływów pracy, działań i wyrażenia przy użyciu kodu Imperatywne](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [Tworzenie DynamicActivity](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
