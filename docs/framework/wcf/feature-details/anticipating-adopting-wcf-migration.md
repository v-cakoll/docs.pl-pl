---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: b43f509bd49ebe89d7ed0be4c37b3ed179aaeb8c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576502"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości
Aby zapewnić łatwiejsze Migrowanie nowych aplikacji ASP.NET do usługi WCF, postępuj zgodnie z powyższymi zaleceniami, a także z poniższymi zaleceniami.  
  
## <a name="protocols"></a>Protokoły  
 Wyłącz obsługę protokołu SOAP 1,2 w programie ASP.NET 2.0:  
  
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
  
 Jest to zalecane, ponieważ WCF wymaga komunikatów zgodnych z różnymi protokołami, takimi jak SOAP 1,1 i SOAP 1,2, aby przejść przy użyciu różnych punktów końcowych. Jeśli usługa sieci Web ASP.NET 2,0 jest skonfigurowana do obsługi zarówno protokołu SOAP 1,1, jak i protokołu SOAP 1,2, który jest domyślną konfiguracją, nie można migrować do przodu do pojedynczego punktu końcowego WCF na oryginalnym adresie, który będzie miał być zgodny ze wszystkimi istniejącymi klientami usługi sieci Web ASP.NET. Ponadto wybranie protokołu SOAP 1,2 zamiast 1,1 będzie bardziej poważnie ograniczyć Clientele usługi.  
  
## <a name="service-development"></a>Opracowywanie usług  
 Funkcja WCF umożliwia definiowanie kontraktów usługi przez zastosowanie ich <xref:System.ServiceModel.ServiceContractAttribute> do interfejsów lub do klas. Zaleca się stosowanie atrybutu do interfejsu, a nie do klasy, ponieważ w ten sposób tworzy definicję kontraktu, który może być wdrożony przez dowolną liczbę klas. ASP.NET 2,0 obsługuje opcję zastosowania <xref:System.Web.Services.WebService> atrybutu do interfejsów, a także klas. Jednak jak już wspomniano, istnieje wada w ASP.NET 2,0, przez który parametr Namespace <xref:System.Web.Services.WebService> atrybutu nie ma wpływu, gdy ten atrybut jest stosowany do interfejsu, a nie klasy. Ponieważ ogólnie zaleca się zmodyfikowanie przestrzeni nazw usługi z wartości domyślnej, `http://tempuri.org` przy użyciu parametru przestrzeni nazw <xref:System.Web.Services.WebService> atrybutu, jeden powinien kontynuować Definiowanie usług sieci Web ASP.NET przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do interfejsów lub do klas.  
  
- Mieć możliwie najmniejszą ilość kodu w metodach, za pomocą których są zdefiniowane te interfejsy. Umożliwiają delegowanie pracy do innych klas. Nowe typy usługi WCF mogą następnie delegować swoją merytoryczną służbę do tych klas.  
  
- Podaj jawne nazwy dla operacji usługi przy użyciu `MessageName` parametru <xref:System.Web.Services.WebMethodAttribute> .  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Jest to ważne, ponieważ domyślne nazwy operacji w programie ASP.NET różnią się od domyślnych nazw dostarczonych przez program WCF. Dostarczając jawne nazwy, można uniknąć polegania na domyślnych.  
  
- Nie należy implementować operacji usługi sieci Web ASP.NET za pomocą metod polimorficznych, ponieważ WCF nie obsługuje implementowania operacji przy użyciu metod polimorficznych.  
  
- Użyj, <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> Aby podać jawne wartości w nagłówkach HTTP SoapAction, za pomocą których żądania HTTP będą kierowane do metod.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Zastosowanie tej metody spowoduje obejście tego, że należy zależeć od domyślnych wartości SOAPAction używanych przez ASP.NET i WCF.  
  
- Unikaj używania rozszerzeń SOAP. Jeśli wymagane są rozszerzenia SOAP, określ, czy cel, dla którego są brane pod uwagę, jest funkcją, która jest już świadczona przez WCF. Jeśli tak naprawdę ma to miejsce, należy ponownie rozważyć wybór, aby nie zastosować funkcji WCF od razu.  
  
## <a name="state-management"></a>Zarządzanie stanem  
 Unikaj konieczności zachowywania stanu usług. Nie tylko jest utrzymany stan, który ma na celu złamanie skalowalności aplikacji, ale mechanizmy zarządzania Stanami ASP.NET i WCF są bardzo różne, chociaż WCF obsługuje mechanizmy ASP.NET w trybie zgodności ASP.NET.  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 Podczas projektowania struktur typów danych, które mają być wysyłane i odbierane przez usługę, należy również projektować struktury reprezentujące różne typy wyjątków, które mogą wystąpić w ramach usługi, która może być przekazana do klienta.  
  
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
  
 Nadaj tym klasom możliwość serializacji do kodu XML:  
  
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
  
 Klasy mogą następnie służyć do podania szczegółów dla jawnie zgłoszonych <xref:System.Web.Services.Protocols.SoapException> wystąpień:  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Te klasy wyjątków będą łatwe do ponownego użycia z <xref:System.ServiceModel.FaultException%601> klasą WCF w celu wygenerowania nowego`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpieczenia  
 Poniżej przedstawiono niektóre zalecenia dotyczące zabezpieczeń.  
  
- Unikaj używania profilów ASP.NET 2,0, ponieważ użycie ich może ograniczyć użycie trybu integracji ASP.NET, jeśli usługa została zmigrowana do programu WCF.  
  
- Unikaj używania list ACL do kontrolowania dostępu do usług, ponieważ usługi sieci Web ASP.NET obsługują listy ACL korzystające z Internet Information Services (IIS), WCF nie — ponieważ usługi sieci Web ASP.NET są zależne od usług IIS do hostingu, a usługa WCF nie musi być hostowana w usługach IIS.  
  
- Należy rozważyć użycie dostawców roli ASP.NET 2,0 do autoryzacji dostępu do zasobów usługi.  
  
## <a name="see-also"></a>Zobacz też

- [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości](anticipating-adopting-the-wcf-easing-future-integration.md)
