---
title: Usługa AJAX bez konfiguracji
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 53a0de88d08fbc12cb8861042a50da6503fa5def
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809189"
---
# <a name="ajax-service-without-configuration"></a>Usługa AJAX bez konfiguracji
W tym przykładzie pokazano, jak używać usługi Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznego JavaScript i XML (AJAX) (usługi, której będziesz mieć dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web) bez użycia żadnej konfiguracji Ustawienia. Usługa używa składni specjalne w pliku svc można automatycznie włączyć punktu końcowego AJAX.  
  
 Obsługa interfejsu AJAX w programie WCF jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem `ScriptManager` formantu. Na przykład przy użyciu programu WCF z ASP.NET AJAX, zobacz [przykłady Ajax](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie bazując na AJAX Service przy użyciu protokołu HTTP POST. Zgodnie z opisem w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> służy do obsługi usługi.  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> do usługi. Jeśli żadne zmiany konfiguracji trzeba wprowadzić do punktu końcowego `<system.ServiceModel>` sekcji można całkowicie usunięte z pliku Web.config dla usługi. Plik Web.config zawiera niektórych ustawień platformy ASP.NET, które są używane przez ConfigFreeClientPage.aspx. Jeśli, które nie były wielkość liter, można usunąć cały plik Web.config.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonać instrukcje dotyczące instalacji w [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie ConfigFreeAjaxService.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Przejdź do http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (nie należy otwierać ConfigFreeClientPage.aspx w przeglądarce z katalogu projektu).  
  
> [!NOTE]
>  Podczas uruchamiania tego przykładu, upewnij się, że uwierzytelniania anonimowego i uwierzytelniania systemu Windows nie są włączone jednocześnie folderu ServiceModelSamples w usługach IIS. Jeśli tak jest, Wyłącz uwierzytelnianie systemu Windows. Po uruchomieniu próbki włączyć uwierzytelnianie systemu Windows i uruchom "polecenie iisreset".  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
