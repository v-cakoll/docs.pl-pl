---
title: Działanie Waitforinput
ms.date: 03/30/2017
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
ms.openlocfilehash: 2e878e8c91c5da12a68da848694ce790896517c7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741175"
---
# <a name="wait-for-input-activity"></a>Działanie Waitforinput
W tym przykładzie pokazano, jak utworzyć nazwany zakładki w przepływie pracy. Windows Workflow Foundation (WF) nie zapewnia działanie tworzenia deklaratywne zakładki. W związku z tym gdy chcesz utworzyć zakładkę w przepływie pracy można napisać niestandardowe działanie, które tworzy go. `WaitForInput` Działanie zdefiniowane w tym przykładzie oferuje tę funkcję, dzięki czemu użytkownicy mogą tworzyć zakładki deklaratywnie w przepływie pracy.  
  
## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie  
  
|**Nazwa projektu**|**Opis**|**Pliki główne**|  
|-|-|-|  
|WaitForInput|Zawiera `WaitForInput` działanie i jego projektanta|WaitForInput.cs<br /><br /> `WaitForInput` definicji działania.|  
|||WaitForInputDesigner.xaml<br /><br /> Projektant niestandardowe `WaitForInput` działania.|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> Używane do aktualizowania typu ogólnego działania w Projektancie konwertera typów WPF.|  
|WaitForInputTestClient|Przykładowa aplikacja kliencka, konfiguruje, która uruchamia przepływ pracy, używając kilku działań WaitForInput za pomocą projektanta przepływów pracy.|Sequence1.XAML<br /><br /> Sekwencyjny przepływ pracy, który używa `WaitForInput` działania.|  
|||Program.cs<br /><br /> Uruchamia wystąpienie przepływu pracy zdefiniowane w Sequence1.xaml.|  
  
## <a name="waitforinput-activity"></a>Działanie WaitForInput  
 `WaitForInput` Działanie tworzy nazwany zakładkę w przepływie pracy. Zakładka oczekuje na sygnał i odbiera dane typu skonfigurowany. Po wznowieniu zakładki dane przekazane do przepływu pracy jest dostępna za pośrednictwem `Result` właściwości.  
  
 `WaitForInput` Pochodzi od klasy działania <xref:System.Activities.NativeActivity> klasy, ponieważ musi utworzyć zakładki, które są dostępne za pośrednictwem jedynie <xref:System.Activities.NativeActivityContext> klasy.  
  
 Działanie ma trzy atrybuty dla powiązania projektanta, dodając argument rodzajowy funkcji, które mogą być aktualizowane i ustawienie domyślnego ogólnego typu ciąg. Działanie ma również argumenty wymienione w poniższej tabeli.  
  
|**Nazwa**|**Typ**|**Opis**|  
|-|-|-|  
|TResult|Argument ogólny (TResult)|Typ zakładki. Jest to typ danych, które mają być przekazane do zakładki po wznowieniu.|  
|Nazwa_zakładki|InArgument\<ciąg >|Nazwa zakładki.|  
|Wynik|InArgument\<TResult >|Dane przekazywane do działania po wznowieniu zakładki.|  
  
## <a name="waitforinput-activity-designer"></a>Projektant działanie WaitForInput  
 `WaitForInput` Projektanta działań jest zaimplementowana w pliku WaitForInputDesigner.xaml. `WaitForInput` Działanie i jego projektanta znajdują się w tym samym zestawie. Pokazano grafiki `WaitForInput` działania w przyborniku, w ramach danej kategorii, która ma taką samą nazwę jak zestawu.  
  
 ![Zrzut ekranu z przybornika WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 Pokazano grafiki `WaitForInput` projektanta. Ponieważ, `WaitForInput` aktywności jest bardzo proste, Projektant umożliwia ustawienie wszystkie argumenty bezpośrednio na powierzchni projektowej.  
  
 ![Projektant działań WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik WaitForInput.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić przykład, bez debugowania, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`