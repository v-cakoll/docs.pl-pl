---
title: Integracja WPF i WF w języku XAML
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 8b461ee3185aa60e885d7cc107124c37d9ffacef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948963"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>Integracja WPF i WF w języku XAML
Ten przykład pokazuje, jak utworzyć aplikację, która używa funkcji Windows Presentation Foundation (WPF) i Windows Workflow Foundation (WF) w jednym dokumencie XAML. Aby to osiągnąć, przykład używa Windows Workflow Foundation (WF) i rozszerzalności XAML.

## <a name="sample-details"></a>Przykładowe szczegóły
 Plik funkcja ShowWindow. XAML deserializacji do <xref:System.Activities.Statements.Sequence> działania z dwoma zmiennymi ciągów, które są manipulowane przez działania sekwencji: `ShowWindow` i `WriteLine`. Dane wyjściowe <xref:System.Activities.Statements.WriteLine.Text%2A> działania do okna konsoli wyrażenie przypisywane do właściwości. <xref:System.Activities.Statements.WriteLine> `ShowWindow` Działanie wyświetla okno WPF jako część logiki wykonywania. <xref:System.Activities.ActivityContext.DataContext%2A> Okno zawiera zmienne zadeklarowane w sekwencji. Kontrolki okna zadeklarowane w `ShowWindow` działaniu używają powiązań danych do manipulowania tymi zmiennymi. Na koniec okno zawiera kontrolkę Button. Zdarzenie dla przycisku jest obsługiwane <xref:System.Activities.ActivityDelegate> przez nazwa `MarkupExtension` , która zawiera `CloseWindow` działanie. `Click` `MarkUpExtension`wywołuje zawarte działanie, które zapewnia, jako kontekst, wszystkie obiekty identyfikowane przez `x:Name`, a także <xref:System.Activities.ActivityContext.DataContext%2A> okno zawierające. W `CloseWindow.InArgument<Window>` tym celu można powiązać za pomocą wyrażenia, które odwołuje się do nazwy okna.

 `ShowWindow` Działanie dziedziczy<xref:System.Activities.AsyncCodeActivity%601> z klasy, aby wyświetlić okno WPF i kończy się po zamknięciu okna. Właściwość jest typu `Func<Window>` , który umożliwia tworzenie okna na żądanie dla każdego wykonywania działania. `Window` Właściwość używa, <xref:System.Xaml.XamlDeferringLoader> aby włączyć ten odroczony model oceny. `Window` `FuncFactoryDeferringLoader` Program`XamlReader` umożliwia przechwytywanie podczas serializacji, a następnie odczytywanie podczas wykonywania działania.

 Działanie dobrze napisywane nigdy nie blokuje wątku harmonogramu. Nie można jednak `ShowWindow` ukończyć działania, dopóki okno, które jest wyświetlane, nie jest zamknięte. Działanie osiąga takie zachowanie, pobierając od <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> wywołując <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> metodę z metody i wyświetlając okno modalnie. `ShowWindow` Delegat jest wywoływany za pomocą WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>. Działanie przypisuje właściwość do `Window.DataContext` właściwości, aby zapewnić wszystkim kontrolom związanym z danymi dostęp do zmiennych w zakresie. <xref:System.Activities.ActivityContext.DataContext%2A> `ShowWindow`

 Ostatnim punktem zainteresowania tego przykładu jest <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> wywołana. `DelegateActivityExtension` `ProvideValue` Metoda tego rozszerzenia znacznika zwraca delegata, który wywołuje działanie osadzone. To działanie jest uruchamiane w środowisku, które zawiera kontekst danych WPF i wszystkie `x:Name` wartości w zakresie. W metodzie to środowisko jest dostarczane do działania <xref:System.Activities.Hosting.SymbolResolver> za pomocą rozszerzenia. `GenericInvoke` To rozszerzenie jest dodawane do <xref:System.Activities.WorkflowInvoker> obiektu, który jest następnie używany do wywołania osadzonego działania za każdym razem, gdy zostanie wywołana delegat rozszerzenia znaczników.

> [!NOTE]
> Domyślny projektant nie obsługuje działania funkcja ShowWindow; w związku z tym plik funkcja ShowWindow. XAML nie jest wyświetlany prawidłowo w projektancie.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania WPFWFIntegration. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

4. Wpisz swoje imię i nazwisko w oknie dialogowym.

5. Zamknij okno dialogowe, a konsola zwraca nazwę użytkownika.

> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
