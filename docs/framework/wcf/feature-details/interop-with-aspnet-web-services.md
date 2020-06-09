---
title: Współdziałanie z usługami ASP.NET w sieci Web
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: f38209ffe2161e58528a108b29e730665a65da37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598869"
---
# <a name="interoperability-with-aspnet-web-services"></a>Współdziałanie z usługami ASP.NET w sieci Web
Współdziałanie między usługami sieci Web ASP.NET Web Services i Windows Communication Foundation (WCF) można uzyskać, upewniając się, że usługi zaimplementowane przy użyciu obu technologii są zgodne ze specyfikacją WS-I Basic Profile 1,1. Usługi sieci Web ASP.NET, które są zgodne ze standardem WS-I Basic Profile 1,1, współdziałają z klientami programu WCF przy użyciu powiązania dostarczonego przez system <xref:System.ServiceModel.BasicHttpBinding> .  
  
 Użyj opcji ASP.NET 2,0, aby dodać <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> atrybuty i do interfejsu, a nie do klasy, i napisać klasę, aby zaimplementować interfejs, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Użycie tej opcji jest preferowane, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybutem stanowi kontrakt dla operacji wykonywanych przez usługę, które mogą być ponownie używane z różnymi klasami, które mogą implementować ten sam kontrakt na różne sposoby.  
  
 Należy unikać używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu, aby komunikaty były kierowane do metod opartych na w pełni kwalifikowanej nazwie elementu treści komunikatu protokołu SOAP, a nie w `SOAPAction` nagłówku HTTP. Funkcja WCF używa `SOAPAction` nagłówka HTTP do routingu komunikatów.  
  
 KOD XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializowany jest typ domyślnie jest semantycznie identyczny z XML, do którego jest <xref:System.Runtime.Serialization.DataContractSerializer> serializowany typ, pod warunkiem, że przestrzeń nazw dla kodu XML jest jawnie zdefiniowana. Podczas definiowania typu danych do użycia z usługami ASP. NETWeb w celu przewidzenia wdrożenia WCF należy wykonać następujące czynności:  
  
- Zdefiniuj typ przy użyciu klas .NET Framework, a nie schematu XML.  
  
- Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, używając tej ostatniej, aby jawnie zdefiniować przestrzeń nazw dla tego typu. Nie dodawaj dodatkowych atrybutów z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób tłumaczenia klasy .NET Framework na XML.  
  
- Przyjmując takie podejście, powinno być możliwe późniejsze przekazanie klas .NET do kontraktów danych z dodaniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez znacząco zmiany kodu XML, do którego klasy są serializowane do transmisji. Typy używane w komunikatach przez usługi sieci Web ASP.NET mogą być przetwarzane jako Kontrakty danych przez aplikacje WCF, a wśród innych korzyści, lepsza wydajność w aplikacjach WCF.  
  
 Należy unikać używania opcji uwierzytelniania zapewnianych przez Internet Information Services (IIS). Klienci WCF nie obsługują tych funkcji. Jeśli usługa musi być zabezpieczona, użyj opcji dostarczonych przez program WCF, ponieważ te opcje są niezawodne i są oparte na protokołach standardowych.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Wpływ na wydajność spowodowany ładowaniem modułu ServiceModel HttpModule  
 W .NET Framework 3,0 `HttpModule` Funkcja WCF została zainstalowana w głównym pliku Web. config w taki sposób, że każda aplikacja ASP.NET była włączona w ramach funkcji WCF. Może to mieć wpływ na wydajność, dlatego można usunąć `ServiceModel` plik Web. config, jak pokazano w poniższym przykładzie.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web](config-wcf-service-with-aspnet-web-service.md)
