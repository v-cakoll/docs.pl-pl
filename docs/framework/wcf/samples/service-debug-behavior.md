---
title: "Zachowanie debugowania usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04520eda9fe7ce2cd461e094fe2cec76d52ccc7d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="service-debug-behavior"></a>Zachowanie debugowania usług
W przykładzie pokazano, jak można skonfigurować ustawienia zachowanie debugowania usług. Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi. W tym przykładzie jawnie definiuje zachowanie debugowania usług w pliku konfiguracji. Mogą również to robić imperatively w kodzie.  
  
 W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik Web.config dla serwera definiuje zachowanie debugowania usług, aby włączyć stronę pomocy i obsługi wyjątków, jak pokazano w poniższym przykładzie.  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) jest element konfiguracji, który umożliwia zmianę właściwości zachowanie debugowania usług. Użytkownik może modyfikować tego zachowania, to osiągnięcie następujących:  
  
-   Dzięki temu usługi do zwrócenia wyjątku zgłoszonego przez kod aplikacji, nawet jeśli wyjątek nie został zadeklarowany za pomocą <xref:System.ServiceModel.FaultContractAttribute>. Odbywa się przez ustawienie `includeExceptionDetailInFaults` do `true`. To ustawienie jest przydatne, gdy debugowanie przypadków, gdy serwer jest zgłaszanie wystąpił nieoczekiwany wyjątek.  
  
    > [!IMPORTANT]
    >  Nie jest bezpieczne, aby włączyć to ustawienie w środowisku produkcyjnym. Wyjątek nieoczekiwany serwera może mieć pewne informacje, które nie jest przeznaczony dla klienta i dlatego ustawienie `includeExceptionDetailsInFaults` do `true` może spowodować wycieku informacji.  
  
-   [ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) również pozwala użytkownikowi na włączanie lub wyłączanie strony pomocy. Każda usługa opcjonalnie mogą uwidaczniać strona pomocy, który zawiera informacje dotyczące usługi, w tym punktu końcowego można pobrać WSDL dla usługi. Można je włączyć, ustawiając `httpHelpPageEnabled` do `true`. Umożliwia to strona pomocy ma zostać zwrócona na żądanie GET adres podstawowy usługi. Ten adres można zmienić, określając inny atrybut `httpHelpPageUrl`. Umożliwia to bezpieczne przy użyciu protokołu HTTPS zamiast protokołu HTTP. Można to zrobić przez ustawienie `httpsHelpPageEnabled` i `httpsHelpPageUrl`.  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Pierwsze trzy operacje (Dodawanie, odejmowanie i mnożenia) musi się zakończyć powodzeniem. Ostatnia operacja "(dzielenie) kończy się niepowodzeniem z dzielenia przez zero wyjątek.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>Zobacz też
