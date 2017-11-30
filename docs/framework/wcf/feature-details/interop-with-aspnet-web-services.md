---
title: "Współdziałanie z usługami ASP.NET w sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 933d1bdac8f6e3a9e2bec5278fe398696131678a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="interoperability-with-aspnet-web-services"></a>Współdziałanie z usługami ASP.NET w sieci Web
Współdziałanie między [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web i [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi sieci Web można osiągnąć przez zapewnienie, że usługi implementowane za pomocą obu tych technologii odpowiadają WS-I Basic Profile 1.1 specyfikacji. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Usługi sieci Web umożliwiających zgodne ze standardem WS-I Basic Profile 1.1 są zgodne z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania dostarczane przez system, <xref:System.ServiceModel.BasicHttpBinding>.  
  
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
  
 Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu powoduje, że komunikaty kierowane do metody oparte na w pełni kwalifikowaną nazwę elementu treści komunikatu protokołu SOAP, a nie od `SOAPAction` nagłówka HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa `SOAPAction` nagłówek HTTP dla routingu wiadomości.  
  
 Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje typu domyślnie jest semantycznie identyczne z pliku XML, do którego <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podana przestrzeni nazw XML jest jawnie zdefiniowany. Podczas określania typu danych do użycia z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]usługi sieci Web w oczekiwaniu przyjęcia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], wykonaj następujące czynności:  
  
-   Zdefiniuj typ, za pomocą klasy .NET Framework, a nie schematu XML.  
  
-   Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawnie zdefiniuj przestrzeń nazw dla typu. Nie należy dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób klasy .NET Framework jest można przetłumaczyć XML.  
  
-   Przyjmując takie podejście, powinno być możliwe dokonanie później klasy platformy .NET w kontraktach danych z uwzględnieniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klas są serializowane do przesłania. Typy używane w komunikatach przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usługi sieci Web mogą być przetwarzane jako kontraktów danych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji reaguje, między innymi korzyści, lepszej wydajności w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.  
  
 Unikaj używania opcji uwierzytelniania dostępnych przez Internet Information Services (IIS). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Klienci nie obsługują je. Jeśli usługa musi być zabezpieczony, użyj opcji dostarczanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ponieważ te opcje są niezawodne i są oparte na standardowych protokołów.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Wpływ na wydajność spowodowane ładowania ServiceModel HttpModule  
 W .NET Framework 3.0, usługi WCF `HttpModule` został zainstalowany w folderze głównym pliku Web.config tak, aby każda aplikacja ASP.NET została włączona WCF. To może mieć wpływ na wydajność, aby usunąć `ServiceModel` w pliku Web.config, jak pokazano w poniższym przykładzie.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi sieci Web ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
