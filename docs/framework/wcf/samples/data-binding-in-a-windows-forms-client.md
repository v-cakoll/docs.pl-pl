---
title: Powiązanie danych w kliencie formularzy systemu Windows
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: a0eaa24cb521dfe4f0d6906d2d8bbbddd3a0d2e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529553"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Powiązanie danych w kliencie formularzy systemu Windows
Niniejszy przykład pokazuje jak powiązać dane zwracane przez usługę Windows Communication Foundation (WCF) w aplikacji Windows Forms.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego artykułu.  
  
 Niniejszy przykład pokazuje usługi, który implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Przykład składa się z klienta aplikacji Windows Forms (.exe), jak i usługi WCF hostowanej przez Internetowe usługi informacyjne (IIS).  
  
 Kontrakt jest definiowany przez `IWeatherService` interfejs, który udostępnia operacji o nazwie `GetWeatherData`. Ta operacja przyjmuje tablicę miasta i zwraca tablicę `WeatherData` obiekty reprezentujące wysokim i niskim prognozowanych temperatury jako uczestnik w mieście.  
  
 Powiązanie danych występuje na komputerze klienckim w aplikacji Windows Forms. Element `DataGridView` jest zdefiniowany w Windows Forms designer, która jest graficzną reprezentację danych. Pośrednik o nazwie `BindingSource` tworzona jest również. Źródło danych `BindingSource` jest ustawiona na tablicę danych zwróconych przez usługę. Celem `BindingSource` ma na celu dostarczenie warstwę pośredni między danymi i widoku danych. Wszystkie interakcje z danymi, takie jak przeglądanie, sortowanie, filtrowanie i aktualizowaniem odbywa się przy użyciu wywołań `BindingSource` składnika. Aby osiągnąć powiązania danych `DataGridView`, `datasource` z `DataGridView` zostanie następnie ustawiona `BindingSource` obiektu. Wszystkie dane zwrócone przez usługę WCF jest następnie wyświetlana graficznie użytkownika.  Za każdym razem, gdy użytkownik kliknie przycisk, zwrócone dane są automatycznie aktualizowane w powiązanych z danymi `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>Zobacz też
