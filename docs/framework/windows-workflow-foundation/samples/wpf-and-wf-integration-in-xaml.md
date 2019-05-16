---
title: Integracja WPF i WF w języku XAML
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 2e5387186be2006c2c6c3e14e7000a21ed88140f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639094"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>Integracja WPF i WF w języku XAML
W tym przykładzie pokazano, jak utworzyć aplikację, która korzysta z funkcji Windows Presentation Foundation (WPF) i Windows Workflow Foundation (WF) w jednym dokumencie XAML. Aby to osiągnąć, w przykładzie użyto rozszerzalności Windows Workflow Foundation (WF) i XAML.

## <a name="sample-details"></a>Przykład szczegółów
 Plik ShowWindow.xaml deserializuje do <xref:System.Activities.Statements.Sequence> działanie przy użyciu dwóch zmiennych ciągu, które są zmieniane przez działania w sekwencji: `ShowWindow` i `WriteLine`. <xref:System.Activities.Statements.WriteLine> Dane wyjściowe działania, w oknie konsoli wyrażenie, które przypisuje do <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości. `ShowWindow` Wyświetla działania [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] okna jako część swojej logiki wykonywania. <xref:System.Activities.ActivityContext.DataContext%2A> Okna zawiera zmienne zadeklarowane w sekwencji. Formanty okna zadeklarowanych w `ShowWindow` działania używać powiązanie danych do manipulowania tych zmiennych. Na koniec okno zawiera formant przycisku. `Click` Zdarzeń dla przycisku jest obsługiwany przez <xref:System.Activities.ActivityDelegate> o nazwie `MarkupExtension` zawierający `CloseWindow` działania. `MarkUpExtension` wywołuje zawarte działanie, który zawiera, jako kontekst, wszystkie obiekty określone przez `x:Name`, jak również <xref:System.Activities.ActivityContext.DataContext%2A> okna nadrzędnego. W efekcie `CloseWindow.InArgument<Window>` może być powiązana, za pomocą wyrażenia, który odwołuje się do nazwy okna.

 `ShowWindow` Pochodzi od klasy działania <xref:System.Activities.AsyncCodeActivity%601> klasy, aby wyświetlić [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] okna i kończy po zamknięciu okna. `Window` Właściwość jest typu `Func<Window>` umożliwiająca okna, które ma zostać utworzony na żądanie dla każdego wykonania działania. `Window` Używa właściwości <xref:System.Xaml.XamlDeferringLoader> umożliwiające tego modelu do oceny odroczonej. `FuncFactoryDeferringLoader` Umożliwia `XamlReader` przechwycone podczas serializacji i odczytania ich podczas wykonywania działania.

 Dobrze napisane działania nigdy nie blokuje wątku harmonogramu. Jednak `ShowWindow` działania nie można ukończyć przed zamknięciem okna, okno. `ShowWindow` Działania osiąga to zachowanie, wynikające z <xref:System.Activities.AsyncCodeActivity>, wywoływania <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> method in Class metoda <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metoda i wyświetlanie trybie modalnym oknie. Obiekt delegowany jest wywoływany przy użyciu WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>. `ShowWindow` Przypisuje działania <xref:System.Activities.ActivityContext.DataContext%2A> właściwość `Window.DataContext` właściwość Podaj wszystkie możliwie dane powiązane służy do sterowania dostępem do zmiennych w zakresie.

 Ostatniego punktu orientacyjnego w tym przykładzie jest <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> o nazwie `DelegateActivityExtension`. `ProvideValue` Metoda tego rozszerzenia znacznika zwraca delegat, który wywołuje działanie osadzonych. To działanie jest uruchamiany w środowisku zawierającym [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] kontekstu danych i wszystkie `x:Name` wartości w zakresie. W `GenericInvoke` , to środowisko jest podana metoda działania za pośrednictwem <xref:System.Activities.Hosting.SymbolResolver> rozszerzenia. To rozszerzenie jest dodawany do <xref:System.Activities.WorkflowInvoker> następnie używany do wywołania osadzone działanie w każdym przypadku, gdy rozszerzenie znaczników obiekt delegowany jest wywoływany.

> [!NOTE]
>  Projektant domyślny nie obsługuje działania ShowWindow; w efekcie plik ShowWindow.Xaml nie są wyświetlane poprawnie w projektancie.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania WPFWFIntegration.sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

4. Wpisz swoje imię i nazwisko do okna dialogowego.

5. Zamknij okno dialogowe i konsolę zwraca nazwę.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
