---
title: Usługa AJAX bez konfiguracji
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: f12b0fad97c9f43397f3b202800943e6d061aa53
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180897"
---
# <a name="ajax-service-without-configuration"></a>Usługa AJAX bez konfiguracji
W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznych w języku JavaScript i XML (technologia AJAX) (usługa, której będziesz mieć dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web), bez używania konfiguracji Ustawienia. Usługa używa specjalnej składni w pliku SVC, można automatycznie włączyć punkt końcowy interfejsu AJAX.  
  
 Obsługa technologii AJAX w programie WCF jest zoptymalizowany do użytku z programem ASP.NET AJAX za pośrednictwem `ScriptManager` kontroli. Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady Ajax](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Ten przykład tworzy po AJAX Service przy użyciu protokołu HTTP POST. Zgodnie z opisem w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) przykładzie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> służy do obsługi usługi.  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> do usługi. Jeśli żadne zmiany konfiguracji potrzebne do endpoint, `<system.ServiceModel>` sekcji można całkowicie usunięte z pliku Web.config dla usługi. Plik Web.config zawiera kilka ustawień platformy ASP.NET, które są używane przez ConfigFreeClientPage.aspx. Jeśli uprzednio nie tak, udało się usunąć cały plik Web.config.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonać instrukcje instalacji [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie ConfigFreeAjaxService.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Przejdź do http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (nie należy otwierać ConfigFreeClientPage.aspx w przeglądarce z katalogu projektu).  
  
> [!NOTE]
>  Podczas uruchamiania tego przykładu, upewnij się, że uwierzytelnianie anonimowe i uwierzytelnianie Windows nie są włączone jednocześnie dla folderu ServiceModelSamples w usługach IIS. Jeśli tak jest rzeczywiście, Wyłącz uwierzytelnianie Windows. Po uruchomieniu przykładu, włączyć uwierzytelnianie Windows, a następnie uruchom "polecenie iisreset".  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
