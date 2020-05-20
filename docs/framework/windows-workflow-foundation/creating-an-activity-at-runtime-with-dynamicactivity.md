---
title: Tworzenie działania w czasie wykonywania z dynamiczną
description: Dynamiczna jest klasą zapieczętowana z konstruktorem publicznym. Użyj klasy, aby złożyć funkcję działania w czasie wykonywania przy użyciu modelu DOM działania.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421543"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Tworzenie działania w czasie wykonywania z dynamiczną
<xref:System.Activities.DynamicActivity>jest konkretną klasą zapieczętowana z konstruktorem publicznym. <xref:System.Activities.DynamicActivity>może służyć do łączenia funkcji działania w środowisku uruchomieniowym przy użyciu modelu DOM działania.  
  
## <a name="dynamicactivity-features"></a>Funkcje dynamiczne  
 <xref:System.Activities.DynamicActivity>ma dostęp do właściwości wykonywania, argumentów i zmiennych, ale nie ma dostępu do usług czasu wykonywania, takich jak planowanie działań podrzędnych lub śledzenie.  
  
 Właściwości najwyższego poziomu można ustawić za pomocą <xref:System.Activities.Argument> obiektów przepływu pracy. W kodzie bezwzględnym te argumenty są tworzone przy użyciu właściwości CLR dla nowego typu. W języku XAML są one deklarowane przy użyciu `x:Class` `x:Member` tagów i.  
  
 Działania skonstruowane przy użyciu <xref:System.Activities.DynamicActivity> interfejsu z projektantem przy użyciu <xref:System.ComponentModel.ICustomTypeDescriptor> . Działania utworzone w projektancie mogą być ładowane dynamicznie przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> , jak pokazano w poniższej procedurze.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Aby utworzyć działanie w czasie wykonywania przy użyciu kodu bezwzględnego  
  
1. Otwórz Studio 2010.  
  
2. Wybierz **plik**, **Nowy**, **projekt**. Wybierz pozycję **Workflow 4,0** w obszarze **Visual C#** w oknie **typy projektów** , a następnie wybierz węzeł **V2010** . W oknie **Szablony** wybierz **kolejno pozycje sekwencyjna aplikacja konsoli przepływu pracy** . Nazwij nowy projekt DynamicActivitySample.  
  
3. Kliknij prawym przyciskiem myszy pozycję Workflow1. XAML w projekcie Hello i wybierz polecenie **Usuń**.  
  
4. Otwórz Program.cs. Dodaj następującą dyrektywę na początku pliku.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Zamień zawartość `Main` metody na następujący kod, który tworzy <xref:System.Activities.Statements.Sequence> działanie zawierające pojedyncze <xref:System.Activities.Statements.WriteLine> działanie i przypisuje je do <xref:System.Activities.DynamicActivity.Implementation%2A> właściwości nowego działania dynamicznego.  
  
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
  
6. Wykonaj aplikację. Okno konsoli z tekstem "Hello world!" listę.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Aby utworzyć działanie w środowisku uruchomieniowym przy użyciu języka XAML  
  
1. Otwórz program Visual Studio 2010.  
  
2. Wybierz **plik**, **Nowy**, **projekt**. Wybierz pozycję **Workflow 4,0** w obszarze **Visual C#** w oknie **typy projektów** , a następnie wybierz węzeł **V2010** . W oknie **Szablony** wybierz pozycję **aplikacja konsoli przepływu pracy** . Nazwij nowy projekt DynamicActivitySample.  
  
3. Otwórz Workflow1. XAML w projekcie Hello. Kliknij opcję **argumenty** u dołu okna projektanta. Utwórz nowy `In` argument o nazwie `TextToWrite` typu `String` .  
  
4. Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** przybornika na powierzchnię projektanta. Przypisz wartość `TextToWrite` do właściwości **Text** działania.  
  
5. Otwórz Program.cs. Dodaj następującą dyrektywę na początku pliku.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Zastąp zawartość metody `Main` następującym kodem.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Wykonaj aplikację. Okno konsoli z tekstem "Hello world!" się.  
  
8. Kliknij prawym przyciskiem myszy plik Workflow1. XAML w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**. Należy zauważyć, że Klasa Activity jest tworzona z `x:Class` i właściwość jest tworzona przy użyciu `x:Property` .  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego](authoring-workflows-activities-and-expressions-using-imperative-code.md)
