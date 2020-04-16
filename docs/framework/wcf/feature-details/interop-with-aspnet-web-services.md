---
title: Współdziałanie z usługami ASP.NET w sieci Web
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464092"
---
# <a name="interoperability-with-aspnet-web-services"></a>Współdziałanie z usługami ASP.NET w sieci Web
Współdziałanie między usługami sieci Web ASP.NET i usługami sieci Web Windows Communication Foundation (WCF) można osiągnąć, zapewniając, że usługi wdrożone przy użyciu obu technologii są zgodne ze specyfikacją WS-I Basic Profile 1.1. ASP.NET usługi sieci Web zgodne z profilem podstawowym WS-I 1.1 są interoperacyjne z klientami <xref:System.ServiceModel.BasicHttpBinding>WCF przy użyciu powiązania dostarczonego przez system WCF, .  
  
 Użyj ASP.NET 2.0 opcja dodawania <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> i atrybuty do interfejsu, a nie do klasy i zapisywania klasy do zaimplementowania interfejsu, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
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
  
 Za pomocą tej opcji jest preferowane, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybutem stanowi kontrakt dla operacji wykonywanych przez usługę, które mogą być ponownie używane z różnych klas, które mogą implementować tego samego kontraktu na różne sposoby.  
  
 Należy unikać <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> używania atrybutu, aby wiadomości były kierowane do metod opartych na w `SOAPAction` pełni kwalifikowanej nazwie elementu treści wiadomości SOAP, a nie nagłówka HTTP. WCF używa `SOAPAction` nagłówka HTTP do routingu wiadomości.  
  
 Kod XML, <xref:System.Xml.Serialization.XmlSerializer> w którym serializuje typ domyślnie jest semantycznie <xref:System.Runtime.Serialization.DataContractSerializer> identyczny z XML, w którym serializuje typ, pod warunkiem, że obszar nazw dla XML jest jawnie zdefiniowany. Podczas definiowania typu danych do użytku z usługami ASP.NETWeb w oczekiwaniu na przyjęcie WCF wykonaj następujące czynności:  
  
- Zdefiniuj typ przy użyciu klas programu .NET Framework, a nie schematu XML.  
  
- Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, używając tej ostatniej, aby jawnie zdefiniować obszar nazw dla typu. Nie należy dodawać <xref:System.Xml.Serialization> dodatkowych atrybutów z obszaru nazw, aby kontrolować sposób tłumaczenia klasy .NET Framework na język XML.  
  
- Przyjmując to podejście, należy później dokonać .NET klas do kontraktów danych <xref:System.Runtime.Serialization.DataContractAttribute> z <xref:System.Runtime.Serialization.DataMemberAttribute> dodatkiem i bez znaczącej zmiany XML, do którego klasy są serializowane do transmisji. Typy używane w wiadomościach przez ASP.NET usług sieci Web mogą być przetwarzane jako kontrakty danych przez aplikacje WCF, co daje między innymi lepszą wydajność w aplikacjach WCF.  
  
 Należy unikać korzystania z opcji uwierzytelniania oferowanych przez internetowe usługi informacyjne (IIS). Klienci WCF nie obsługują ich. Jeśli usługa musi być zabezpieczona, należy użyć opcji dostarczonych przez WCF, ponieważ te opcje są niezawodne i są oparte na standardowych protokołów.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Wpływ na wydajność spowodowany ładowaniem urządzenia ServiceModel HttpModule  
 W .NET Framework 3.0 WCF `HttpModule` został zainstalowany w głównym pliku Web.config, tak aby każda aplikacja ASP.NET była włączona WCF. Może to wpłynąć na `ServiceModel` wydajność, dzięki czemu można usunąć plik Web.config, jak pokazano w poniższym przykładzie.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
