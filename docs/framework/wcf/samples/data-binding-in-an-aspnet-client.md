---
title: Powiązywanie danych w kliencie programu ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: a3d4213729c8025592a756242a6174d7ace63eaa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511647"
---
# <a name="data-binding-in-an-aspnet-client"></a>Powiązywanie danych w kliencie programu ASP.NET
Niniejszy przykład pokazuje jak powiązać dane zwrócone przez typowe usługi Windows Communication Foundation (WCF) w aplikacji formularzy sieci Web.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Niniejszy przykład pokazuje usługi, który implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Przykład składa się z klienta aplikacji formularzy sieci Web jest dostępna z przeglądarki i usługi WCF hostowanej przez Internetowe usługi informacyjne (IIS).  
  
 Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Kontrakt jest definiowany przez `IWeatherService` interfejs, który udostępnia operacji o nazwie `GetWeatherData`. Ta operacja przyjmuje tablicę miasta i zwraca tablicę `WeatherData` obiekty reprezentujące wysokim i niskim prognozowanych temperatury jako uczestnik w mieście.  
  
 Na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] strony .aspx klienta, sieci DataGrid Web zdefiniowano kontrolkę, która zawiera graficzną reprezentację danych zwracanych przez usługę. Kod strony .aspx, wywołuje usługę WCF dla danych o pogodzie i zwraca dane do tablicy `WeatherData` obiektów. DataGrid Określa, gdzie można pobrać danych z przez ustawienie jego `DataSource` właściwości tablicy. Powiązanie danych odbywa się przy użyciu wywołania do DataGrid `DataBind` metody. Cały ten kod znajduje się wewnątrz.`aspx` na stronie `Page_Load` metody, więc w każdym razem, gdy użytkownik odświeża stronę przeglądarki danych jest aktualizowany w elemencie DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Klient ten przykład jest witryny sieci Web, która działa na serwerze sieci Web projektowym. Aby uruchomić serwera wdrożeniowego sieci Web, wpisz następujące polecenie w wierszu polecenia: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Następnie przejdź do http://localhost:8000/client. Aby uruchomić ten przykład, na komputerach, należy zastąpić wszystkie odwołania do `localhost` w pliku Web.config klienta z nazwą komputera serwera.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a>Zobacz też
