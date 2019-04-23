---
title: WebContentTypeMapper — przykład
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 381fc4a3084b1a2620384a04de85b9085e02ae16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973515"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper — przykład
Niniejszy przykład pokazuje jak mapować nowych typów zawartości do formatów treści komunikat usług Windows Communication Foundation (WCF).  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> Element zapewnia Ci dostęp w sieci Web koder komunikatów, co pozwala WCF do odbierania JSON, XML lub nieprzetworzone komunikaty binarne na ten sam punkt końcowy. Koder Określa format treści wiadomości, sprawdzając typ zawartości HTTP żądania. W tym przykładzie przedstawiono <xref:System.ServiceModel.Channels.WebContentTypeMapper> klasy, która pozwala użytkownikowi na kontrolowanie mapowanie między typu zawartości i format treści.  
  
 Usługi WCF zapewnia zestawem mapowań domyślnych typów zawartości. Na przykład `application/json` mapuje do formatu JSON i `text/xml` mapuje do pliku XML. Typ zawartości, która nie została zamapowana na JSON lub XML jest mapowany na pierwotnych format binarny.  
  
 W niektórych przypadkach (na przykład interfejsy API wypychania stylu) dla deweloperów usługi nie kontroluje zawartości typ zwracany przez klienta. Na przykład klienci mogą zwracać dane JSON jako `text/javascript` zamiast `application/json`. W tym przypadku deweloperów usługi należy podać typ, który pochodzi od klasy <xref:System.ServiceModel.Channels.WebContentTypeMapper> poprawnie, jak pokazano w poniższym przykładowym kodzie obsługi danego typu zawartości.  
  
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
  
 Typ musi przesłonić metodę <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metody. Metoda musi zwrócić `contentType` argumentów i zwracanego jedną z następujących wartości: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, lub <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Zwracanie <xref:System.ServiceModel.Channels.WebContentFormat.Default> odracza do domyślnych mapowań kodera komunikatów w sieci Web. W poprzednim kodzie przykładowe `text/javascript` zawartości typu jest mapowany do formatu JSON i innych mapowaniach pozostają niezmienione.  
  
 Aby użyć `JsonContentTypeMapper` klasy, należy użyć następującego w z pliku Web.config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Aby sprawdzić wymagania dotyczące korzystania z JsonContentTypeMapper, usuń atrybut zamapował z powyższych pliku konfiguracji. Strona klienta ładuje się podczas próby użycia `text/javascript` do wysyłania zawartości do formatu JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Skompiluj rozwiązanie WebContentTypeMapperSample.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Przejdź do `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (nie należy otwierać JCTMClientPage.htm w przeglądarce z katalogu projektu).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
