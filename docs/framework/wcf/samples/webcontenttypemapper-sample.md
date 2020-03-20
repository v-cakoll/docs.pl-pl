---
title: WebContentTypeMapper — przykład
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 540e5e775cf7b2a5a5b585d98772415653fa833a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143567"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper — przykład
W tym przykładzie pokazano, jak mapować nowe typy zawartości do formatów treści komunikatów programu Windows Communication Foundation (WCF).  
  
 Element <xref:System.ServiceModel.Description.WebHttpEndpoint> podłącza koder wiadomości sieci Web, który umożliwia WCF odbierać JSON, XML lub nieprzetworzone wiadomości binarne w tym samym punkcie końcowym. Koder określa format treści wiadomości, patrząc na typ zawartości HTTP żądania. W tym przykładzie wprowadza <xref:System.ServiceModel.Channels.WebContentTypeMapper> klasę, która umożliwia użytkownikowi kontrolowanie mapowania między typem zawartości a formatem treści.  
  
 WCF udostępnia zestaw mapowań domyślnych dla typów zawartości. Na przykład `application/json` mapuje do `text/xml` JSON i mapuje do XML. Każdy typ zawartości, który nie jest mapowany na JSON lub XML, jest mapowany na nieprzetworzony format binarny.  
  
 W niektórych scenariuszach (na przykład interfejsów API w stylu wypychania) deweloper usługi nie kontroluje typu zawartości zwracanego przez klienta. Na przykład klienci mogą zwracać JSON jako `text/javascript` zamiast . `application/json` W takim przypadku deweloper usługi musi podać typ, który pochodzi od <xref:System.ServiceModel.Channels.WebContentTypeMapper> do obsługi danego typu zawartości poprawnie, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Typ musi zastąpić <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metodę. Metoda musi ocenić `contentType` argument i zwrócić jedną <xref:System.ServiceModel.Channels.WebContentFormat.Json> <xref:System.ServiceModel.Channels.WebContentFormat.Xml>z <xref:System.ServiceModel.Channels.WebContentFormat.Raw>następujących <xref:System.ServiceModel.Channels.WebContentFormat.Default>wartości: , , , lub . Powrót <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers do domyślnych mapowania kodera wiadomości sieci Web. W poprzednim przykładowym `text/javascript` kodzie typ zawartości jest mapowany na JSON, a wszystkie inne mapowania pozostają niezmienione.  
  
 Aby użyć `JsonContentTypeMapper` tej klasy, użyj następujących elementów w witrynie Web.config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Aby sprawdzić wymagania dotyczące korzystania z JsonContentTypeMapper, usuń atrybut contentTypeMapper z powyższego pliku konfiguracji. Strona klienta nie można załadować `text/javascript` podczas próby wysłania zawartości JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Tworzenie rozwiązania WebContentTypeMapperSample.sln zgodnie z opisem w [tworzenie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Przejdź `http://localhost/ServiceModelSamples/JCTMClientPage.htm` do (nie otwieraj pliku JCTMClientPage.htm w przeglądarce z poziomu katalogu projektu).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
