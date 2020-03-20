---
title: Powiązanie danych w kliencie formularzy systemu Windows
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d538e8a525f8d07e9ac9f57d4b10119907602d90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145049"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Powiązanie danych w kliencie formularzy systemu Windows
W tym przykładzie pokazano, jak powiązać dane zwrócone przez usługę Windows Communication Foundation (WCF) w aplikacji Windows Forms.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego artykułu.  
  
 W tym przykładzie pokazano usługę, która implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź. Przykład składa się z aplikacji klienckiej windows forms (exe) i usługi WCF hostowane przez internetowe usługi informacyjne (IIS).  
  
 Kontrakt jest definiowany `IWeatherService` przez interfejs, który `GetWeatherData`udostępnia operację o nazwie . Ta operacja akceptuje tablicę miast i `WeatherData` zwraca tablicę obiektów, które reprezentują wysoką i niską prognozowaną temperaturę dla miasta.  
  
 Powiązanie danych występuje na kliencie w aplikacji Windows Forms. A `DataGridView` jest zdefiniowany w projektancie windows forms, który jest graficzną reprezentacją danych. Tworzony jest `BindingSource` również pośrednik o nazwie. Źródło danych `BindingSource` jest ustawiona na tablicę danych zwracaną przez usługę. Celem jest `BindingSource` zapewnienie warstwy pośredniej między danymi a widokiem danych. Cała interakcja z danymi, na przykład nawigacja, sortowanie, filtrowanie i `BindingSource` aktualizowanie, odbywa się za pomocą wywołań składnika. Aby wykonać powiązanie `DataGridView`danych `datasource` do `DataGridView` , jest `BindingSource` następnie ustawiona na obiekt. Wszystkie dane zwrócone z usługi WCF są następnie wyświetlane graficznie użytkownikowi.  Za każdym razem, gdy użytkownik kliknie przycisk, zwrócone `DataGridView`dane są automatycznie aktualizowane w pliku danych.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
