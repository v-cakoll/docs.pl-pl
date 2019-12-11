---
title: Integracja WPF i WF w języku XAML
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: b8015e5c526f58875beb58ab48a21c050bdc8a06
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960089"
---
# <a name="wpf-and-windows-workflow-foundation-integration-in-xaml"></a>Integracja WPF i Windows Workflow Foundation w języku XAML

Ten przykład pokazuje, jak utworzyć aplikację, która używa funkcji Windows Presentation Foundation (WPF) i Windows Workflow Foundation (WF) w jednym dokumencie XAML. Aby to osiągnąć, przykład używa rozszerzalności Windows Workflow Foundation i XAML.

## <a name="sample-details"></a>Przykładowe szczegóły

 Plik funkcja ShowWindow. XAML deserializacji <xref:System.Activities.Statements.Sequence> działania z dwoma zmiennymi ciągów, które są manipulowane przez działania sekwencji: `ShowWindow` i `WriteLine`. <xref:System.Activities.Statements.WriteLine> dane wyjściowe działania do okna konsoli wyrażenie przypisywane do właściwości <xref:System.Activities.Statements.WriteLine.Text%2A>. Działanie `ShowWindow` wyświetla okno WPF jako część logiki wykonywania. <xref:System.Activities.ActivityContext.DataContext%2A> okna zawiera zmienne zadeklarowane w sekwencji. Kontrolki okna zadeklarowane w działaniu `ShowWindow` używają powiązań danych do manipulowania tymi zmiennymi. Na koniec okno zawiera kontrolkę Button. Zdarzenie `Click` dla tego przycisku jest obsługiwane przez <xref:System.Activities.ActivityDelegate> o nazwie `MarkupExtension` zawierające działanie `CloseWindow`. `MarkUpExtension` wywołuje zawarte działanie, które zapewnia, jako kontekst, wszelkie obiekty zidentyfikowane przez `x:Name`, a także <xref:System.Activities.ActivityContext.DataContext%2A> okna zawierającego. W tym celu `CloseWindow.InArgument<Window>` można powiązać przy użyciu wyrażenia, które odwołuje się do nazwy okna.

 Działanie `ShowWindow` dziedziczy z klasy <xref:System.Activities.AsyncCodeActivity%601>, aby wyświetlić okno WPF i kończyło się po zamknięciu okna. Właściwość `Window` jest typu `Func<Window>`, który umożliwia tworzenie okna na żądanie dla każdego wykonywania działania. Właściwość `Window` używa <xref:System.Xaml.XamlDeferringLoader>, aby włączyć ten odroczony model oceny. `FuncFactoryDeferringLoader` umożliwia przechwytywanie `XamlReader` podczas serializacji, a następnie odczytywanie podczas wykonywania działania.

 Działanie dobrze napisywane nigdy nie blokuje wątku harmonogramu. Nie można jednak wykonać działania `ShowWindow`, dopóki okno, które jest wyświetlane, nie zostanie zamknięte. Działanie `ShowWindow` realizuje to zachowanie, pobierając od <xref:System.Activities.AsyncCodeActivity>, wywołując metodę <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> w metodzie <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i wyświetlając okno modalnie. Delegat jest wywoływany za pomocą <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>WPF. Działanie `ShowWindow` służy do przypisywania właściwości <xref:System.Activities.ActivityContext.DataContext%2A> do właściwości `Window.DataContext` w celu zapewnienia, że wszystkie kontrolki powiązane z danymi mają dostęp do zmiennych znajdujących się w zakresie.

 Ostatnim punktem zainteresowania tego przykładu jest <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> o nazwie `DelegateActivityExtension`. Metoda `ProvideValue` tego rozszerzenia znacznika zwraca delegata, który wywołuje działanie osadzone. To działanie jest uruchamiane w środowisku zawierającym kontekst danych WPF i wszelkie `x:Name` wartości w zakresie. W metodzie `GenericInvoke` to środowisko jest dostarczane do działania za pomocą rozszerzenia <xref:System.Activities.Hosting.SymbolResolver>. To rozszerzenie jest dodawane do <xref:System.Activities.WorkflowInvoker>, który jest następnie używany do wywołania osadzonego działania przy każdym wywołaniu delegata rozszerzenia znaczników.

> [!NOTE]
> Domyślny projektant nie obsługuje działania funkcja ShowWindow; w związku z tym plik funkcja ShowWindow. XAML nie jest wyświetlany prawidłowo w projektancie.

## <a name="run-the-sample"></a>Uruchamianie przykładu

1. Za pomocą programu Visual Studio Otwórz plik rozwiązania WPFWFIntegration. sln.

2. Aby skompilować rozwiązanie, naciśnij **klawisze Ctrl**+**SHIFT**+**B**.

3. Aby uruchomić rozwiązanie, naciśnij klawisz **F5**.

4. Wpisz swoje imię i nazwisko w oknie dialogowym.

5. Zamknij okno dialogowe, a konsola zwraca nazwę użytkownika.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
