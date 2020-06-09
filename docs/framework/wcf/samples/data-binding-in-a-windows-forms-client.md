---
title: Powiązanie danych w kliencie formularzy systemu Windows
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d2784c86bc3ef84f99f4731f441019b3f568b321
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575488"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Powiązanie danych w kliencie formularzy systemu Windows
Ten przykład pokazuje, jak powiązać dane zwrócone przez usługę Windows Communication Foundation (WCF) w aplikacji Windows Forms.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego artykułu.  
  
 Ten przykład pokazuje usługę implementującą kontrakt, który definiuje wzorzec komunikacji z odpowiedzią na żądanie. Przykład składa się z klienta Windows Forms aplikacji (exe) i usługi WCF hostowanej przez Internet Information Services (IIS).  
  
 Kontrakt jest definiowany przez `IWeatherService` interfejs, który uwidacznia operację o nazwie `GetWeatherData` . Ta operacja akceptuje tablicę miast i zwraca tablicę `WeatherData` obiektów, która reprezentuje górną i niską prognozę dla miasta.  
  
 Powiązanie danych odbywa się na kliencie w aplikacji Windows Forms. A `DataGridView` jest zdefiniowany w projektancie Windows Forms, który jest graficzną reprezentacją danych. `BindingSource`Tworzony jest również pośrednik o nazwie. Źródło danych `BindingSource` jest ustawione na tablicę danych zwracaną przez usługę. Celem `BindingSource` jest zapewnienie warstwy pośredniej między danymi a widokiem danych. Wszystkie interakcje z danymi, takie jak nawigowanie, sortowanie, filtrowanie i aktualizowanie, są realizowane przy użyciu wywołań do `BindingSource` składnika. Aby wykonać powiązanie danych z `DataGridView` `datasource` `DataGridView` obiektem, jest on następnie ustawiany dla `BindingSource` obiektu. Wszystkie dane zwrócone przez usługę WCF są następnie wyświetlane graficznie dla użytkownika.  Za każdym razem, gdy użytkownik kliknie przycisk, zwrócone dane są automatycznie aktualizowane w powiązane dane `DataGridView` .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
