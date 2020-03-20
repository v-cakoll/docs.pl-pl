---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185473"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości
Aby zapewnić łatwiejszą migrację nowych aplikacji ASP.NET do WCF, postępuj zgodnie z poprzednimi zaleceniami, a także następującymi zaleceniami.  
  
## <a name="protocols"></a>Protokoły  
 Wyłącz obsługę protokołu ASP.NET 2.0 dla protokołu SOAP 1.2:  
  
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
  
 Jest to wskazane, ponieważ WCF wymaga komunikatów zgodnych z różnymi protokołami, takich jak SOAP 1.1 i SOAP 1.2, aby przejść przy użyciu różnych punktów końcowych. Jeśli usługa sieci Web ASP.NET 2.0 jest skonfigurowana do obsługi zarówno protokołu SOAP 1.1, jak i PROTOKOŁU SOAP 1.2, który jest konfiguracją domyślną, nie można jej przeprowadzić migracji do jednego punktu końcowego WCF pod oryginalnym adresem, który z pewnością byłby zgodny ze wszystkimi ASP.NET Web istniejących klientów serwisu. Również wybranie protokołu SOAP 1.2 zamiast 1.1 spowoduje bardziej poważne ograniczenie klienteli usługi.  
  
## <a name="service-development"></a>Rozwój usług  
 WCF umożliwia definiowanie umów serwisowych <xref:System.ServiceModel.ServiceContractAttribute> przez zastosowanie albo do interfejsów lub klas. Zaleca się zastosowanie atrybutu do interfejsu, a nie do klasy, ponieważ w ten sposób tworzy definicję kontraktu, który może być różnie implementowane przez dowolną liczbę klas. ASP.NET 2.0 obsługuje opcję stosowania atrybutu <xref:System.Web.Services.WebService> do interfejsów, a także klas. Jednak, jak już wspomniano, istnieje wada w ASP.NET 2.0, za pomocą <xref:System.Web.Services.WebService> którego Namespace parametr atrybutu nie ma wpływu, gdy ten atrybut jest stosowany do interfejsu, a nie klasy. Ponieważ ogólnie zaleca się modyfikowanie obszaru nazw usługi z wartości `http://tempuri.org`domyślnej, używając parametru Obszar nazw <xref:System.Web.Services.WebService> atrybutu, należy kontynuować definiowanie <xref:System.ServiceModel.ServiceContractAttribute> ASP.NET usług sieci Web, stosując atrybut do interfejsów lub klas.  
  
- Mają jak najmniejszy kod, jak to możliwe w metodach, za pomocą których te interfejsy są zdefiniowane. Niech delegują swoją pracę do innych klas. Nowe typy usług WCF może następnie również delegować ich pracy merytorycznej do tych klas.  
  
- Podaj jawne nazwy operacji `MessageName` usługi przy <xref:System.Web.Services.WebMethodAttribute>użyciu parametru .  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Jest to ważne, ponieważ domyślne nazwy operacji w ASP.NET różnią się od nazw domyślnych dostarczonych przez WCF. Podając jawne nazwy, można uniknąć polegania na domyślnych.  
  
- Nie należy implementować ASP.NET operacji usługi sieci Web metod polimorficznych, ponieważ WCF nie obsługuje implementowania operacji z metodami polimorficznymi.  
  
- Użyj, <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> aby podać jawne wartości dla nagłówków HTTP SOAPAction, za pomocą których żądania HTTP będą kierowane do metod.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Przyjęcie tego podejścia będzie obejść konieczności polegać na domyślne soapaction wartości używane przez ASP.NET i WCF są takie same.  
  
- Unikaj używania rozszerzeń SOAP. Jeśli rozszerzenia protokołu SOAP są wymagane, a następnie określić, czy celem, dla którego są one rozważane jest funkcja, która jest już dostarczona przez WCF. Jeśli rzeczywiście tak jest, to ponownie rozważyć wybór nie przyjąć WCF od razu.  
  
## <a name="state-management"></a>Zarządzanie państwem  
 Unikaj konieczności utrzymywania stanu w usługach. Nie tylko utrzymanie stanu mają tendencję do naruszenia skalowalności aplikacji, ale mechanizmy zarządzania stanem ASP.NET i WCF są bardzo różne, chociaż WCF obsługuje mechanizmy ASP.NET w trybie zgodności ASP.NET.  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 Podczas projektowania struktur typów danych, które mają być wysyłane i odbierane przez usługę, należy również projektować struktury reprezentujące różne typy wyjątków, które mogą wystąpić w ramach usługi, które można przekazać klientowi.  
  
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
  
 Daj takim klasom możliwość serializacji się do XML:  
  
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
  
 Klasy mogą następnie służyć do zapewnienia szczegółów <xref:System.Web.Services.Protocols.SoapException> dla jawnie zgłoszonych wystąpień:  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Te klasy wyjątków będą łatwo wielokrotnego pożytego z klasą WCF, <xref:System.ServiceModel.FaultException%601> aby`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpieczenia  
 Poniżej przedstawiono kilka zaleceń dotyczących zabezpieczeń.  
  
- Należy unikać używania ASP.NET 2.0 Profile, ponieważ ich używanie ograniczyłoby użycie trybu integracji ASP.NET, jeśli usługa została zmigrowana do WCF.  
  
- Unikaj używania list ACL do kontrolowania dostępu do usług, ponieważ ASP.NET usług sieci Web obsługuje listy ACL korzystające z internetowych usług informacyjnych (IIS), WCF nie — ponieważ ASP.NET usług sieci Web zależą od usług IIS dla hostingu, a WCF nie musi być hostowany w usługach IIS.  
  
- Należy rozważyć użycie ASP.NET 2.0 dostawców ról do autoryzowania dostępu do zasobów usługi.  
  
## <a name="see-also"></a>Zobacz też

- [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
