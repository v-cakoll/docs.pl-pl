---
title: Za pomocą działania InvokePowerShell
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: c5609556af94ed3e372538047ff6309a105975ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520243"
---
# <a name="using-the-invokepowershell-activity"></a>Za pomocą działania InvokePowerShell
InvokePowerShell przykładowych pokazano, jak można wywołać za pomocą poleceń programu Windows PowerShell `InvokePowerShell` działania.  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Proste innowacji poleceń programu Windows PowerShell.  
  
-   Pobieranie wartości z potoku dane wyjściowe programu Windows PowerShell i zapisanie ich w zmiennych przepływu pracy.  
  
-   Przekazywanie danych w systemie windows PowerShell jako wejściowych potoku wykonywania polecenia.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>Omówienie  
 Ten przykład zawiera następujące trzy projekty.  
  
|Nazwa projektu|Opis|Główne pliki|  
|------------------|-----------------|----------------|  
|CodedClient|Przykładowej aplikacji klienta, który używa działanie programu PowerShell.|-   **Plik program.cs**: programowane tworzy na podstawie sekwencji przepływu pracy, który wywołuje InvokePowerShell działania.|  
|DesignerClient|Zestaw działań niestandardowych, które zawierają `InvokePowerShell` działań niestandardowych i innych dodatkowych działań niestandardowych i przepływu pracy, który używa ich.|<ul><li>Działania:<br /><br /> <ul><li>**PrintCollection.cs**: działanie pomocnika, która wyświetla wszystkie elementy kolekcji do konsoli.</li><li>**ReadLine.cs**: działaniem pomocnika dla danych wejściowych odczytu z konsoli.</li></ul></li><li>System plików:<br /><br /> <ul><li>**Copy.XAML**: działanie, które kopiuje plik.</li><li>**CreateFile.xaml**: działanie, które tworzy plik.</li><li>**DeleteFile.xaml**: działanie, które usuwa plik.</li><li>**MakeDir.xaml**: działanie, które tworzy katalog.</li><li>**Move.XAML**: działanie, które przenosi plik.</li><li>**ReadFile.xaml**: działanie, które umożliwia odczytanie pliku i zwraca jego zawartość.</li><li>**TestPath.xaml**: działanie, które sprawdza istnienie ścieżki.</li></ul></li><li>Proces:<br /><br /> <ul><li>**GetProcess.xaml**: działanie, które pobiera listę uruchomionych procesów.</li><li>**StopProcess.xaml**: działanie, które zatrzymuje określonego procesu.</li></ul></li><li>**Plik program.cs**: wywołanie Sequence1 przepływu pracy.</li><li>**Sequence1.XAML**: przepływ pracy oparty na sekwencji.</li></ul>|  
|PowerShell|`InvokePowerShell` Działanie i jego skojarzony projektantów.|Pliki działań<br /><br /> -   **ExecutePowerShell.cs**: logiki główny wykonywania działania.<br />-   **InvokePowerShell.cs**: otokę z logiką wykonywania głównych, zawiera ogólne (wartość zwrotna) i wersji nierodzajową (wartość-return). Jest to interfejs publiczny dla działania.<br />-   **NoPersistZone.cs**: działanie uniemożliwia utrwalanie żadnych działań podrzędnych. Ta klasa jest używana w ramach `InvokePowerShell` implementacji działania uniemożliwi działanie utrwalone pośredniej wykonywania.<br /><br /> Projektant plików:<br /><br /> 1.  **ArgumentDictionaryEditor.cs**: okno dialogowe systemu Windows, który umożliwia użytkownikom edytowanie argumenty `InvokePowerShell` działania.<br />2.  **GenericInvokePowerShellDesigner.xaml** i **GenericInvokePowerShellDesigner.xaml.cs**: Określa wygląd ogólnego `InvokePowerShell` działania w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].<br />3.  **InvokePowerShellDesigner.xaml** i **InvokePowerShellDesigner.cs**: Określa wygląd nieogólnego `InvokePowerShell` działania w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].|  
  
 Projektów klienckich omówiono najpierw, ponieważ jest łatwiejsze do zrozumienia funkcji wewnętrznego działania programu PowerShell, po jego użycia jest rozpoznawany.  
  
