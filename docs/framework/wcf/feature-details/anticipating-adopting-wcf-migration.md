---
title: "Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie przyszłych migracji."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ecac6917d47604aa66e9cdc0d845e76ad2de5d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie przyszłych migracji.
Aby zapewnić ułatwia migrację przyszłych nowej aplikacji ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], postępuj zgodnie z poprzednim zalecenia, jak również poniższe zalecenia.  
  
## <a name="protocols"></a>protokoły  
 Wyłącz obsługę programu ASP.NET 2.0 SOAP 1.2:  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>    
      </webServices>  
     </system.web>   
</configuration>  
```  
  
 To jest wskazane ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga wiadomości go przy użyciu różnych punktów końcowych zgodnych z różnych protokołów, takich jak SOAP 1.1 i SOAP 1.2. Usługi sieci Web programu ASP.NET 2.0 jest skonfigurowany do obsługi protokołu SOAP 1.1 i SOAP 1.2, co jest konfiguracją domyślną, a następnie go nie można migrować do przodu do pojedynczego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego pod adresem oryginalnej, które będą na pewno jest zgodny ze wszystkimi ASP Usługa sieci web .NET istniejących klientów. Również Wybieranie protokołu SOAP 1.2 zamiast 1.1 więcej znacznie ograniczyć klientelę usługi.  
  
## <a name="service-development"></a>Projektowanie usługi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Służy do definiowania kontraktów usług, stosując <xref:System.ServiceModel.ServiceContractAttribute> albo interfejsy lub klasy. Zaleca się zastosowanie atrybutu interfejs, a nie do klasy, ponieważ spowoduje to tworzy definicję kontraktu, który może być różnorodnie zaimplementowany przez dowolną liczbę klas. Program ASP.NET 2.0 obsługuje opcję stosowania <xref:System.Web.Services.WebService> atrybutu do interfejsów, a także klasy. Jak już wspomniano, istnieje jednak usterką w programie ASP.NET 2.0, w którym parametr Namespace <xref:System.Web.Services.WebService> atrybut nie ma znaczenia, gdy ten atrybut jest stosowany do interfejsu zamiast klasy. Ponieważ ogólnie jest zalecane, aby zmodyfikować przestrzeni nazw usługi z wartością domyślną http://tempuri.org przy użyciu parametru Namespace <xref:System.Web.Services.WebService> atrybutu, co powinno być kontynuowane Definiowanie usług sieci Web ASP.NET, stosując <xref:System.ServiceModel.ServiceContractAttribute> Atrybut interfejsy lub klasy.  
  
-   Ma małego kodu, jak to możliwe w metodach, według których te interfejsy są zdefiniowane. Niech delegowania ich pracy na inne grupy. Nowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typów usług można następnie delegować merytorycznych działanie tych klas.  
  
-   Jawne nazwy operacji usługi za pomocą `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Jest ważne, ponieważ domyślne nazwy operacji w programie ASP.NET są inne niż domyślne nazwy dostarczonych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Zapewniając jawne nazwy, można uniknąć polegania na domyślne.  
  
-   Nie implementuje operacji usługi sieci Web ASP.NET za pomocą metod polimorficznym, ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie obsługuje operacji implementującej za pomocą metod polimorficznym.  
  
-   Użyj <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> o podanie wartości jawne nagłówki SOAPAction HTTP przez HTTP żądania będą kierowane do metod.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Biorąc to rozwiązanie zostanie obejścia konieczności polegać na domyślne wartości SOAPAction używanych przez platformę ASP.NET i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są takie same.  
  
-   Unikaj stosowania rozszerzeń protokołu SOAP. Jeśli wymagane są rozszerzenia protokołu SOAP, następnie określić, czy cel, dla których są one są uznawane za jest funkcją, która jest już obsługiwane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Jeśli w rzeczywistości jest wielkość liter, rozważenia opcja nie przyjmuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] od razu.  
  
## <a name="state-management"></a>Stan zarządzania  
 Unikaj używania do zarządzania stanem w usługach. Nie tylko zachowanie stanu mogą naruszyć skalowalność aplikacji, ale mechanizmy zarządzania stan aplikacji ASP.NET i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bardzo różnią się, mimo że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje mechanizmów ASP.NET w zgodności z platformą ASP.NET tryb.  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 Projektowanie struktury typów danych, aby być wysyłane i odbierane przez usługę, również struktury projektu do reprezentowania różnych typów wyjątków, które mogą wystąpić w ramach usługi co może chcieć przekazania do klienta.  
  
```  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 Zapewnianie takich klas możliwości serializacji się do pliku XML:  
  
```  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 Klasy, następnie może służyć do Podaj szczegóły, aby jawnie zgłoszony <xref:System.Web.Services.Protocols.SoapException> wystąpień:  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Te klasy wyjątków będzie łatwo wielokrotnego użytku z[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.FaultException%601> klasę, aby zgłosić nową`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpieczenia  
 Poniżej przedstawiono kilka zaleceń dotyczących zabezpieczeń.  
  
-   Unikaj jako ich użycie za pomocą profilów programu ASP.NET 2.0 ograniczałyby trybu integracji ASP.NET Jeśli usługa został zmigrowany do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Unikaj używania listy kontroli dostępu do kontrolowania dostępu do usług, jako usługi sieci Web ASP.NET obsługuje listy ACL za pomocą Internet Information Services (IIS), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie — ponieważ usług sieci Web ASP.NET są zależne od usług IIS do hostowania i WCF niekoniecznie musi być obsługiwana przez usługi IIS.  
  
-   Należy rozważyć użycie dostawców ról ASP.NET 2.0 w celu autoryzowania dostępu do zasobów usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
