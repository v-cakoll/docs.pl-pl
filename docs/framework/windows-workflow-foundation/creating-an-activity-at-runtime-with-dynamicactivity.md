---
title: Tworzenie działania w czasie wykonywania za pomocą działania DynamicActivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 58dea5f6e469f871da35fc57aa4d9d8a1266bfed
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724635"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Tworzenie działania w czasie wykonywania za pomocą działania DynamicActivity
<xref:System.Activities.DynamicActivity> jest klasą konkretną, sealed przy użyciu publicznego konstruktora. <xref:System.Activities.DynamicActivity> może służyć do włączenia funkcji działania w czasie wykonywania za pomocą działania modelu DOM.  
  
## <a name="dynamicactivity-features"></a>Funkcje DynamicActivity  
 <xref:System.Activities.DynamicActivity> ma dostęp do właściwości wykonywania, argumentów i zmiennych, ale nie dostęp do usług czasu wykonywania, takich jak planowanie działania podrzędne lub śledzenia.  
  
 Można ustawić właściwości najwyższego poziomu za pomocą przepływu pracy <xref:System.Activities.Argument> obiektów. Kodu imperatywnego tych argumentów tworzonych za pomocą właściwości CLR dla nowego typu. W XAML, są deklarowane za pomocą `x:Class` i `x:Member` tagów.  
  
 Tworzony przy użyciu działań <xref:System.Activities.DynamicActivity> interfejs za pomocą projektanta przy użyciu <xref:System.ComponentModel.ICustomTypeDescriptor>. Działania utworzone w Projektancie można załadować dynamicznie przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak pokazano w poniższej procedurze.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Aby utworzyć działanie w czasie wykonywania przy użyciu kodu imperatywnego  
  
1.  OpenVisual Studio 2010.  
  
2.  Wybierz **pliku**, **nowe**, **projektu**. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **sekwencyjne Aplikacja konsoli przepływu pracy** w **szablony** okna. Nazwa nowego projektu DynamicActivitySample.  
  
3.  Kliknij prawym przyciskiem myszy Workflow1.xaml w projekcie HelloActivity, a następnie wybierz pozycję **Usuń**.  
  
4.  Otwórz plik Program.cs. Dodaj następującą dyrektywę na początku pliku.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  Zastąp zawartość `Main` metoda poniższym kodem, który tworzy <xref:System.Activities.Statements.Sequence> działania, który zawiera jeden <xref:System.Activities.Statements.WriteLine> działania i przypisuje go do <xref:System.Activities.DynamicActivity.Implementation%2A> właściwość nowe działanie dynamicznych.  
  
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
  
6.  Wykonania aplikacji. Okno konsoli z tekstu "Hello World!" Wyświetla.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Aby utworzyć działanie w czasie wykonywania przy użyciu XAML  
  
1.  Open Visual Studio 2010.  
  
2.  Wybierz **pliku**, **nowe**, **projektu**. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **Aplikacja konsoli przepływu pracy** w **szablony** okna. Nazwa nowego projektu DynamicActivitySample.  
  
3.  Otwórz Workflow1.xaml w projekcie HelloActivity. Kliknij przycisk **argumenty** opcję w dolnej części projektanta. Utwórz nową `In` argument o nazwie `TextToWrite` typu `String`.  
  
4.  Przeciągnij **WriteLine** działanie z **podstawowych** sekcji przybornika na powierzchni projektowej. Przypisz wartość `TextToWrite` do **tekstu** właściwości działania.  
  
5.  Otwórz plik Program.cs. Dodaj następującą dyrektywę na początku pliku.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  Zastąp zawartość `Main` metoda następującym kodem.  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  Wykonania aplikacji. Okno konsoli z tekstu "Hello World!" zostanie wyświetlone.  
  
8.  Kliknij prawym przyciskiem myszy plik Workflow1.xaml **Eksploratora rozwiązań** i wybierz **Wyświetl kod**. Należy zauważyć, że klasa działania jest tworzona z `x:Class` , a właściwość jest tworzony przy użyciu `x:Property`.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego](authoring-workflows-activities-and-expressions-using-imperative-code.md)
