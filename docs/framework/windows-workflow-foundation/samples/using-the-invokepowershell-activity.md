---
title: Używanie działania InvokePowerShell
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: fa42cddd930b755e9938a02a137ee77ee273fad0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227704"
---
# <a name="using-the-invokepowershell-activity"></a>Używanie działania InvokePowerShell
Przykładowe InvokePowerShell przedstawia sposób wywołania poleceń programu Windows PowerShell przy użyciu `InvokePowerShell` działania.  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Proste innowacji poleceń programu Windows PowerShell.  
  
-   Pobieranie wartości z potoku danych wyjściowych programu Windows PowerShell i zapisanie ich w zmiennych przepływu pracy.  
  
-   Przekazywanie danych do systemu windows PowerShell jako danych wejściowych potoku wykonywania polecenia.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>Dyskusja  
 Ten przykład zawiera następujące trzy projekty.  
  
|Nazwa projektu|Opis|Pliki główne|  
|------------------|-----------------|----------------|  
|CodedClient|Przykładową aplikację klienta, który używa działania programu PowerShell.|-   **Plik program.cs**: programowe tworzy na podstawie sekwencji przepływu pracy, który wywołuje działania InvokePowerShell.|  
|DesignerClient|Zestaw działań niestandardowych, które zawierają `InvokePowerShell` niestandardowe działanie oraz innych dodatkowych działań niestandardowych i przepływu pracy, który używa tych.|<ul><li>Działania:<br /><br /> <ul><li>**PrintCollection.cs**: działanie pomocnika, która wyświetla wszystkie elementy w kolekcji do konsoli.</li><li>**ReadLine.cs**: pomocnika dotyczące wprowadzania odczytywanie z konsoli.</li></ul></li><li>System plików:<br /><br /> <ul><li>**Copy.XAML**: działanie, które służy do kopiowania pliku.</li><li>**CreateFile.xaml**: działanie, które tworzy plik.</li><li>**DeleteFile.xaml**: działanie, które usuwa plik.</li><li>**MakeDir.xaml**: działanie, które tworzy katalog.</li><li>**Move.XAML**: działania przenoszenia pliku.</li><li>**ReadFile.xaml**: działanie, które odczytuje plik i zwraca jego zawartość.</li><li>**TestPath.xaml**: działanie, które sprawdza istnienie ścieżki.</li></ul></li><li>Proces:<br /><br /> <ul><li>**GetProcess.xaml**: działanie, które pobiera listę uruchomionych procesów.</li><li>**StopProcess.xaml**: działanie, które zatrzymuje określonego procesu.</li></ul></li><li>**Plik program.cs**: wywołuje Sequence1 przepływu pracy.</li><li>**Sequence1.XAML**: przepływ pracy na podstawie sekwencji.</li></ul>|  
|PowerShell|`InvokePowerShell` Działanie i jego skojarzone projektantów.|Pliki działań<br /><br /> -   **ExecutePowerShell.cs**: logika wykonania głównego działania.<br />-   **InvokePowerShell.cs**: otokę z logiką wykonywania głównych, zawiera ogólny (wartość zwracana) i wersji nieogólnego (zwrotny wartość). Jest to interfejs publiczny dla działania.<br />-   **NoPersistZone.cs**: to działanie zapobiega utrwalanie wszystkie działania podrzędne. Ta klasa jest używana w ramach `InvokePowerShell` implementacji działania, aby uniemożliwić działanie utrwalone w środku wykonywania.<br /><br /> Pliki projektanta:<br /><br /> 1.  **ArgumentDictionaryEditor.cs**: okno dialogowe Windows, który umożliwia użytkownikowi edytowanie argumenty `InvokePowerShell` działania.<br />2.  **GenericInvokePowerShellDesigner.xaml** i **GenericInvokePowerShellDesigner.xaml.cs**: definiuje wygląd ogólnego `InvokePowerShell` działania w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].<br />3.  **InvokePowerShellDesigner.xaml** i **InvokePowerShellDesigner.cs**: definiuje wygląd elementów nieogólnego `InvokePowerShell` działania w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].|  
  
 Projektów klienckich omówiono najpierw się łatwiejsze do zrozumienia funkcje wewnętrzne działanie programu PowerShell, po jego użycie jest zrozumiały.  
  
