---
title: "Powiązanie danych w kliencie formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b78cfbd63687fc7288c945ebcbec790150efed61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a>Powiązanie danych w kliencie formularzy systemu Windows
W tym przykładzie pokazano sposób powiązania danych zwróconych przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] w aplikacji formularzy systemu Windows.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego artykułu.  
  
 W przykładzie pokazano to usługa, która implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Próbka składa się z klienta aplikacji formularzy systemu Windows (.exe) i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi hostowanej przez Internetowe usługi informacyjne (IIS).  
  
 Kontrakt jest definiowana za pomocą `IWeatherService` interfejsu, który udostępnia operacji o nazwie `GetWeatherData`. Ta operacja akceptuje tablicy miast i zwraca tablicę `WeatherData` obiekty reprezentujące wysoki i niski prognozowanych temperatura miasta.  
  
 Powiązanie danych występuje na komputerze klienckim w aplikacji formularzy systemu Windows. A `DataGridView` jest zdefiniowany w narzędziu Projektant dla formularzy systemu Windows, czyli graficzną reprezentację danych. Pośrednik o nazwie `BindingSource` tworzona jest również. Źródło danych `BindingSource` ma ustawioną wartość tablicy danych zwróconych przez usługę. Celem `BindingSource` jest zapewnienie warstwę pośredni między danymi i widoku danych. Wszystkie interakcje z danymi, takich jak przeglądanie, sortowanie, filtrowanie i aktualizowanie, jest realizowane za pomocą wywołania `BindingSource` składnika. Powiązywanie danych do celu `DataGridView`, `datasource` z `DataGridView` następnie ustawiono `BindingSource` obiektu. Wszystkie dane zwrócone w wyniku [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] graficznie zebrane usługi dla użytkownika.  Za każdym razem, gdy użytkownik kliknie przycisk, zwrócone dane są automatycznie aktualizowane w powiązanym z danymi `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>Zobacz też
