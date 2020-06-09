---
title: Używanie liczników wydajności
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 0b63cdc145ff8806c26b255500bcb2a132e9ef9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596503"
---
# <a name="using-performance-counters"></a>Używanie liczników wydajności
W tym przykładzie pokazano, jak uzyskać dostęp do liczników wydajności Windows Communication Foundation (WCF) oraz jak tworzyć liczniki wydajności zdefiniowane przez użytkownika. Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie klient wywołuje cztery metody `ICalculator` usługi. Klient kontynuuje działanie, dopóki nie zostanie on przerwany przez użytkownika. Usługa pozostaje niezmieniona.  
  
 Liczniki wydajności są włączane w sekcji Diagnostyka w pliku Web. config dla usługi, jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 To zadanie można również wykonać za pomocą [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Po włączeniu liczników wydajności cały pakiet liczników wydajności programu WCF jest włączony dla usługi. .NET Framework automatycznie utrzymuje dane dotyczące wydajności na trzech poziomach: `ServiceModelService` , `ServiceModelEndpoint` i `ServiceModelOperation` . Każdy z tych poziomów ma liczniki wydajności, takie jak "wywołania", "wywołania na sekundę" i "wywołania zabezpieczeń, które nie są autoryzowane".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Aby wyświetlić dane wydajności  
  
1. Uruchom narzędzie Monitor wydajności, klikając przycisk **Start**, **Uruchom polecenie...**, wprowadź `perfmon` i kliknij przycisk **OK,** lub z panelu sterowania wybierz pozycję **Narzędzia administracyjne** , a następnie kliknij dwukrotnie pozycję **wydajność**.  
  
    > [!NOTE]
    > Nie można dodać liczników do momentu uruchomienia przykładowego kodu.  
  
2. Usuń liczniki wydajności, które znajdują się na liście, zaznaczając je i naciskając klawisz Delete.  
  
3. Dodaj liczniki WCF, klikając prawym przyciskiem myszy okienko wykresu i wybierając polecenie **Dodaj liczniki**. W oknie dialogowym **Dodawanie liczników** wybierz pozycję **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 lub ServiceModelService 3.0.0.0** w polu listy rozwijanej obiekt wydajności. Wybierz liczniki, które chcesz wyświetlić z listy.  
  
    > [!NOTE]
    > Brak liczników wydajności programu WCF dla usługi, jeśli na komputerze nie są uruchomione żadne usługi WCF.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Aby włączyć liczniki przy użyciu edytora konfiguracji  
  
1. Otwórz wystąpienie programu SvcConfigEditor. exe.  
  
2. W menu plik kliknij polecenie **Otwórz** , a następnie kliknij pozycję **plik konfiguracji..**..  
  
3. Przejdź do folderu usługi przykładowej aplikacji i Otwórz plik Web. config.  
  
4. W drzewie konfiguracji kliknij pozycję **Diagnostyka** .  
  
5. Przełącz **licznik wydajności** w oknie **Diagnostyka** , aby pokazać opcję "wszystkie".  
  
6. Zapisz plik konfiguracji i Zamknij Edytor.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
