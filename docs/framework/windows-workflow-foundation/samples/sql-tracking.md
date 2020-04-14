---
title: Śledzenie SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 72bfcaac2903b3e7fa5679422ad4feaa79e93211
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243183"
---
# <a name="sql-tracking"></a>Śledzenie SQL

W tym przykładzie pokazano, jak napisać niestandardowego uczestnika śledzenia SQL, który zapisuje rekordy śledzenia do bazy danych SQL. Windows Workflow Foundation (WF) zapewnia śledzenie przepływu pracy, aby uzyskać wgląd w wykonywanie wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia emituje rekordy śledzenia przepływu pracy podczas wykonywania przepływu pracy. Aby uzyskać więcej informacji na temat śledzenia przepływu pracy, zobacz [Śledzenie przepływu pracy i śledzenie](../workflow-tracking-and-tracing.md).

## <a name="use-the-sample"></a>Użyj próbki

1. Sprawdź, czy masz zainstalowany program SQL Server 2008, SQL Server 2008 Express lub nowszy. Skrypty spakowane z przykładem zakładają użycie wystąpienia sql express na komputerze lokalnym. Jeśli masz inne wystąpienie, zmodyfikuj skrypty związane z bazą danych przed uruchomieniem przykładu.

2. Utwórz bazę danych śledzenia programu SQL Server, uruchamiając plik Trackingsetup.cmd w katalogu skryptów (\WF\Basic\Tracking\SqlTracking\CS\Scripts). Spowoduje to utworzenie bazy danych o nazwie TrackingSample.

   > [!NOTE]
   > Skrypt tworzy bazę danych w domyślnym wystąpieniu programu SQL Express. Jeśli chcesz zainstalować go w innym wystąpieniu bazy danych, edytuj skrypt Trackingsetup.cmd.

3. Otwórz program SqlTrackingSample.sln w programie Visual Studio 2010.

4. Naciśnij **klawisze Ctrl**+**Shift**+**B,** aby utworzyć rozwiązanie.

5. Naciśnij **klawisz F5,** aby uruchomić aplikację.

   Otworzy się okno przeglądarki i zostanie wyświetle listę katalogów aplikacji.

6. W przeglądarce kliknij pozycję StockPriceService.xamlx.

7. Przeglądarka wyświetla stockpriceservice strony, która zawiera adres WSDL usługi lokalnej. Skopiuj ten adres.

   Przykładem adresu WSDL usługi `http://localhost:65193/StockPriceService.xamlx?wsdl`lokalnej jest .

8. Korzystając z Eksploratora plików, uruchom klienta testowego WCF (WcfTestClient.exe). Znajduje się w *katalogu Programu Microsoft Visual Studio 10.0\Common7\IDE*.

9. W kliencie testowym WCF kliknij menu **Plik** i wybierz polecenie **Dodaj usługę**. Wklej adres usługi lokalnej w skrzynce tekstowej. Kliknij **przycisk OK,** aby zamknąć okno dialogowe.

10. W kliencie testowym WCF kliknij dwukrotnie **getstockprice**. Spowoduje to `GetStockPrice` otwarcie operacji, która przyjmuje `Contoso` jeden parametr, wpisz wartość i kliknij przycisk **Wywołaj**.

11. Emitowane rekordy śledzenia są zapisywane w bazie danych SQL. Aby wyświetlić rekordy śledzenia, otwórz bazę danych TrackingSample w programie SQL Management Studio i przejdź do tabel. Uruchomienie kwerendy wybierającej w tabelach wyświetla dane w rekordach śledzenia przechowywanych w odpowiednich tabelach.

   Aby uzyskać więcej informacji na temat programu SQL Server Management Studio, zobacz [Wprowadzenie programu SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms). Pobierz SQL Server Management Studio [tutaj](https://aka.ms/ssmsfullsetup).

## <a name="uninstall-the-sample"></a>Odinstalowywanie przykładu

1. Uruchom skrypt Trackingingcleanup.cmd w przykładowym katalogu (*\WF\Basic\Tracking\SqlTracking*).

    > [!NOTE]
    > Plik Trackingcleanup.cmd próbuje usunąć bazę danych na komputerze lokalnym SQL Express. Jeśli używasz innego wystąpienia serwera SQL, edytuj plik Trackingcleanup.cmd.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
