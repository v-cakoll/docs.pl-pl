---
title: "Powiązywanie danych w kliencie programu ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18d133b8eb5bef9e6e9152ef856265c1cbe18b51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-an-aspnet-client"></a>Powiązywanie danych w kliencie programu ASP.NET
W tym przykładzie pokazano, jak można powiązać danych zwróconych przez typowe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] w aplikacji formularzy sieci Web.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie pokazano to usługa, która implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Próbka składa się z aplikacja formularzy sieci Web dostępnych w przeglądarce klienta i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi hostowanej przez Internetowe usługi informacyjne (IIS).  
  
 Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `IWeatherService` interfejsu, który udostępnia operacji o nazwie `GetWeatherData`. Ta operacja akceptuje tablicy miast i zwraca tablicę `WeatherData` obiekty reprezentujące wysoki i niski prognozowanych temperatura miasta.  
  
 Na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] strony .aspx klienta, sieci DataGrid Web definiowana kontrolka, który zawiera graficzną reprezentację danych zwróconych przez usługę. Kod dla wywołań strony .aspx [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi pogody danych i zwraca dane do tablicy `WeatherData` obiektów. DataGrid Określa, gdzie można uzyskać za pomocą przez ustawienie jej `DataSource` właściwości do tej tablicy. Powiązanie danych występuje podczas wywołania do elementu DataGrid `DataBind` metody. Wszystkie ten kod znajduje się wewnątrz.`aspx` strony `Page_Load` metody, aby zawsze użytkownik odświeża stronę przeglądarki, dane jest aktualizowany w elemencie DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Klient ten przykład jest witryną sieci Web, działającą na serwerze sieci Web development. Aby uruchomić serwera wdrożeniowego sieci Web, wpisz następujące polecenie w wierszu polecenia: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Następnie przejdź do http://localhost: 8000/klienta. Aby uruchomić ten przykład na komputerach, należy zastąpić wszystkie odwołania do `localhost` w pliku Web.config klienta z nazwą komputera serwera.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a>Zobacz też
