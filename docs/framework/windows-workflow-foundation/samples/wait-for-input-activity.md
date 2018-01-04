---
title: "Poczekaj, aż działania wejściowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac05054d56c424ab3f4d1fdfd9c3590aac8b00bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wait-for-input-activity"></a>Poczekaj, aż działania wejściowego
Ten przykład przedstawia sposób tworzenia zakładek o nazwie w przepływie pracy. [!INCLUDE[wf](../../../../includes/wf-md.md)]nie zapewnia działanie tworzenia deklaratywne zakładki. W związku z tym jeśli chcesz utworzyć zakładkę w przepływie pracy, należy napisać działania niestandardowego, który go utworzył. `WaitForInput` Działanie zdefiniowane w tym przykładzie zapewnia tę funkcję, dzięki czemu użytkownicy mogą tworzyć zakładki deklaratywnie w przepływie pracy.  
  
## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie  
  
|**Nazwa projektu**|**Opis**|**Główne pliki**|  
|-|-|-|  
|WaitForInput|Zawiera `WaitForInput` działanie i jego projektanta|WaitForInput.cs<br /><br /> `WaitForInput`definicji działania.|  
|||WaitForInputDesigner.xaml<br /><br /> Projektant niestandardowych `WaitForInput` działania.|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> Konwerter typów WPF używane do aktualizowania typu ogólnego działania w projektancie.|  
|WaitForInputTestClient|Przykładowej aplikacji klienta, który konfiguruje i uruchamia przepływ pracy przy użyciu kilku działań WaitForInput za pomocą projektanta przepływów pracy.|Sequence1.XAML<br /><br /> Sekwencyjny przepływ pracy, który używa `WaitForInput` działania.|  
|||Plik program.CS<br /><br /> Uruchomione jest wystąpienie przepływu pracy zdefiniowane w Sequence1.xaml.|  
  
## <a name="waitforinput-activity"></a>Działanie WaitForInput  
 `WaitForInput` Działanie tworzy zakładki o nazwie w przepływie pracy. Zakładka oczekuje na sygnał i odbiera dane skonfigurowanego typu elementu. Po wznowieniu działania zakładki dane przekazywane do przepływu pracy są dostępne za pośrednictwem `Result` właściwości.  
  
 `WaitForInput` Działania jest pochodną <xref:System.Activities.NativeActivity> klasy, ponieważ należy utworzyć zakładki, które są dostępne za pośrednictwem jedynie <xref:System.Activities.NativeActivityContext> klasy.  
  
 Działanie ma trzy atrybuty zastosować dla niego powiązanie projektanta, dodaniu funkcji argumentów ogólnych, które mogą być aktualizowane i ustawienie typu ogólnego domyślnego ciągu. Działanie ma również argumenty wymienione w poniższej tabeli.  
  
|**Nazwa**|**Typ**|**Opis**|  
|-|-|-|  
|TResult|Argument rodzajowy (TResult)|Typ zakładki. Jest to typ danych do przekazania do zakładki po wznowieniu.|  
|Nazwa zakładki|InArgument\<ciąg >|Nazwa zakładki.|  
|Wynik|InArgument\<TResult >|Dane przekazywane do działania, po wznowieniu działania zakładki.|  
  
## <a name="waitforinput-activity-designer"></a>Projektant działań WaitForInput  
 `WaitForInput` Projektant działań jest zaimplementowana w pliku WaitForInputDesigner.xaml. `WaitForInput` Działanie i jego projektanta znajdują się w tym samym zestawie. Poniżej przedstawiono graficzne `WaitForInput` działania w przyborniku kategorii, który ma taką samą nazwę jak zestawu.  
  
 ![Zrzut ekranu przybornika WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 Poniżej przedstawiono graficzne `WaitForInput` projektanta. Ponieważ, `WaitForInput` działanie jest bardzo proste, projektanta pozwala na ustawienie wszystkie argumenty bezpośrednio w powierzchnię projektanta.  
  
 ![Projektant działań WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik WaitForInput.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby rozpocząć próbki bez debugowania, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`