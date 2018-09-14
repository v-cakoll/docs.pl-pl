---
title: Za pomocą międzyoperacyjności za pomocą wymiany danych zewnętrznych
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 534321e5b5568e0dd0988333dc98ccc18ff33df8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616315"
---
# <a name="using-interop-with-external-data-exchange"></a>Za pomocą międzyoperacyjności za pomocą wymiany danych zewnętrznych
<xref:System.Activities.Statements.Interop> Działanie może być używane do wykonywania działań z Windows Workflow Foundation (WF) w [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] i [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) i przepływów pracy w programie Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4). W tym przykładzie przedstawiono sposób konfigurowania i uruchamiania WF3 przepływu pracy, który używa <xref:System.Workflow.Activities.ExternalDataExchangeService> (i odpowiednich działań niestandardowych do wywoływania metod i obsługa zdarzeń) przy użyciu <xref:System.Activities.Statements.Interop> działanie w usłudze przepływu pracy WF4.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz plik ExternalDataExchange.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Aby stworzyć próbkę, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić przykład, naciśnij klawisz F5.
