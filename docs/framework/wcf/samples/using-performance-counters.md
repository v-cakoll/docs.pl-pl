---
title: "Używanie liczników wydajności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84cbbf83c240ae11099e2c9646150c810a437e71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-performance-counters"></a>Używanie liczników wydajności
W tym przykładzie przedstawiono sposób uzyskiwania dostępu do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] liczniki wydajności oraz sposobu tworzenia liczników wydajności zdefiniowanych przez użytkownika. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie klient wywołuje metody cztery `ICalculator` usługi. Klient w dalszym ciągu to zrobić, dopóki nie zostanie przerwane przez użytkownika. Usługa pozostanie bez zmian.  
  
 Liczniki wydajności są włączone w sekcji Diagnostyka pliku Web.config dla usługi, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 To zadanie można również wykonać za pomocą [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Jeśli liczniki wydajności są włączone, cały zestaw [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liczniki wydajności są włączone dla usługi. .NET Framework automatycznie przechowuje dane dotyczące wydajności na trzech poziomach: `ServiceModelService`, `ServiceModelEndpoint` i `ServiceModelOperation`. Każda z tych poziomów ma liczniki wydajności, takich jak "Wywołania", "Wywołania na sekundę" i "Zabezpieczenia wywołania nieautoryzowane".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Aby wyświetlić dane wydajności  
  
1.  Uruchom narzędzie monitora wydajności, klikając **Start**, **Uruchom...** , wprowadź `perfmon` i kliknij przycisk **OK** lub z poziomu Panelu sterowania, wybierz **narzędzia administracyjne** i kliknij dwukrotnie **wydajności**.  
  
    > [!NOTE]
    >  Nie można dodać liczniki, dopóki nie zostanie uruchomiony w przykładowym kodzie.  
  
2.  Usuń liczniki wydajności, które są wyświetlane, zaznaczając je i naciskając klawisz Delete.  
  
3.  Dodaj [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liczniki prawym przyciskiem myszy okienko Wykres i wybierając **Dodaj liczniki**. W **Dodaj liczniki** okno dialogowe, wybierz opcję **ServiceModelOperation 3.0.0.0 ServiceModelEndpoint 3.0.0.0 i ServiceModelService 3.0.0.0** w obiekcie wydajności listy rozwijanej pola listy. Wybierz liczniki, które mają być wyświetlane na liście.  
  
    > [!NOTE]
    >  Istnieją nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liczniki wydajności dla usługi, jeśli istnieją nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi działające na komputerze.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Aby włączyć liczniki za pomocą edytora konfiguracji  
  
1.  Otwórz wystąpienie SvcConfigEditor.exe.  
  
2.  W menu Plik kliknij polecenie **Otwórz** , a następnie kliknij przycisk **pliku konfiguracji...** .  
  
3.  Przejdź do folderu usługi przykładowej aplikacji, a następnie otwórz plik Web.config.  
  
4.  Kliknij przycisk **diagnostyki** na drzewie konfiguracji.  
  
5.  Przełącz **licznika wydajności** w **diagnostyki** okno, aby wyświetlić "All".  
  
6.  Zapisz plik konfiguracji i zamknij Edytor.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
