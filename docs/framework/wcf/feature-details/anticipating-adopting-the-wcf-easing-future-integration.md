---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f81e158a5e7f897307c0c6d376dfe01dac127ead
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489599"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości
Jeśli obecnie za pomocą programu ASP.NET i przewidywać przy użyciu usługi WCF w przyszłości ten temat zawiera wskazówki, aby upewnić się, że nowych usług sieci Web ASP.NET zostanie współdziała również z aplikacji WCF.  
  
## <a name="general-recommendations"></a>Ogólne zalecenia  
 Przyjmuje ASP.NET 2.0 dla wszystkich nowych usług. W ten sposób umożliwi dostęp do ulepszenia i ulepszenia nowej wersji. Jednak będzie również umożliwiać umożliwiające korzystanie ze składników programu ASP.NET 2.0 oraz składniki usługi WCF w tej samej aplikacji.  
  
## <a name="protocols"></a>protokoły  
 Skorzystać z funkcji nowego składnika ASP.NET 2.0 weryfikowania zgodności ze standardem WS-I Basic Profile 1.1:  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Usługi sieci Web ASP.NET, które są zgodne ze standardem WS-I Basic Profile 1.1 będzie współdziałać z klienci WCF za pomocą usługi WCF wstępnie zdefiniowanych powiązań, <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Projektowanie usługi  
 Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> w pełni kwalifikowaną nazwę elementu treści komunikatu protokołu SOAP, a nie w nagłówku SOAPAction HTTP na podstawie atrybutu powoduje, że komunikaty kierowane do metody. Usługi WCF używa nagłówka SOAPAction HTTP dla routingu wiadomości.  
  
## <a name="data-representation"></a>Reprezentacja wartości danych  
 Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje typu domyślnie jest semantycznie identyczne z pliku XML, do którego <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podana przestrzeni nazw XML jest jawnie zdefiniowany. Podczas określania typu danych do użycia z usługami sieci Web ASP.NET w oczekiwaniu przyjmujące WCF w przyszłości, wykonaj następujące czynności:  
  
1.  Zdefiniuj typ, za pomocą klasy .NET Framework, a nie schematu XML.  
  
2.  Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawnie zdefiniuj przestrzeń nazw dla typu. Czy nie dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób klasy .NET Framework jest można przetłumaczyć XML.  
  
 Przyjmując takie podejście, powinno być możliwe dokonanie później klasy platformy .NET w kontraktach danych z uwzględnieniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klas są serializowane do przesłania. Typy używane w komunikatach przez usługi sieci Web ASP.NET będzie przetwarzany jako kontraktów danych przez aplikacje WCF reaguje między inne korzyści większą wydajność w aplikacji WCF.  
  
## <a name="security"></a>Zabezpieczenia  
 Unikaj używania opcji uwierzytelniania dostępnych przez Internet Information Services (IIS). Klienci WCF ich nie obsługują. Jeśli usługa musi być zabezpieczony, należy użyć opcji udostępniane przez usługi WCF, ponieważ te opcje są bardziej rozbudowane i są oparte na standardowych protokołów.  
  
## <a name="see-also"></a>Zobacz też  
 [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
