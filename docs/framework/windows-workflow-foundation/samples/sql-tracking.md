---
title: "Śledzenie SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dcffb306c8466e63e0d5888c91d5f6015845d81c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="sql-tracking"></a>Śledzenie SQL
W tym przykładzie pokazano, jak pisać niestandardowe uczestnika śledzenia SQL, który zapisuje śledzenie rekordów bazy danych SQL. [!INCLUDE[wf](../../../../includes/wf-md.md)]udostępnia śledzenia wgląd we wykonywania wystąpienia przepływu pracy przepływu pracy. Środowisko uruchomieniowe śledzenia emituje przepływu pracy śledzenia rekordów podczas wykonywania przepływu pracy. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]przepływ pracy śledzenia, zobacz [przepływu pracy śledzenia i śledzenia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Sprawdź, zainstalowany jest program SQL Server 2008, SQL Server 2008 Express lub nowszej. Skrypty z przykładowej założono korzystanie z wystąpienia programu SQL Express na komputerze lokalnym. Jeśli masz inne wystąpienie Zmodyfikuj skrypty związanych z bazy danych przed uruchomieniem próbki.  
  
2.  Utwórz bazę danych śledzenia programu SQL Server, uruchamiając Trackingsetup.cmd w katalogu skryptów (\WF\Basic\Tracking\SqlTracking\CS\Scripts). Spowoduje to utworzenie bazy danych o nazwie TrackingSample.  
  
    > [!NOTE]
    >  Skrypt tworzy bazy danych w domyślnym wystąpieniu programu SQL Express. Jeśli użytkownik chce go zainstalować na wystąpieniu innej bazy danych, zmodyfikuj plik skryptu Trackingsetup.cmd.  
  
3.  Otwórz SqlTrackingSample.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
5.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Oknie przeglądarki zostanie otwarty i zawiera katalog zawierający informacje o aplikacji.  
  
6.  W przeglądarce kliknij przycisk StockPriceService.xamlx.  
  
7.  W przeglądarce pojawi się stronie StockPriceService zawiera Usługa lokalna adres WSDL. Skopiuj ten adres.  
  
     Przykładem usługa lokalna adres WSDL jest http://localhost:65193/StockPriceService.xamlx?wsdl.  
  
8.  Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], uruchomić klienta testowego WCF (WcfTestClient.exe). Znajduje się w katalogu 10.0\Common7\IDE programu Microsoft Visual Studio.  
  
9. W kliencie testowym WCF, kliknij przycisk **pliku** menu i wybierz **Dodaj usługę**. Wklej adres usługi lokalnej w polu tekstowym. Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
10. W kliencie testowym WCF, kliknij dwukrotnie **GetStockPrice**. Spowoduje to otwarcie `GetStockPrice` operacja, która przyjmuje jeden parametr typu w wartości `Contoso` i kliknij przycisk **Invoke**.  
  
11. Rejestruje emitowany śledzenia są zapisywane do bazy danych SQL. Aby wyświetlić rekordy śledzenia, należy otworzyć TrackingSample bazy danych w programie SQL Management Studio i przejdź do tabel. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SQL Server Management Studio, zobacz [wprowadzenie do programu SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express można pobrać [tutaj](http://go.microsoft.com/fwlink/?LinkId=180520). Uruchamianie zapytania select w tabelach wyświetla dane przechowywane w tabelach odpowiednie rekordy śledzenia.  
  
#### <a name="to-uninstall-the-sample"></a>Aby odinstalować próbki  
  
1.  Uruchom skrypt theTrackingcleanup.cmd w katalogu próbki (\WF\Basic\Tracking\SqlTracking).  
  
    > [!NOTE]
    >  Trackingcleanup.cmd próbuje usunąć bazę danych programu SQL Express komputera lokalnego. Jeśli korzystasz z innego wystąpienia programu SQL server, należy edytować Trackingcleanup.cmd.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
