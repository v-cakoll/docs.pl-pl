---
title: WebContentTypeMapper — przykład
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 1b15651859fd17673caf898df02c2b74a85d7612
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038540"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper — przykład
Ten przykład pokazuje, jak mapować nowe typy zawartości na formaty treści wiadomości Windows Communication Foundation (WCF).  
  
 Element <xref:System.ServiceModel.Description.WebHttpEndpoint> jest elementem kodera komunikatów sieci Web, który umożliwia platformie WCF odbieranie komunikatów JSON, XML lub nieprzetworzonych danych binarnych w tym samym punkcie końcowym. Koder określa format treści wiadomości, sprawdzając zawartość HTTP-Type żądania. Ten przykład wprowadza <xref:System.ServiceModel.Channels.WebContentTypeMapper> klasę, która umożliwia użytkownikowi kontrolowanie mapowania między typem zawartości i formatem treści.  
  
 Funkcja WCF udostępnia zestaw domyślnych mapowań dla typów zawartości. Na przykład `application/json` mapuje do formatu JSON `text/xml` i mapuje do formatu XML. Wszystkie typy zawartości, które nie są zamapowane na notację JSON lub XML, są mapowane na format nieprzetworzonych danych binarnych.  
  
 W niektórych scenariuszach (na przykład interfejsów API wypychania) Deweloper usługi nie kontroluje typu zawartości zwracanej przez klienta. Na przykład klienci mogą zwrócić kod JSON jako `text/javascript` `application/json`zamiast. W takim przypadku deweloper usług musi dostarczyć typ, który pochodzi od <xref:System.ServiceModel.Channels.WebContentTypeMapper> , aby prawidłowo obsłużyć dany typ zawartości, jak pokazano w poniższym przykładowym kodzie.  
  
```  
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
  
 Typ musi przesłaniać <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metodę. Metoda musi `contentType` oszacować argument i zwracać jedną z następujących wartości: <xref:System.ServiceModel.Channels.WebContentFormat.Xml> <xref:System.ServiceModel.Channels.WebContentFormat.Json>,, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, lub <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Zwracanie <xref:System.ServiceModel.Channels.WebContentFormat.Default> wartości do domyślnych mapowań kodera komunikatów sieci Web. W poprzednim przykładowym kodzie `text/javascript` typ zawartości jest mapowany na format JSON, a wszystkie inne mapowania pozostają bez zmian.  
  
 Aby użyć `JsonContentTypeMapper` klasy, użyj następującego w pliku Web. config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Aby sprawdzić wymagania dotyczące używania JsonContentTypeMapper, Usuń atrybut contentTypeMapper z powyższego pliku konfiguracji. Nie można załadować strony klienta podczas próby wysłania zawartości JSON `text/javascript` przy użyciu programu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Skompiluj rozwiązanie WebContentTypeMapperSample. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Przejdź do `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (nie otwieraj JCTMClientPage. htm w przeglądarce z katalogu projektu).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
