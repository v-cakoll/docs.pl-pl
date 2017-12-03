---
title: "Rozszerzanie śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09804e91b872e4daca929d9f9740d691d42b31c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="extending-tracing"></a>Rozszerzanie śledzenia
W tym przykładzie pokazano, jak rozszerzyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcja śledzenia pisząc śledzenia zdefiniowanych przez użytkownika działań w kod klienta i usługi. Dzięki temu użytkownikowi na tworzenie śledzenia działań i grupować dane śledzenia w logiczne jednostki pracy. Istnieje również możliwość służące do skorelowania działań za pośrednictwem transferu (w ramach tego samego punktu końcowego) i propagacji (za pośrednictwem punktów końcowych). W tym przykładzie śledzenie jest włączone dla klienta i usługi. Aby uzyskać więcej informacji o sposobie włączania śledzenia w plikach konfiguracji klienta i usługi, zobacz [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Śledzenie i propagowania działań.  
 Śledzenie działania użytkownika zezwala użytkownikowi na tworzenie własnych działań śledzenia do śledzenia grupy w logiczne jednostki pracy, korelowanie działań za pośrednictwem przesyłania i propagacji i zmniejszyć koszt wydajności [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] śledzenia (na przykład miejsce kosztu dysku dla pliku dziennika).  
  
### <a name="adding-custom-sources"></a>Dodawanie źródeł niestandardowych  
 Ślady zdefiniowane przez użytkownika można dodać do kodu klienta i usługi. Dodawanie źródła śledzenia w plikach konfiguracji klienta lub usługę umożliwiają te niestandardowe śladów rejestrowane i wyświetlane w [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Poniższy kod przedstawia sposób dodawania źródła śledzenia zdefiniowanych przez użytkownika o nazwie `ServerCalculatorTraceSource` do pliku konfiguracji.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a>Korelowanie działań  
 Aby skorelować działań bezpośrednio w obrębie punktów końcowych, `propagateActivity` atrybut musi być ustawiony na `true` w `System.ServiceModel` źródła śledzenia. Ponadto propagację śladów bez pośrednictwa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działania ServiceModel działania śledzenia musi być wyłączona. Można to zaobserwować w poniższym przykładzie kodu.  
  
> [!NOTE]
>  Wyłączenie śledzenia działania ServiceModel nie jest taka sama jak o poziomie śledzenia, wskazywane przez `switchValue` właściwość ustawiona na wartość off.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Zmniejszenie kosztów wydajności  
 Ustawienie `ActivityTracing` wyłączone w `System.ServiceModel` źródło śladu generuje plik śledzenia, który zawiera tylko ślady działania zdefiniowane przez użytkownika, bez żadnej śladów działania ServiceModel uwzględnione. Powoduje to znacznie mniejszy rozmiar pliku dziennika. Jednak możliwość skorelowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przetwarzania śladów zostaną utracone.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