## <a name="using-this-sample"></a>Za pomocą tego przykładu  
 W poniższych sekcjach opisano sposób użycia trzy projekty w próbce.  
  
### <a name="using-the-coded-client-project"></a>Za pomocą programu Project kodowane klienta  
 Klient próbki programowo tworzy działania sequence, który zawiera przykłady kilka różnych metod za pomocą `InvokePowerShell` działania. Pierwsze uruchomienie uruchamia Notatnik.  
  
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
  
 `Output` zmienna jest używana do przechowywania danych wyjściowych polecenia.  
  
 Następne wywołanie pokazuje, jak przetwarzanie końcowe krok zostanie uruchomiony na każdej poszczególnych danych wyjściowych wywołania programu PowerShell. `InitializationAction` ustawiono funkcji, które generuje reprezentację ciągu dla każdego procesu. Kolekcja te ciągi, jest zwracany w `Output` zmiennej przez `InvokePowerShell<string>` działania.  
  
 Pomyślne `InvokePowerShell` wywołania pokazują przekazywanie danych do działania i pobierania danych wyjściowych i błędów wychodzących.  
  
### <a name="using-the-designer-client-project"></a>Przy użyciu klienta projektanta projektu  
 Projekt DesignerClient składa się z zestawu działań niestandardowych prawie wszystkie są wbudowane, zawierający `InvokePowerShell` działania. Większość działań wywołać wersja nieogólnego `InvokePowerShell` działania i nie oczekuje wartości zwracanej. Inne działania przy użyciu wersji ogólnego `InvokePowerShell` działania i użyj `InitializationAction` argument po przetwarzaniu wyniki.  
  
## <a name="using-the-powershell-project"></a>Przy użyciu programu PowerShell projektu  
 Akcja główna działania ma miejsce w `ExecutePowerShell` klasy. Ponieważ wykonanie polecenia programu PowerShell nie powinny blokować wątku głównego przepływu pracy, działanie jest tworzony za działanie asynchroniczne poprzez dziedziczenie z <xref:System.Activities.AsyncCodeActivity> klasy.  
  
 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Metoda jest wywoływana przez środowisko uruchomieniowe przepływu pracy, aby rozpocząć uruchomienia działania. Rozpoczyna się przez wywoływanie interfejsów API środowiska PowerShell, aby utworzyć potok programu PowerShell.  
  
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
  
 Dane wejściowe przekazywane w potoku w są także wysyłane do potoku w tym momencie. Na koniec potoku jest ujęte w `PipelineInvokerAsyncResult` obiektu i zwracane. `PipelineInvokerAsyncResult` Obiektu rejestruje odbiornik i wywołuje potok.  
  