## <a name="using-this-sample"></a>Za pomocą tego przykładu  
 Poniżej opisano sposób użycia trzy projekty w próbce.  
  
### <a name="using-the-coded-client-project"></a>Za pomocą projektu kodowanego klienta  
 Klient przykładowy tworzy programowo działania sekwencji, który zawiera przykłady kilka różnych metod przy użyciu `InvokePowerShell` działania. Pierwsze wywołanie powoduje uruchomienie programu Notatnik.  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 Drugie wywołanie pobiera listę procesów uruchomionych na komputerze lokalnym.  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 `Output` Zmienna służy do przechowywania danych wyjściowych polecenia.  
  
 Następne wywołanie pokazuje, jak uruchomić krok przetwarzania końcowego na każdy poszczególne dane wyjściowe wywołania programu PowerShell. `InitializationAction` jest ustawiona na funkcję, która generuje reprezentację ciągu znaków dla każdego procesu. Kolekcja tych ciągów jest zwracany w `Output` zmiennej przez `InvokePowerShell<string>` działania.  
  
 Pomyślne wykonanie `InvokePowerShell` wywołania zademonstrować przekazywanie danych do działania i pobieranie danych wyjściowych i występuje.  
  
### <a name="using-the-designer-client-project"></a>Za pomocą projektu Projektanta klienta  
 Projekt DesignerClient składa się z zestawu działań niestandardowych są prawie wszystkie wbudowane zawierający `InvokePowerShell` działania. Większość działań związanych z wywołania nieogólnego wersję `InvokePowerShell` działania i nie powinna mieć wartość zwracaną. Inne działania przy użyciu ogólnych wersji `InvokePowerShell` działanie i użyj `InitializationAction` argument do przetwarzania wyników, po utworzeniu.  
  
## <a name="using-the-powershell-project"></a>Za pomocą projektu programu PowerShell  
 Akcja główna działania odbywa się w `ExecutePowerShell` klasy. Ponieważ wykonanie polecenia programu PowerShell nie powinny blokować wątku głównego przepływu pracy, działanie jest tworzona jako asynchroniczną działania przez dziedziczenie z <xref:System.Activities.AsyncCodeActivity> klasy.  
  
 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Metoda jest wywoływana przez środowisko wykonawcze przepływów pracy, aby rozpocząć działania. Uruchamia przez wywołanie interfejsów API programu PowerShell w celu utworzenia potoku programu PowerShell.  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 Następnie tworzy polecenia programu PowerShell i wypełnia je parametry i zmienne.  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 Dane wejściowe potokiem w również są wysyłane do potoku w tym momencie. Na koniec otoczona potoku `PipelineInvokerAsyncResult` obiektu i zwracana. `PipelineInvokerAsyncResult` Obiektu rejestruje odbiornik i wywołuje potok.  
  
