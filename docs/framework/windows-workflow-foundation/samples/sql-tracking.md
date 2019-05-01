---
title: Śledzenie SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: f3c48b40e2d3d7dec2b9008b3de738f9b2983610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785921"
---
# <a name="sql-tracking"></a>Śledzenie SQL
W tym przykładzie pokazano, jak napisać uczestnikiem niestandardowe śledzenia SQL, który zapisuje rekordy śledzenia bazą danych SQL. Windows Workflow Foundation (WF) zapewnia wgląd w wykonywania wystąpienia przepływu pracy śledzenia przepływu pracy. Środowisko uruchomieniowe śledzenia emituje przepływu pracy śledzenia rekordów podczas wykonywania przepływu pracy. Aby uzyskać więcej informacji na temat śledzenia przepływu pracy, zobacz [przepływu pracy i śledzenie](../workflow-tracking-and-tracing.md).

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Sprawdź, zainstalowany jest program SQL Server 2008, SQL Server 2008 Express lub nowszej. Skrypty w pakiecie z przykładem założono korzystanie z wystąpienia programu SQL Express na komputerze lokalnym. Jeśli masz inne wystąpienie, zmodyfikuj skrypty związane z bazy danych przed uruchomieniem przykładu.

2. Utwórz bazę danych śledzenia programu SQL Server, uruchamiając Trackingsetup.cmd w katalogu skryptów (\WF\Basic\Tracking\SqlTracking\CS\Scripts). Spowoduje to utworzenie bazy danych o nazwie TrackingSample.

    > [!NOTE]
    >  Skrypt tworzy bazę danych w domyślnym wystąpieniu programu SQL Express. Jeśli chcesz zainstalować je na inne wystąpienie bazy danych, zmodyfikuj skrypt Trackingsetup.cmd.  
  
3. Otwórz SqlTrackingSample.sln w programie Visual Studio 2010.  
  
4. Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
5. Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Okno przeglądarki otwiera i pokazuje katalog zawierający informacje o aplikacji.  
  
6. W przeglądarce kliknij przycisk StockPriceService.xamlx.  
  
7. W przeglądarce pojawi się stronie StockPriceService zawiera usługę lokalnego adresu WSDL. Skopiuj ten adres.  
  
     Na przykład adres WSDL Usługa lokalna `http://localhost:65193/StockPriceService.xamlx?wsdl`.  
  
8. Za pomocą [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], uruchom klienta testowego WCF (WcfTestClient.exe). Znajduje się on w katalogu programu Microsoft Visual Studio 10.0\Common7\IDE.  
  
9. W kliencie testowym WCF kliknij **pliku** menu, a następnie wybierz **Dodaj usługę**. Wklej adres lokalnej usługi w polu tekstowym. Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
10. W kliencie testowym WCF, kliknij dwukrotnie **GetStockPrice**. Spowoduje to otwarcie `GetStockPrice` operacji, która przyjmuje jeden parametr, typ wartości `Contoso` i kliknij przycisk **Invoke**.  
  
11. Rekordów emitowany śledzenia są zapisywane w bazie danych SQL. Aby wyświetlić rekordy śledzenia, należy otworzyć TrackingSample bazy danych w programie SQL Management Studio i przejdź do tabel. Aby uzyskać więcej informacji na temat programu SQL Server Management Studio, zobacz [wprowadzenie do programu SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express można pobrać [tutaj](https://go.microsoft.com/fwlink/?LinkId=180520). Uruchamianie zapytania select w tabelach wyświetla dane przechowywane w tabelach odpowiednich rekordów śledzenia.  
  
#### <a name="to-uninstall-the-sample"></a>Aby odinstalować próbki  
  
1. Uruchom skrypt theTrackingcleanup.cmd w katalogu próbki (\WF\Basic\Tracking\SqlTracking).  
  
    > [!NOTE]
    >  Trackingcleanup.cmd próbuje usunąć bazę danych programu SQL Express komputera lokalnego. Jeśli używasz innego wystąpienia programu SQL server, należy edytować Trackingcleanup.cmd.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
