---
title: Powiązanie danych w kliencie formularzy systemu Windows
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: 38991390f2d0dd272b8d07041b61e6cf16db0cae
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="data-binding-in-a-windows-forms-client"></a>Powiązanie danych w kliencie formularzy systemu Windows
W tym przykładzie pokazano, jak można powiązać z danymi zwróconymi przez usługę Windows Communication Foundation (WCF) w aplikacji formularzy systemu Windows.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego artykułu.  
  
 W przykładzie pokazano to usługa, która implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Próbka składa się z klienta aplikacji formularzy systemu Windows (.exe) i usługi WCF hostowanej przez Internetowe usługi informacyjne (IIS).  
  
 Kontrakt jest definiowana za pomocą `IWeatherService` interfejsu, który udostępnia operacji o nazwie `GetWeatherData`. Ta operacja akceptuje tablicy miast i zwraca tablicę `WeatherData` obiekty reprezentujące wysoki i niski prognozowanych temperatura miasta.  
  
 Powiązanie danych występuje na komputerze klienckim w aplikacji formularzy systemu Windows. A `DataGridView` jest zdefiniowany w narzędziu Projektant dla formularzy systemu Windows, czyli graficzną reprezentację danych. Pośrednik o nazwie `BindingSource` tworzona jest również. Źródło danych `BindingSource` ma ustawioną wartość tablicy danych zwróconych przez usługę. Celem `BindingSource` jest zapewnienie warstwę pośredni między danymi i widoku danych. Wszystkie interakcje z danymi, takich jak przeglądanie, sortowanie, filtrowanie i aktualizowanie, jest realizowane za pomocą wywołania `BindingSource` składnika. Powiązywanie danych do celu `DataGridView`, `datasource` z `DataGridView` następnie ustawiono `BindingSource` obiektu. Wszystkie dane zwrócone z usługi WCF zebrane graficznie dla użytkownika.  Za każdym razem, gdy użytkownik kliknie przycisk, zwrócone dane są automatycznie aktualizowane w powiązanym z danymi `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>Zobacz też
