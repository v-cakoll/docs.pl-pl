---
title: Programowanie magazynu metadanych
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 6efcb86e29f19a29d6ef382afa336d0ca2ce4306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-store-programmability"></a>Programowanie magazynu metadanych
Magazyn metadanych jest [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] typy funkcji, która umożliwia skojarzenie dowolnego metadane w formie atrybuty CLR w czasie wykonywania. Dzięki temu luźne powiązanie między składniki wykonawcze i ich odpowiedniki czasu projektowania, a także możliwość zmiany składniki czasu projektowania bez wpływu na środowisko uruchomieniowe. Przykładzie pokazano, jak program względem magazynu metadanych przez stosowanie atrybutów do typu run-time, źródło, dla którego mamy żadnej kontroli nad. Zwykle terminologii jest, że aplikacji obsługującej rejestruje metadanych dla zestawu typów.  
  
 W danych wyjściowych, mogą pojawić się dodatkowe, nieoczekiwany atrybut <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`. To jest dodawany przy użyciu metadanych interfejsu API i nie ma wpływu na działanie próbki.  
  
 W tym przykładzie przedstawiono:  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Atrybut iniekcji przy użyciu metadanych przechowywać interfejsu API.  
  
-   Odroczenie metadanych rejestracji przy użyciu mechanizmu wywołania zwrotnego.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ProgrammingMetadataStore.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`