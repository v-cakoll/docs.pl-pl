---
title: Programowalność Store metadanych
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 9f30fcdac131b8749a4d165875b9bbb584542843
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562707"
---
# <a name="metadata-store-programmability"></a>Programowalność Store metadanych
Magazyn metadanych jest [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] funkcja, która umożliwia skojarzenie dowolnego metadanych w formie atrybuty CLR typów w czasie wykonywania. Pozwala to na tym luźne powiązanie składniki czasu wykonywania i ich odpowiedniki w czasie projektowania, a także możliwość zmiany składniki czasu projektowania, bez wywierania wpływu na środowiska uruchomieniowego. Przykład pokazuje, jak programować przy użyciu magazynu metadanych przez zastosowanie atrybutów do typu run-time, źródło, dla którego mamy żadnej kontroli nad. Zazwyczaj terminologią to, że aplikacji macierzystej rejestruje metadanych dla zestawu typów.  
  
 W danych wyjściowych, możesz zauważyć atrybut dodatkowa, Nieoczekiwana <xref:System.Runtime.InteropServices.GuidAttribute>. To jest dodawany, gdy za pomocą interfejsu API metadanych i nie ma wpływu na uruchomione próbki.  
  
 W tym przykładzie przedstawiono:  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Iniekcja atrybutu przy użyciu metadanych przechowywać interfejsu API.  
  
-   Przy użyciu mechanizmu wywołania zwrotnego, które mają być odroczone rejestracji metadane.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ProgrammingMetadataStore.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`