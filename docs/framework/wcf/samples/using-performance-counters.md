---
title: Używanie liczników wydajności
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 2c5042d497a09984a6f6c398a943b443ee9aafb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007607"
---
# <a name="using-performance-counters"></a>Używanie liczników wydajności
Niniejszy przykład pokazuje sposób dostępu do liczników wydajności usługi Windows Communication Foundation (WCF) oraz tworzenie liczników wydajności zdefiniowanych przez użytkownika. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W tym przykładzie, gdy klient wywołuje cztery metody `ICalculator` usługi. Klient w dalszym ciągu to zrobić, dopóki nie zostanie przerwane przez użytkownika. Usługa pozostaje bez zmian.  
  
 Liczniki wydajności są włączone w sekcji Diagnostyka w pliku Web.config dla usługi, jak pokazano w poniższym Przykładowa konfiguracja.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 To zadanie można również wykonać przy użyciu [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Jeśli liczniki wydajności są włączone, cały zestaw liczników wydajności programu WCF jest włączone dla usługi. .NET Framework automatycznie przechowuje dane dotyczące wydajności na trzech poziomach: `ServiceModelService`, `ServiceModelEndpoint` i `ServiceModelOperation`. Każda z tych poziomów ma liczników wydajności, takich jak "Wywołania", "Wywołania na sekundę" i "Zabezpieczenia połączeń nie masz praw".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Aby wyświetlić dane dotyczące wydajności  
  
1. Uruchom narzędzie monitora wydajności, klikając **Start**, **uruchamianie...** , wprowadź `perfmon` i kliknij przycisk **OK** lub z poziomu Panelu sterowania wybierz **narzędzia administracyjne** i kliknij dwukrotnie **wydajności**.  
  
    > [!NOTE]
    >  Nie można dodać liczniki, dopóki nie zostanie uruchomiony w przykładowym kodzie.  
  
2. Usuń liczniki wydajności, które są wyświetlane, zaznaczając je i naciskając klawisz Delete.  
  
3. Dodaj liczniki WCF, klikając prawym przyciskiem myszy okienko Wykres i wybierając **Dodaj liczniki**. W **Dodaj liczniki** okno dialogowe, wybierz opcję **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 lub ServiceModelService 3.0.0.0** w obiekcie wydajności polu listy rozwijanej listy. Wybierz liczniki, które mają być wyświetlane na liście.  
  
    > [!NOTE]
    >  Istnieją nie liczniki wydajności programu WCF dla usługi, jeśli brak usług WCF uruchomionego na komputerze.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Aby włączyć liczniki za pomocą edytora konfiguracji  
  
1. Otwórz wystąpienie SvcConfigEditor.exe.  
  
2. W menu Plik kliknij polecenie **Otwórz** a następnie kliknij przycisk **pliku konfiguracji...** .  
  
3. Przejdź do folderu usługi przykładową aplikację i Otwórz plik Web.config.  
  
4. Kliknij przycisk **diagnostyki** drzewa konfiguracji.  
  
5. Przełącz **licznika wydajności** w **diagnostyki** okna, aby pokazać "All".  
  
6. Zapisz plik konfiguracji, a następnie zamknij Edytor.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
