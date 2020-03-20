---
title: Tworzenie działania w czasie wykonywania za pomocą dynamicactivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182991"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Tworzenie działania w czasie wykonywania za pomocą dynamicactivity
<xref:System.Activities.DynamicActivity>jest betonową, uszczelnioną klasą z konstruktorem publicznym. <xref:System.Activities.DynamicActivity>może służyć do montażu funkcji działania w czasie wykonywania przy użyciu działania DOM.  
  
## <a name="dynamicactivity-features"></a>Funkcje DynamicActivity  
 <xref:System.Activities.DynamicActivity>ma dostęp do właściwości wykonywania, argumentów i zmiennych, ale nie ma dostępu do usług w czasie wykonywania, takich jak planowanie działań podrzędnych lub śledzenia.  
  
 Właściwości najwyższego poziomu można ustawić <xref:System.Activities.Argument> za pomocą obiektów przepływu pracy. W kodzie imperatywnym te argumenty są tworzone przy użyciu właściwości CLR na nowy typ. W języku XAML są `x:Class` `x:Member` one zadeklarowane przy użyciu i tagi.  
  
 Działania skonstruowane <xref:System.Activities.DynamicActivity> przy użyciu interfejsu <xref:System.ComponentModel.ICustomTypeDescriptor>z projektantem przy użyciu . Działania utworzone w projektancie można ładować dynamicznie przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak pokazano w poniższej procedurze.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Aby utworzyć działanie w czasie wykonywania przy użyciu kodu imperatywu  
  
1. OpenVisual Studio 2010.  
  
2. Wybierz **pozycję Plik**, **Nowy**, **Projekt**. Wybierz **przepływ pracy 4.0** w obszarze **Visual C#** w oknie **Typy projektu** i wybierz węzeł w wersji **2010.** Wybierz **kolejną aplikację konsoli przepływu pracy** w oknie **Szablony.** Nazwij nowy projekt DynamicActivitySample.  
  
3. Kliknij prawym przyciskiem myszy pozycję Przepływ pracy1.xaml w projekcie HelloActivity i wybierz polecenie **Usuń**.  
  
4. Otwórz Program.cs. Dodaj następującą dyrektywę do górnej części pliku.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Zastąp `Main` zawartość metody następującym kodem, który <xref:System.Activities.Statements.Sequence> tworzy <xref:System.Activities.Statements.WriteLine> działanie, które zawiera <xref:System.Activities.DynamicActivity.Implementation%2A> pojedyncze działanie i przypisuje je do właściwości nowego działania dynamicznego.  
  
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
  
6. Wykonaj aplikację. Okno konsoli z tekstem "Hello World!" Wyświetla.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Aby utworzyć działanie w czasie wykonywania przy użyciu języka XAML  
  
1. Otwórz program Visual Studio 2010.  
  
2. Wybierz **pozycję Plik**, **Nowy**, **Projekt**. Wybierz **przepływ pracy 4.0** w obszarze **Visual C#** w oknie **Typy projektu** i wybierz węzeł w wersji **2010.** Wybierz pozycję **Aplikacja konsoli przepływu pracy** w oknie **Szablony.** Nazwij nowy projekt DynamicActivitySample.  
  
3. Otwórz plik Workflow1.xaml w projekcie HelloActivity. Kliknij opcję **Argumenty** u dołu projektanta. Utwórz `In` nowy `TextToWrite` argument `String`o nazwie typu .  
  
4. Przeciągnij działanie **WriteLine** z sekcji **Podstawowe przybornika** na powierzchnię projektanta. Przypisz `TextToWrite` wartość do **właściwości Text** działania.  
  
5. Otwórz Program.cs. Dodaj następującą dyrektywę do górnej części pliku.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Zastąp zawartość metody `Main` następującym kodem.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Wykonaj aplikację. Okno konsoli z tekstem "Hello World!" Pojawia się.  
  
8. Kliknij prawym przyciskiem myszy plik Workflow1.xaml w **Eksploratorze rozwiązań** i wybierz polecenie **Wyświetl kod**. Należy zauważyć, że klasa `x:Class` działania jest tworzona z i właściwość jest tworzona z `x:Property`.  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego](authoring-workflows-activities-and-expressions-using-imperative-code.md)