```  
pipeline.InvokeAsync();  
```  
  
 Po zakończeniu wykonywania, dane wyjściowe i błędów są przechowywane w tej samej `PipelineInvokerAsyncResult` obiektu i kontroli jest zwracane do środowiska wykonawczego przepływów pracy za pomocą wywołania metody wywołania zwrotnego pierwotnie przekazana do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.  
  
 Na końcu metody wykonywania przepływu pracy środowisko wykonawcze wywołuje działania <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody.  
  
 `InvokePowerShell` Klasy zawija `ExecutePowerShellCommand` klasy i tworzy dwie wersje działanie; ogólny wersja oraz wersja nieogólnego. Wersja nieogólnego zwraca dane wyjściowe wykonania programu PowerShell bezpośrednio, natomiast ogólnego wersji przekształca wyniki poszczególnych do typu ogólnego.  
  
 Wersja ogólnego działania jest implementowany jako sekwencyjny przepływ pracy, który wywołuje `ExecutePowerShellCommand` i przetwarza po jego wyniki. Dla każdego elementu w kolekcji wynik wywołania krok przetwarzania końcowego `InitializationAction` Jeśli jest ustawiona. W przeciwnym razie jest proste rzutowania.  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 Dla każdego z dwóch `InvokePowerShell` działań (ogólnych i nieogólnego), Projektant został utworzony. InvokePowerShellDesigner.xaml i jego pliku .cs skojarzone zdefiniować wygląd w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] nieogólnego wersję `InvokePowerShell` działania. Wewnątrz InvokePowerShellDesigner.xaml <xref:System.Windows.Controls.DockPanel> jest używana do reprezentowania interfejsu graficznego.  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 Należy pamiętać, że `Text` właściwości pola tekstowego jest dwukierunkowego powiązania, które zapewnia, że wartość tego działania `CommandText` właściwość jest równoważna wartości danych wejściowych do projektanta.  
  
 GenericInvokePowerShellDesigner.xaml i jego pliku .cs skojarzone definiują interfejs graficzny dla ogólnego `InvokePowerShell` działania. Projektant jest nieco bardziej skomplikowane, ponieważ umożliwia użytkownikom ustawienie `InitializationAction`. Kluczowym elementem jest użycie <xref:System.Activities.Presentation.WorkflowItemPresenter> umożliwia przeciąganie i upuszczanie działania podrzędne na `InvokePowerShell` powierzchni projektowej.  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 Dostosowywanie projektanta nie zatrzymuje się z plikami XAML zdefiniować wygląd działania na kanwę projektu. Okna dialogowe, używany do wyświetlania parametrów działania można również dostosować. Te parametry i zmienne programu PowerShell mają wpływ na zachowanie poleceń programu PowerShell. Działanie udostępnia je jako <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` typów. ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml i PropertyEditorResources.cs zdefiniować okno dialogowe, które służy do edytowania tych typów.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
 Należy zainstalować program Windows PowerShell, aby uruchomić ten przykład. Windows PowerShell można zainstalować z tej lokalizacji: [programu Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).  
  
#### <a name="to-run-the-coded-client"></a>Aby uruchomić kodowane klienta  
  
1.  Otwórz za pomocą PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Kliknij prawym przyciskiem myszy rozwiązanie i skompiluj je.  
  
3.  Kliknij prawym przyciskiem myszy **CodedClient** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
4.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
#### <a name="to-run-the-designer-client"></a>Aby uruchomić projektanta klienta  
  
1.  Otwórz za pomocą PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Kliknij prawym przyciskiem myszy rozwiązanie i skompiluj je.  
  
3.  Kliknij prawym przyciskiem myszy **DesignerClient** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
4.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
## <a name="known-issues"></a>Znane problemy  
  
1.  Jeśli odwołanie do `InvokePowerShell` zestawu działań lub projekt z innego projektu spowoduje błąd kompilacji, może być konieczne ręczne dodawanie `<SpecificVersion>True</SpecificVersion>` elementu do nowego projektu w wierszu, który odwołuje się plik .csproj `InvokePowerShell`.  
  
2.  Jeśli nie zainstalowano programu Windows PowerShell, następujący komunikat o błędzie jest wyświetlany w programie Visual Studio, zaraz po dodaniu `InvokePowerShell` działanie do przepływu pracy: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  W programie Windows PowerShell 2.0 programowo wywoływania `$input.MoveNext()` kończy się niepowodzeniem i skrypty, używając `$input.MoveNext()` generuje błędy niezamierzone i wyników. Aby obejść ten problem, należy rozważyć użycie zlecenie PowerShell `foreach` zamiast wywoływać metodę `MoveNext()` podczas iteracji tablicy.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`