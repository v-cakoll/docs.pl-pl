---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 09bbb11c58992f0fabcb822f5f3d88fef273bea9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425282"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości
Aby zapewnić łatwiejsze migracji w przyszłości nowej aplikacji ASP.NET do programu WCF, postępuj zgodnie z poprzednim zalecenia, a także poniższe zalecenia.  
  
## <a name="protocols"></a>Protokoły  
 Wyłączanie obsługi programu ASP.NET 2.0 protokołu SOAP 1.2:  
  
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
  
 Ten sposób jest zalecane, ponieważ WCF wymaga wiadomości go przy użyciu różnych punktów końcowych zgodnych z różnych protokołów, takich jak SOAP 1.1 i SOAP 1.2. Jeśli sieci Web ASP.NET 2.0 usługa jest skonfigurowana do obsługi protokołu SOAP 1.1 i SOAP 1.2, która jest domyślna konfiguracja, a następnie nie może być migrowane do przodu do jednym punkcie końcowym WCF pod adresem oryginalnej, która byłaby bez obaw być zgodne ze wszystkimi sieci Web platformy ASP.NET istniejący klienci usługi. Również wybranie SOAP 1.2 zamiast 1.1 bardziej poważnie ograniczy klientelę usługi.  
  
## <a name="service-development"></a>Tworzenie usługi  
 Usługi WCF służy do definiowania kontraktów usług, stosując <xref:System.ServiceModel.ServiceContractAttribute> interfejsy lub klasy. Zalecane jest aby zastosować atrybut do interfejsu, a nie do klasy, ponieważ spowoduje to więc tworzy definicję kontraktu, który może być różnorodnie implementowany przez dowolną liczbę klas. Program ASP.NET 2.0 obsługuje opcję stosowania <xref:System.Web.Services.WebService> atrybutu do interfejsów, a także klasy. Jak już wspomniano, istnieje jednak wadę w programie ASP.NET 2.0 za pomocą którego parametr Namespace <xref:System.Web.Services.WebService> atrybut nie ma wpływu Jeśli ten atrybut jest stosowany do interfejsu, a nie klasę. Ponieważ jest na ogół do modyfikowania przestrzeni nazw usługi z wartością domyślną `http://tempuri.org`, za pomocą parametru Namespace <xref:System.Web.Services.WebService> atrybutu, jeden powinno być kontynuowane Definiowanie usług sieci Web ASP.NET, stosując <xref:System.ServiceModel.ServiceContractAttribute> Atrybut interfejsy lub klasy.  
  
- Jak to możliwe za pomocą metod, które są zdefiniowane te interfejsy, należy mieć jako niewielkiej ilości kodu. Poproś delegować swoją pracę dla innych klas. Nowe typy usług WCF następnie może również delegować swoją pracę merytorycznych do tych klas.  
  
- Podać jawne nazwy dla operacji usługi za pomocą `MessageName` parametru <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     To jest ważne, ponieważ z domyślnymi nazwami operacje w programie ASP.NET: różnią się od nazwy domyślne, dostarczone przez architekturę WCF. Dostarczając jawnej nazwy, można uniknąć, opierając się na domyślne.  
  
- Nie należy implementować operacji usługi sieci Web platformy ASP.NET za pomocą metod polimorficznych, ponieważ WCF nie obsługuje operacji implementującej za pomocą metod polimorficznych.  
  
- Użyj <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> podać jawne wartości nagłówków SOAPAction HTTP, przez które HTTP żądania będą kierowane do metody.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     W ten sposób obejścia, konieczności opierają się na domyślnej wartości SOAPAction używane przez program ASP.NET i WCF jest taka sama.  
  
- Należy unikać używania rozszerzeń protokołu SOAP. Jeśli rozszerzenia SOAP, które są wymagane, określ, czy celem, dla którego one są uznawane za to funkcja, która znajduje się już przez architekturę WCF. Jeśli tak jest rzeczywiście tak, ponowne rozpatrzenie możliwość nie przyjmują razu WCF.  
  
## <a name="state-management"></a>Zarządzanie stanem  
 Uniknąć konieczności zarządzania stanem w usługach. Nie tylko jest zachowanie stanu mają tendencję do naruszenia bezpieczeństwa skalowalność aplikacji, ale mechanizmami zarządzania stan programu ASP.NET i WCF różnią się bardzo, chociaż WCF obsługuje mechanizmów platformy ASP.NET w trybie zgodności w programie ASP.NET.  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 Projektowanie struktury typów danych, aby być wysyłane i odbierane przez usługę, również struktury projektu do reprezentowania różne rodzaje wyjątków, które mogą wystąpić w ramach usługi ten. może chcieć przekazania do klienta.  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException 
{ 
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation 
    {  
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
  
```csharp  
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
  
 Klasy mogą następnie służyć do Podaj szczegóły, aby jawnie zgłoszony <xref:System.Web.Services.Protocols.SoapException> wystąpień:  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Te klasy wyjątków będzie łatwo wielokrotnego użytku z programem WCF <xref:System.ServiceModel.FaultException%601> klasy, aby wygenerować nowy `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpieczenia  
 Poniżej przedstawiono kilka zaleceń dotyczących zabezpieczeń.  
  
- Należy unikać przy użyciu profilów platformy ASP.NET 2.0 jako ich użycie będzie ograniczyć użycie trybu integracji programu ASP.NET, jeśli usługa została poddana migracji do programu WCF.  
  
- Należy unikać używania listy ACL do kontrolowania dostępu do usług, jako usług sieci Web platformy ASP.NET — obsługuje listy kontroli dostępu przy użyciu usług Internet Information Services (IIS), usługi WCF nie — ponieważ usług sieci Web programu ASP.NET, są zależne od usług IIS do hostowania i usługi WCF nie musi być hostowane w usługach IIS.  
  
- Należy rozważyć użycie dostawcy roli programu ASP.NET 2.0 do autoryzowania dostępu do zasobów usługi.  
  
## <a name="see-also"></a>Zobacz także

- [Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
