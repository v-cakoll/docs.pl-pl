---
title: Współdziałanie z usługami ASP.NET w sieci Web
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 8a0737a36989dd8bc6f5d5670555c7b2218798bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interoperability-with-aspnet-web-services"></a>Współdziałanie z usługami ASP.NET w sieci Web
Współdziałanie między [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web i usług sieci Web Windows Communication Foundation (WCF) można osiągnąć przez zapewnienie, że usługi implementowane za pomocą obu tych technologii odpowiadają WS-I Basic Profile 1.1 specyfikacji. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Usługi sieci Web umożliwiających zgodne ze standardem WS-I Basic Profile 1.1 są zgodne z klienci WCF za pomocą powiązania dostarczane przez system WCF <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Użyj [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] możliwość dodania <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> atrybuty do interfejsu, a nie na klasę i zapisywania klasy do zaimplementowania interfejsu, jak pokazano w poniższym kodzie próbki.  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 Ta opcja jest preferowana, ponieważ interfejs <xref:System.Web.Services.WebService> atrybutu stanowi kontraktu dla operacji wykonywanych przez usługę mogą być ponownie używane z różnymi klasami, które mogą implementować ten sam kontrakt na różne sposoby.  
  
 Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu powoduje, że komunikaty kierowane do metody oparte na w pełni kwalifikowaną nazwę elementu treści komunikatu protokołu SOAP, a nie od `SOAPAction` nagłówka HTTP. Używa WCF `SOAPAction` nagłówek HTTP dla routingu wiadomości.  
  
 Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje typu domyślnie jest semantycznie identyczne z pliku XML, do którego <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podana przestrzeni nazw XML jest jawnie zdefiniowany. Podczas określania typu danych do użycia z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]usługi sieci Web w oczekiwaniu przyjmowanie WCF, wykonaj następujące czynności:  
  
-   Zdefiniuj typ, za pomocą klasy .NET Framework, a nie schematu XML.  
  
-   Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawnie zdefiniuj przestrzeń nazw dla typu. Nie należy dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób klasy .NET Framework jest można przetłumaczyć XML.  
  
-   Przyjmując takie podejście, powinno być możliwe dokonanie później klasy platformy .NET w kontraktach danych z uwzględnieniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klas są serializowane do przesłania. Typy używane w komunikatach przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usługi sieci Web mogą być przetwarzane jako kontraktów danych aplikacji WCF, reaguje, między innymi korzyści większą wydajność w aplikacji WCF.  
  
 Unikaj używania opcji uwierzytelniania dostępnych przez Internet Information Services (IIS). Klienci WCF ich nie obsługują. Jeśli usługi musi być zabezpieczony, użyj opcji dostępnych przez usługi WCF, ponieważ te opcje są niezawodne i są oparte na standardowych protokołów.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Wpływ na wydajność spowodowane ładowania ServiceModel HttpModule  
 W .NET Framework 3.0, usługi WCF `HttpModule` został zainstalowany w folderze głównym pliku Web.config tak, aby każda aplikacja ASP.NET została włączona WCF. To może mieć wpływ na wydajność, aby usunąć `ServiceModel` w pliku Web.config, jak pokazano w poniższym przykładzie.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
