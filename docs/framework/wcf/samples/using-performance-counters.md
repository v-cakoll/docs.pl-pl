---
title: Używanie liczników wydajności
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143580"
---
# <a name="using-performance-counters"></a>Używanie liczników wydajności
W tym przykładzie pokazano, jak uzyskać dostęp do liczników wydajności programu Windows Communication Foundation (WCF) i jak tworzyć liczniki wydajności zdefiniowane przez użytkownika. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie klient wywołuje cztery `ICalculator` metody usługi. Klient kontynuuje to, dopóki nie zostanie przerwany przez użytkownika. Usługa pozostaje niezmieniona.  
  
 Liczniki wydajności są włączone w sekcji diagnostyki pliku Web.config dla usługi, jak pokazano w poniższej przykładowej konfiguracji.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 To zadanie można również wykonać za pomocą [narzędzia Edytor konfiguracji (SvcConfigEditor.exe).](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
  
 Gdy liczniki wydajności są włączone, cały zestaw liczników wydajności WCF jest włączona dla usługi. Program .NET Framework automatycznie przechowuje dane `ServiceModelService`o `ServiceModelEndpoint` `ServiceModelOperation`wydajności na trzech poziomach: , i . Każdy z tych poziomów ma liczniki wydajności, takie jak "Połączenia", "Połączenia na sekundę" i "Połączenia zabezpieczeń nie autoryzowane".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Aby wyświetlić dane dotyczące wydajności  
  
1. Uruchom narzędzie Monitor wydajności, **Start**klikając przycisk Start `perfmon` , **Uruchom...**, wprowadź i kliknij przycisk **OK** lub w Panelu sterowania, wybierz pozycję **Narzędzia administracyjne** i kliknij dwukrotnie pozycję **Wydajność**.  
  
    > [!NOTE]
    > Nie można dodać liczników, dopóki przykładowy kod nie jest uruchomiony.  
  
2. Usuń liczniki wydajności, które są wymienione, zaznaczając je i naciskając klawisz Delete.  
  
3. Dodaj liczniki WCF, klikając prawym przyciskiem myszy okienko wykresu i wybierając pozycję **Dodaj liczniki**. W oknie dialogowym **Dodawanie liczników** wybierz pozycję **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 lub ServiceModelService 3.0.0.0** w polu listy rozwijanej obiektu Wydajność. Wybierz liczniki, które chcesz wyświetlić z listy.  
  
    > [!NOTE]
    > Nie ma żadnych liczników wydajności WCF dla usługi, jeśli na komputerze nie ma żadnych usług WCF.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Aby włączyć liczniki za pomocą Edytora konfiguracji  
  
1. Otwórz wystąpienie pliku SvcConfigEditor.exe.  
  
2. W menu Plik kliknij polecenie **Otwórz,** a następnie kliknij polecenie **Plik konfiguracyjny...**.  
  
3. Przejdź do przykładowego folderu usługi aplikacji i otwórz plik Web.config.  
  
4. Kliknij **pozycję Diagnostyka** w drzewie konfiguracji.  
  
5. Przełącz **licznik wydajności** w oknie **Diagnostyka,** aby wyświetlić "Wszystko".  
  
6. Zapisz plik konfiguracyjny i zamknij edytor.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
