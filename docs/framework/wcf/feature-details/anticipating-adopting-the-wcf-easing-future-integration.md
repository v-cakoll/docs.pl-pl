---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: c6e749c32947a4159d6bfd56c4d30a06f6ef0b7f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316339"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości
Jeśli obecnie używają platformy ASP.NET i przewidywać, przy użyciu usługi WCF w przyszłości, w tym temacie przedstawiono wskazówki, aby upewnić się, że nowych usług sieci Web programu ASP.NET będą działać poprawnie wraz z aplikacji WCF.  
  
## <a name="general-recommendations"></a>Ogólne zalecenia  
 Przyjęcie programu ASP.NET 2.0 dla wszelkie nowe usługi. Ten sposób umożliwi dostęp do usprawnień i ulepszeń, nowych wersji. Jednak także pozwoli to na możliwość wykorzystania składniki programu ASP.NET 2.0 wraz z składniki usługi WCF w tej samej aplikacji.  
  
## <a name="protocols"></a>Protokoły  
 Użyj nowych funkcji programu ASP.NET 2.0 dotyczące weryfikacji zgodności WS-I Basic Profile 1.1:  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Usługi sieci Web platformy ASP.NET, które odpowiadają WS-I Basic Profile 1.1 będzie współdziałać z klientów programu WCF za pomocą usługi WCF wstępnie zdefiniowanych powiązań, <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Tworzenie usługi  
 Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu powoduje, że wiadomości kierowane do metody oparte na w pełni kwalifikowana nazwa elementu treści komunikatu protokołu SOAP, a nie nagłówek SOAPAction HTTP. Usługi WCF używa nagłówka SOAPAction HTTP służącą do rozesłania wiadomości.  
  
## <a name="data-representation"></a>Reprezentacja danych  
 Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje semantycznie taka sama jak XML, do którego jest typem domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typem parametru przestrzeni nazw XML jest jawnie zdefiniowany. Podczas definiowania typu danych do użytku z usługami sieci Web platformy ASP.NET w oczekiwaniu przyjmujące WCF w przyszłości, wykonaj następujące czynności:  
  
1. Definiowanie typu przy użyciu klas .NET Framework, a nie schematu XML.  
  
2. Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawne definiowanie przestrzeni nazw dla typu. Czy nie dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeń nazw w celu kontrolowania, jak klasy .NET Framework ma być przetłumaczone na XML.  
  
 Przyjmując takie podejście, powinno być możliwe zapewnienie później klas .NET w kontraktach danych dodając <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klasy są serializowane w celu przesłania go. Typy używane w komunikatach przez usługi sieci Web platformy ASP.NET będzie do przetworzenia jako kontraktów danych przez aplikacje WCF reaguje, oraz inne korzyści, lepszej wydajności w aplikacjach usługi WCF.  
  
## <a name="security"></a>Zabezpieczenia  
 Należy unikać używania opcji uwierzytelniania udostępniane przez Internetowe usługi informacyjne (IIS). Klienci WCF nie obsługują je. Jeśli usługa musi być bezpieczne, użyj opcji dostępnych przez architekturę WCF, ponieważ te opcje są bardziej rozbudowane i bazują na standardowych protokołów.  
  
## <a name="see-also"></a>Zobacz także

- [Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie migracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
