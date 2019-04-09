---
title: Współdziałanie z usługami ASP.NET w sieci Web
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: c6fec1d520cd251473d8840b7b1afe879002a04c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108579"
---
# <a name="interoperability-with-aspnet-web-services"></a>Współdziałanie z usługami ASP.NET w sieci Web
Współdziałanie między [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web i usług sieci Web Windows Communication Foundation (WCF), można osiągnąć przez zapewnienie, że usługi implementowane przy użyciu obie technologie są zgodne z WS-I Basic Profile 1.1 specyfikacji. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Sieci Web usługi, które odpowiadają WS-I Basic Profile 1.1 są zgodne z klientów programu WCF za pomocą powiązania dostarczane przez system WCF <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Użyj [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] możliwość dodania <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> atrybuty do interfejsu, a nie klasę w celu zapisywania klasy do zaimplementowania interfejsu, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Użycie tej opcji jest preferowana, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybut definiuje kontrakt dla operacji wykonywanych przez usługę, która może być ponownie używane z różnymi klasami, które mogą implementować tej samej umowy na różne sposoby.  
  
 Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu powoduje, że wiadomości kierowane do metody oparte na w pełni kwalifikowana nazwa elementu treści komunikatu protokołu SOAP, a nie od `SOAPAction` nagłówka HTTP. Korzysta z usługi WCF `SOAPAction` nagłówka HTTP służącą do rozesłania wiadomości.  
  
 Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje semantycznie taka sama jak XML, do którego jest typem domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typem parametru przestrzeni nazw XML jest jawnie zdefiniowany. Podczas definiowania typu danych do użycia z usługą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]usług, oczekując na przyjęcie WCF sieci Web, wykonaj następujące czynności:  
  
-   Definiowanie typu przy użyciu klas .NET Framework, a nie schematu XML.  
  
-   Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawne definiowanie przestrzeni nazw dla typu. Nie należy dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeń nazw w celu kontrolowania, jak klasy .NET Framework ma być przetłumaczone na XML.  
  
-   Przyjmując takie podejście, powinno być możliwe zapewnienie później klas .NET w kontraktach danych dodając <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klasy są serializowane w celu przesłania go. Typy używane w wiadomości według [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web mogą być przetwarzane tak kontraktów danych przez aplikacje WCF, reaguje pozwala między innymi, lepszej wydajności w aplikacjach usługi WCF.  
  
 Należy unikać używania opcji uwierzytelniania udostępniane przez Internetowe usługi informacyjne (IIS). Klienci WCF nie obsługują je. Jeśli usługa musi zostać zabezpieczony, użyj opcji dostępnych przez architekturę WCF, ponieważ te opcje są niezawodne i bazują na standardowych protokołów.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Wpływ na wydajność spowodowane przez ładowanie HttpModule modelu ServiceModel  
 W .NET Framework 3.0, WCF `HttpModule` został zainstalowany w folderze głównym pliku Web.config, tak, aby każda aplikacja ASP.NET została włączona WCF. To może mieć wpływ na wydajność, dzięki czemu możesz usunąć `ServiceModel` w pliku Web.config, jak pokazano w poniższym przykładzie.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w Internecie](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
