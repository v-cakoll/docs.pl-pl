---
title: Integracja programu WF w języku XAML i WPF
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 2fb145a8511383c37be536a78522a256514c08c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518193"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>Integracja programu WF w języku XAML i WPF
Ten przykład przedstawia sposób tworzenia aplikacji, która używa funkcji systemu Windows Presentation Foundation (WPF) i Windows Workflow Foundation (WF) w jednym dokumencie XAML. W tym celu próbki korzysta z rozszerzeń systemu Windows Workflow Foundation (WF) i języka XAML.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Deserializuje pliku ShowWindow.xaml do <xref:System.Activities.Statements.Sequence> działania dwóch zmiennych ciągu, które są manipulować przez działania sekwencji: `ShowWindow` i `WriteLine`. <xref:System.Activities.Statements.WriteLine> Działania danych wyjściowych do okna konsoli wyrażenia, który przypisuje do <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości. `ShowWindow` Wyświetla działanie [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] okno jako część jej logiki wykonywania. <xref:System.Activities.ActivityContext.DataContext%2A> Okna zawiera zmienne zadeklarowane w sekwencji. Formanty okna zadeklarowany w `ShowWindow` działania zaznaczać tych zmiennych za pomocą wiązania z danymi. Na koniec okna zawiera kontrolkę przycisku. `Click` Zdarzenie dla przycisku jest obsługiwane przez <xref:System.Activities.ActivityDelegate> o nazwie `MarkupExtension` zawierający `CloseWindow` działania. `MarkUpExtension` wywołuje zawarte działanie, która udostępnia kontekst, wszystkie obiekty określone przez `x:Name`, a także <xref:System.Activities.ActivityContext.DataContext%2A> okna nadrzędnego. W związku z tym `CloseWindow.InArgument<Window>` powiązany za pomocą wyrażenia, który odwołuje się do nazwy okna.  
  
 `ShowWindow` Działania jest pochodną <xref:System.Activities.AsyncCodeActivity%601> klasy do wyświetlenia [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] okna i działanie jest kończone po zamknięciu okna. `Window` Właściwość jest typu `Func<Window>` umożliwiająca okno, aby być tworzone na żądanie dla każdego wykonania działania. `Window` Używa właściwości <xref:System.Xaml.XamlDeferringLoader> do modelu oceny odroczonej. `FuncFactoryDeferringLoader` Umożliwia `XamlReader` przechwycone podczas serializacji i następnie odczytywane podczas wykonywania działania.  
  
 Dobrze napisane działania nigdy nie blokuje wątku harmonogramu. Jednak `ShowWindow` do czasu zamknięcia okna, okno nie może ukończyć działania. `ShowWindow` Działania osiąga to zachowanie, wynikające z <xref:System.Activities.AsyncCodeActivity>, wywoływania <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> metody w <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> — metoda i wyświetlanie okna w trybie modalnym. Delegat jest wywoływany przez podsystem WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>. `ShowWindow` Przypisuje działania <xref:System.Activities.ActivityContext.DataContext%2A> właściwości `Window.DataContext` właściwość żadnych danych powiązana kontroli dostępu do zmiennych w zakresie.  
  
 Ostatni punkt odsetek w tym przykładzie jest <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> o nazwie `DelegateActivityExtension`. `ProvideValue` Metoda tego rozszerzenia znacznika zwraca delegata, który wywołuje aktywność osadzonych. To działanie jest uruchamiany w środowisku zawierającym [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] kontekstu danych i wszystkie `x:Name` wartości w zakresie. W `GenericInvoke` metody, to środowisko jest dostępne do działania za pośrednictwem <xref:System.Activities.Hosting.SymbolResolver> rozszerzenia. To rozszerzenie jest dodawany do <xref:System.Activities.WorkflowInvoker> następnie używany do wywołania osadzonych działania zawsze, gdy jest wywoływany delegat rozszerzenia znaczników.  
  
> [!NOTE]
>  Projektant domyślny nie obsługuje działania ShowWindow; w efekcie plik ShowWindow.Xaml nie są wyświetlane poprawnie w projektancie.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WPFWFIntegration.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
4.  Wpisz swoje imię i nazwisko w oknie dialogowym.  
  
5.  Zamknij okno dialogowe i konsolę zwraca nazwę.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`