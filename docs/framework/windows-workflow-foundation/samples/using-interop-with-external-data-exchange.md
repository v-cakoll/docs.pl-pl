---
title: Za pomocą międzyoperacyjności z programem Exchange danych zewnętrznych
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 9571a571137ff0a493be67ee9c607cd46dd47889
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515375"
---
# <a name="using-interop-with-external-data-exchange"></a>Za pomocą międzyoperacyjności z programem Exchange danych zewnętrznych
<xref:System.Activities.Statements.Interop> Działanie może być używane do wykonywania działań z systemu Windows Workflow Foundation (WF) w [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] i [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) i przepływów pracy w programie Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4). W tym przykładzie przedstawiono sposób konfigurowania i uruchamiania WF3 przepływu pracy, który używa <xref:System.Workflow.Activities.ExternalDataExchangeService> (i odpowiednich działań niestandardowych do wywoływania metody i obsługi zdarzeń) przy użyciu <xref:System.Activities.Statements.Interop> działania w WF4 usługi przepływu pracy.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz plik ExternalDataExchange.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Aby samodzielnie tworzyć przykładowy, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić przykład, naciśnij klawisz F5.
