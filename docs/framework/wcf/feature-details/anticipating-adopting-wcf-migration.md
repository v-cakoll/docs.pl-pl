---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie przyszłych migracji.'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: aeafc164d16d9dc60ad0b3012da292e9b0bb38b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490048"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie przyszłych migracji.
W celu zapewnienia łatwiejsze przyszłych migracji nowej aplikacji ASP.NET do programu WCF, wykonaj powyżej zaleceń, jak również poniższe zalecenia.  
  
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
  
 W ten sposób jest zalecane, ponieważ WCF wymaga wiadomości go przy użyciu różnych punktów końcowych zgodnych z różnych protokołów, takich jak SOAP 1.1 i SOAP 1.2. Jeśli sieci Web ASP.NET 2.0 usługa jest skonfigurowana do obsługi protokołu SOAP 1.1 i SOAP 1.2, co jest konfiguracja domyślna, a następnie nie może być migrowane do przodu do pojedynczego punktu końcowego WCF pod adresem oryginalnej, która byłaby pewnością być zgodny z wszystkich sieci Web ASP.NET istniejących klientów usługi. Również Wybieranie protokołu SOAP 1.2 zamiast 1.1 więcej znacznie ograniczyć klientelę usługi.  
  
## <a name="service-development"></a>Projektowanie usługi  
 Usługi WCF służy do definiowania kontraktów usług, stosując <xref:System.ServiceModel.ServiceContractAttribute> albo interfejsy lub klasy. Zaleca się zastosowanie atrybutu interfejs, a nie do klasy, ponieważ spowoduje to tworzy definicję kontraktu, który może być różnorodnie zaimplementowany przez dowolną liczbę klas. Program ASP.NET 2.0 obsługuje opcję stosowania <xref:System.Web.Services.WebService> atrybutu do interfejsów, a także klasy. Jak już wspomniano, istnieje jednak usterką w programie ASP.NET 2.0, w którym parametr Namespace <xref:System.Web.Services.WebService> atrybut nie ma znaczenia, gdy ten atrybut jest stosowany do interfejsu zamiast klasy. Ponieważ ogólnie jest zalecane, aby zmodyfikować przestrzeni nazw usługi z wartością domyślną http://tempuri.org, za pomocą parametru Namespace <xref:System.Web.Services.WebService> atrybutu, co powinno być kontynuowane Definiowanie usług sieci Web ASP.NET, stosując <xref:System.ServiceModel.ServiceContractAttribute> Atrybut interfejsy lub klasy.  
  
-   Ma małego kodu, jak to możliwe w metodach, według których te interfejsy są zdefiniowane. Niech delegowania ich pracy na inne grupy. Następnie nowych typów usług WCF można również delegować merytorycznych działanie tych klas.  
  
-   Jawne nazwy operacji usługi za pomocą `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Jest ważne, ponieważ domyślne nazwy operacji w programie ASP.NET są inne niż domyślne nazwy dostarczonych przez usługę WCF. Zapewniając jawne nazwy, można uniknąć polegania na domyślne.  
  
-   Nie implementują działania usługi sieci Web ASP.NET za pomocą metod polimorficznym, ponieważ WCF nie obsługuje operacji implementującej za pomocą metod polimorficznym.  
  
-   Użyj <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> o podanie wartości jawne nagłówki SOAPAction HTTP przez HTTP żądania będą kierowane do metod.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Biorąc to podejście obejścia, konieczności polegać na domyślne wartości SOAPAction używanych przez platformę ASP.NET i WCF są takie same.  
  
-   Unikaj stosowania rozszerzeń protokołu SOAP. Jeśli wymagane są rozszerzenia protokołu SOAP, ustal, czy cel, dla których są one są uznawane za to funkcja, która jest już obsługiwane przez usługi WCF. Jeśli w rzeczywistości jest wielkość liter, rozważa ponownie wyboru nie od razu przyjęcie WCF.  
  
## <a name="state-management"></a>Stan zarządzania  
 Unikaj używania do zarządzania stanem w usługach. Nie jest zachowanie stanu mogą naruszyć skalowalność aplikacji tylko mechanizmy zarządzania stanu programu ASP.NET i WCF różnią się bardzo, chociaż WCF obsługuje mechanizmu ASP.NET w trybie zgodności ASP.NET.  
  
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
  
 Te klasy wyjątków będzie łatwo wielokrotnego użytku z programem WCF<xref:System.ServiceModel.FaultException%601> klasę, aby zgłosić nową `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpieczenia  
 Poniżej przedstawiono kilka zaleceń dotyczących zabezpieczeń.  
  
-   Unikaj jako ich użycie za pomocą profilów programu ASP.NET 2.0 ograniczałyby trybu integracji ASP.NET usługa została migracji do programu WCF.  
  
-   Unikaj używania listy kontroli dostępu do kontrolowania dostępu do usług, jak obsługuje usługi sieci Web ASP.NET listy kontroli dostępu przy użyciu usługi Internet Information Services (IIS), usługi WCF nie — ponieważ usług sieci Web ASP.NET są zależne od usług IIS do hostowania i WCF niekoniecznie musi być obsługiwana przez usługi IIS.  
  
-   Należy rozważyć użycie dostawców ról ASP.NET 2.0 w celu autoryzowania dostępu do zasobów usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
