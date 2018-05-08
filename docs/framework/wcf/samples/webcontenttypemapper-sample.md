---
title: WebContentTypeMapper — przykład
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 3b3d53b0fe619c74c5e7f3533194f4b5e7c18a16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper — przykład
W tym przykładzie przedstawiono sposób mapowania nowe typy zawartości do formatów treści wiadomości Windows Communication Foundation (WCF).  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> Element podłącza kodera wiadomości w sieci Web, dzięki czemu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do odbierania JSON, XML lub raw komunikatów binarnych w tym samym punkcie końcowym. Koder Określa format treści wiadomości, analizując typ zawartości HTTP żądania. W tym przykładzie przedstawiono <xref:System.ServiceModel.Channels.WebContentTypeMapper> klasy, która umożliwia użytkownikowi na kontrolowanie mapowanie między typu zawartości i formatu treści.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera zestaw domyślnych mapowań typów zawartości. Na przykład `application/json` mapy do formatu JSON i `text/xml` mapy do pliku XML. Typ zawartości, który nie jest zamapowany na formacie JSON i XML jest zamapowany na format binarny raw.  
  
 W niektórych scenariuszach (na przykład stylu wypychania API) dewelopera usługi nie kontroluje zawartości typ zwracany przez klienta. Na przykład klienci mogą zwracać dane JSON jako `text/javascript` zamiast `application/json`. W takim przypadku podać typu pochodzącego od dewelopera usługi <xref:System.ServiceModel.Channels.WebContentTypeMapper> poprawnie, jak pokazano w poniższym kodzie próbki obsługi danego typu zawartości.  
  
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
  
 Typ musi zastąpić <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metody. Należy ocenić metodę `contentType` argumentów i zwracane jednej z następujących wartości: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, lub <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Zwracanie <xref:System.ServiceModel.Channels.WebContentFormat.Default> różni się do domyślnych mapowań kodera wiadomości w sieci Web. W poprzednim przykładowym kodzie `text/javascript` zawartości typu jest mapowana do formatu JSON, a wszystkie inne mapowania pozostają niezmienione.  
  
 Aby użyć `JsonContentTypeMapper` klasy, należy użyć następującego w pliku Web.config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Aby sprawdzić wymagania dotyczące korzystania z JsonContentTypeMapper, usuń atrybut zamapował z powyższych pliku konfiguracji. Strona klienta nie udało się załadować podczas próby użycia `text/javascript` do wysyłania zawartości JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie WebContentTypeMapperSample.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Przejdź do http://localhost/ServiceModelSamples/JCTMClientPage.htm (nie należy otwierać JCTMClientPage.htm w przeglądarce z katalogu projektu).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a>Zobacz też
