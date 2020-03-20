---
title: Powiązywanie danych w kliencie programu ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c068c1cab5a5b9dad75e781e58076f4066a3b2a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145010"
---
# <a name="data-binding-in-an-aspnet-client"></a>Powiązywanie danych w kliencie programu ASP.NET
W tym przykładzie pokazano, jak powiązać dane zwrócone przez typową usługę Windows Communication Foundation (WCF) w aplikacji formularzy sieci Web.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie pokazano usługę, która implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź. Przykład składa się z aplikacji formularzy sieci Web klienta dostępne z przeglądarki i usługi WCF hostowane przez internetowych usług informacyjnych (IIS).  
  
 Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowany `IWeatherService` przez interfejs, który `GetWeatherData`udostępnia operację o nazwie . Ta operacja akceptuje tablicę miast i `WeatherData` zwraca tablicę obiektów, które reprezentują wysoką i niską prognozowaną temperaturę dla miasta.  
  
 Na stronie ASP.NET client .aspx zdefiniowano formant sieci Web DataGrid, który zawiera graficzną reprezentację danych zwracanych przez usługę. Kod na stronie .aspx wywołuje usługę WCF dla danych pogodowych `WeatherData` i zwraca dane do tablicy obiektów. DataGrid określa, skąd ma być można `DataSource` uzyskać jego dane, ustawiając jego właściwość do tej tablicy. Powiązanie danych występuje z wywołaniem Metody `DataBind` DataGrid. Cały ten kod znajduje się wewnątrz pliku .`aspx` `Page_Load` metody strony, więc za każdym razem, gdy użytkownik odświeża stronę przeglądarki, dane są aktualizowane w DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Ten przykładowy klient jest witryną sieci Web, która działa w ramach programu rozwoju serwera sieci Web. Aby uruchomić programowy serwer sieci Web, w `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`wierszu polecenia wpisz następujące polecenie: . Następnie przejdź `http://localhost:8000/client`do pliku . Aby uruchomić ten przykład na różnych `localhost` komputerach, zastąp wszystkie odwołania do pliku Web.config klienta nazwą komputera serwera.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
