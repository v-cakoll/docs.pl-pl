---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 6392194b3124c999031123225dcc28c8de6171e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576528"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości
Jeśli używasz usługi ASP.NET już dzisiaj i przewidujesz korzystanie z programu WCF w przyszłości, w tym temacie znajdują się wskazówki pozwalające zapewnić zgodność nowych usług sieci Web ASP.NET ze wszystkimi aplikacjami WCF.  
  
## <a name="general-recommendations"></a>Ogólne zalecenia  
 Przyjmij ASP.NET 2,0 dla nowych usług. Pozwoli to zapewnić dostęp do ulepszeń i ulepszeń nowej wersji. Jednak umożliwi to również możliwość korzystania ze składników ASP.NET 2,0 ze składnikami WCF w tej samej aplikacji.  
  
## <a name="protocols"></a>Protokoły  
 Użyj nowej funkcji ASP.NET 2.0 do sprawdzania zgodności z profilem Basic WS-I 1,1:  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Usługi sieci Web ASP.NET zgodne ze standardem WS-I Basic Profile 1,1 będą współdziałać z klientami WCF przy użyciu wstępnie zdefiniowanych powiązań programu WCF <xref:System.ServiceModel.BasicHttpBinding> .  
  
## <a name="service-development"></a>Opracowywanie usług  
 Należy unikać używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu, aby komunikaty były kierowane do metod opartych na w pełni kwalifikowanej nazwie elementu treści komunikatu protokołu SOAP, a nie w nagłówku HTTP SoapAction. Funkcja WCF używa nagłówka HTTP SOAPAction dla komunikatów routingu.  
  
## <a name="data-representation"></a>Reprezentacja danych  
 KOD XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializowany jest typ domyślnie jest semantycznie identyczny z XML, do którego jest <xref:System.Runtime.Serialization.DataContractSerializer> serializowany typ, pod warunkiem, że przestrzeń nazw dla kodu XML jest jawnie zdefiniowana. Podczas definiowania typu danych do użycia z usługami sieci Web ASP.NET w celu przewidzenia wdrożenia WCF w przyszłości wykonaj następujące czynności:  
  
1. Zdefiniuj typ przy użyciu klas .NET Framework, a nie schematu XML.  
  
2. Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, używając tej ostatniej, aby jawnie zdefiniować przestrzeń nazw dla tego typu. Nie dodawaj dodatkowych atrybutów z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób tłumaczenia klasy .NET Framework na XML.  
  
 Przyjmując takie podejście, powinno być możliwe późniejsze przekazanie klas .NET do kontraktów danych z dodaniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez znacząco zmiany kodu XML, do którego klasy są serializowane do transmisji. Typy używane w komunikatach przez usługi sieci Web ASP.NET będą mogły być przetwarzane jako Kontrakty danych przez aplikacje WCF, a wśród innych korzyści, lepsza wydajność aplikacji WCF.  
  
## <a name="security"></a>Zabezpieczenia  
 Należy unikać używania opcji uwierzytelniania zapewnianych przez Internet Information Services (IIS). Klienci WCF nie obsługują tych funkcji. Jeśli usługa musi być zabezpieczona, użyj opcji dostarczonych przez program WCF, ponieważ te opcje są bogatsze i są oparte na protokołach standardowych.  
  
## <a name="see-also"></a>Zobacz też

- [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości](anticipating-adopting-wcf-migration.md)
