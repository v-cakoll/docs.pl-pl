---
title: Usługa AJAX bez konfiguracji
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: b3c12801d14c7f6850a985c521c0e3fff92ba8e4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045813"
---
# <a name="ajax-service-without-configuration"></a>Usługa AJAX bez konfiguracji

Ten przykład pokazuje, jak używać programu Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznej języka JavaScript i XML (AJAX) (usługi, do której można uzyskać dostęp za pomocą kodu JavaScript z klienta przeglądarki sieci Web) bez użycia żadnej konfiguracji Ustawienia. Usługa używa specjalnej składni w pliku SVC, aby automatycznie włączyć punkt końcowy AJAX.

Obsługa technologii AJAX w programie WCF jest zoptymalizowana pod kątem użycia z `ScriptManager` ASP.NET AJAX przez formant. Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

 Ten przykład kompiluje się w usłudze AJAX przy użyciu protokołu HTTP POST. Zgodnie z opisem <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> w [podstawowym przykładzie usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) jest używany do hostowania usługi.

```svc
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> do usługi. Jeśli nie trzeba wprowadzać zmian w konfiguracji punktu końcowego, `<system.ServiceModel>` sekcja może zostać całkowicie usunięta z pliku Web. config dla usługi. Plik Web. config zawiera kilka ustawień ASP.NET, które są używane przez ConfigFreeClientPage. aspx. Jeśli tak się nie dzieje, można usunąć cały plik Web. config.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że instrukcje instalacji zostały wykonane w [procedurze jednorazowej konfiguracji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Skompiluj rozwiązanie ConfigFreeAjaxService. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Przejdź do `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (nie otwieraj ConfigFreeClientPage. aspx w przeglądarce z katalogu projektu).

> [!NOTE]
> Podczas uruchamiania tego przykładu upewnij się, że uwierzytelnianie anonimowe i uwierzytelnianie systemu Windows nie są włączone równocześnie dla folderu ServiceModelSamples w usługach IIS. W takim przypadku należy wyłączyć uwierzytelnianie systemu Windows. Po uruchomieniu przykładu Włącz uwierzytelnianie systemu Windows i uruchom polecenie "iisreset".

## <a name="see-also"></a>Zobacz także

- [Podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
