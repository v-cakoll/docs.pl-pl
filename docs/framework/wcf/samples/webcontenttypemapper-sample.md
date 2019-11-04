---
title: WebContentTypeMapper — przykład
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: a259f459606c9745fe10276d967946eb675a7f5e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423797"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper — przykład
Ten przykład pokazuje, jak mapować nowe typy zawartości na formaty treści wiadomości Windows Communication Foundation (WCF).  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> element Plugs w koderze komunikatów sieci Web, który umożliwia WCF odbieranie danych JSON, XML lub nieprzetworzonych komunikatów binarnych w tym samym punkcie końcowym. Koder określa format treści wiadomości, sprawdzając zawartość HTTP-Type żądania. Ten przykład wprowadza klasę <xref:System.ServiceModel.Channels.WebContentTypeMapper>, która umożliwia użytkownikowi kontrolowanie mapowania między typem zawartości i formatem treści.  
  
 Funkcja WCF udostępnia zestaw domyślnych mapowań dla typów zawartości. Na przykład `application/json` Maps do formatu JSON i `text/xml` Maps do formatu XML. Wszystkie typy zawartości, które nie są zamapowane na notację JSON lub XML, są mapowane na format nieprzetworzonych danych binarnych.  
  
 W niektórych scenariuszach (na przykład interfejsów API wypychania) Deweloper usługi nie kontroluje typu zawartości zwracanej przez klienta. Na przykład klienci mogą zwrócić kod JSON jako `text/javascript`, a nie `application/json`. W takim przypadku Deweloper usługi musi dostarczyć typ, który pochodzi od <xref:System.ServiceModel.Channels.WebContentTypeMapper>, aby prawidłowo obsłużyć dany typ zawartości, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 Typ musi przesłaniać metodę <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29>. Metoda musi oszacować argument `contentType` i zwracać jedną z następujących wartości: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>lub <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Zwrócenie <xref:System.ServiceModel.Channels.WebContentFormat.Default> jest wykonywane do domyślnych mapowań kodera komunikatów sieci Web. W poprzednim przykładowym kodzie `text/javascript` typ zawartości jest mapowany na notację JSON, a wszystkie pozostałe mapowania pozostają bez zmian.  
  
 Aby użyć klasy `JsonContentTypeMapper`, użyj następującego w pliku Web. config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Aby sprawdzić wymagania dotyczące używania JsonContentTypeMapper, Usuń atrybut contentTypeMapper z powyższego pliku konfiguracji. Nie można załadować strony klienta podczas próby użycia `text/javascript` do wysłania zawartości JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Skompiluj rozwiązanie WebContentTypeMapperSample. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Przejdź do `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (nie należy otwierać JCTMClientPage. htm w przeglądarce z katalogu projektu).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
