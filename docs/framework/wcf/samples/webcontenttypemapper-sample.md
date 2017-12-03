---
title: "WebContentTypeMapper — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27342076290ca40abefea63edcc5f5c7186c4256
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper — przykład
W tym przykładzie pokazano, jak nowe typy zawartości do mapowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] formatów treści komunikatu.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> Element podłącza kodera wiadomości w sieci Web, dzięki czemu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do odbierania JSON, XML lub raw komunikatów binarnych w tym samym punkcie końcowym. Koder Określa format treści wiadomości, analizując typ zawartości HTTP żądania. W tym przykładzie przedstawiono <xref:System.ServiceModel.Channels.WebContentTypeMapper> klasy, która umożliwia użytkownikowi na kontrolowanie mapowanie między typu zawartości i formatu treści.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zawiera zestaw domyślnych mapowań typów zawartości. Na przykład `application/json` mapy do formatu JSON i `text/xml` mapy do pliku XML. Typ zawartości, który nie jest zamapowany na formacie JSON i XML jest zamapowany na format binarny raw.  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a>Zobacz też