```  
pipeline.InvokeAsync();  
```  
  
 Po zakończeniu wykonywania, danych wyjściowych i błędów są przechowywane w tym samym `PipelineInvokerAsyncResult` obiektu i kontroli jest zwracane do środowiska uruchomieniowego przepływu pracy, wywołując metodę wywołania zwrotnego oryginalnie przekazana do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.  
  
 Po zakończeniu wykonywania metody środowiska uruchomieniowego przepływu pracy wywołuje działania <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody.  
  
 `InvokePowerShell` Klasy zawija `ExecutePowerShellCommand` klasy i tworzy dwie wersje działanie; ogólny wersja oraz wersja nierodzajową. Wersja nieogólnego zwraca dane wyjściowe wykonania programu PowerShell bezpośrednio, natomiast ogólnego wersji przekształca poszczególne wyniki do typu ogólnego.  
  
 Wersja ogólnego działania jest zaimplementowany jako sekwencyjnego przepływu pracy, który wywołuje `ExecutePowerShellCommand` i przetwarza po jego wyniki. Dla każdego elementu w kolekcji wynik przetwarzania końcowego krok wywołuje `InitializationAction` Jeśli jest ustawiona. W przeciwnym razie ma prosty rzutowania.  
  
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
  
 Dla każdego z tych `InvokePowerShell` działania (ogólne i inny niż ogólny), projektanta został utworzony. InvokePowerShellDesigner.xaml i jego plik skojarzony CS określenia jej wyglądu w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] wersji nieogólnego `InvokePowerShell` działania. Wewnątrz InvokePowerShellDesigner.xaml <xref:System.Windows.Controls.DockPanel> jest używana do reprezentowania interfejsu graficznego.  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 Należy pamiętać, że `Text` właściwości pola tekstowego jest wiązanie dwukierunkowe, który zapewnia, że wartość działania `CommandText` właściwości jest odpowiednikiem wartości danych wejściowych do projektanta.  
  
 GenericInvokePowerShellDesigner.xaml i jego plik skojarzony CS definiują interfejsu graficznego dla ogólnego `InvokePowerShell` działania. Projektant jest nieco bardziej skomplikowane, ponieważ umożliwia użytkownikom ustawianie `InitializationAction`. Użycie jest kluczowym elementem <xref:System.Activities.Presentation.WorkflowItemPresenter> zezwalająca przeciągnij i upuść działań podrzędnych na `InvokePowerShell` powierzchnię projektanta.  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 Dostosowywanie projektanta nie zatrzymuje z plikami .xaml definiujących wygląd działania w obszarze roboczym projekt. Okna dialogowe używany do wyświetlania parametry działania można również dostosować. Te parametry i zmienne środowiska PowerShell wpływają na zachowanie poleceń programu PowerShell. Działanie udostępnia je jako <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` typów. ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml i PropertyEditorResources.cs zdefiniować okno dialogowe, które umożliwia edytowanie tych typów.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
 Należy zainstalować program Windows PowerShell, aby uruchomić ten przykład. Z tej lokalizacji można zainstalować programu Windows PowerShell: [programu Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).  
  
#### <a name="to-run-the-coded-client"></a>Do uruchomienia kodowanych klienta  
  
1.  Otwórz za pomocą PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Kliknij prawym przyciskiem myszy rozwiązanie i jego tworzenia.  
  
3.  Kliknij prawym przyciskiem myszy **CodedClient** projekt i wybierz **Ustaw jako projekt startowy**.  
  
4.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
#### <a name="to-run-the-designer-client"></a>Aby uruchomić projektanta klienta  
  
1.  Otwórz za pomocą PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Kliknij prawym przyciskiem myszy rozwiązanie i jego tworzenia.  
  
3.  Kliknij prawym przyciskiem myszy **DesignerClient** projekt i wybierz **Ustaw jako projekt startowy**.  
  
4.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
## <a name="known-issues"></a>Znane problemy  
  
1.  Jeśli odwołuje się do `InvokePowerShell` zestawu działań lub projektu z innego projektu spowoduje błąd kompilacji, może być konieczne ręczne dodanie `<SpecificVersion>True</SpecificVersion>` elementu do pliku .csproj nowy projekt w wierszu, który odwołuje się do `InvokePowerShell`.  
  
2.  Jeśli nie zainstalowano programu Windows PowerShell, komunikat o błędzie jest wyświetlany w programie Visual Studio, natychmiast po dodaniu `InvokePowerShell` działania do przepływu pracy: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  W programie Windows PowerShell 2.0 programowo wywoływania `$input.MoveNext()` kończy się niepowodzeniem i skrypty, używając `$input.MoveNext()` niezamierzone błędów i wyników. Aby obejść ten problem, należy wziąć pod uwagę przy użyciu programu PowerShell zlecenie `foreach` zamiast wywoływać metodę `MoveNext()` podczas iteracji tablicy.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`