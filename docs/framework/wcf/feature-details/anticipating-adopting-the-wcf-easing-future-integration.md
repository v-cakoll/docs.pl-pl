---
title: "Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccf6e5363da872d3902c12713bd19f5820370428
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości
Jeśli obecnie za pomocą programu ASP.NET, a przewiduje się przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w przyszłości, w tym temacie przedstawiono wskazówki dotyczące upewnij się, że nowe usługi sieci Web ASP.NET będzie współpracować razem z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.  
  
## <a name="general-recommendations"></a>Ogólne zalecenia  
 Przyjmuje ASP.NET 2.0 dla wszystkich nowych usług. W ten sposób umożliwi dostęp do ulepszenia i ulepszenia nowej wersji. Jednak również umożliwi umożliwiające korzystanie ze składników programu ASP.NET 2.0 razem z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składniki w tej samej aplikacji.  
  
## <a name="protocols"></a>protokoły  
 Skorzystać z funkcji nowego składnika ASP.NET 2.0 weryfikowania zgodności ze standardem WS-I Basic Profile 1.1:  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Usługi sieci Web ASP.NET, które są zgodne ze standardem WS-I Basic Profile 1.1 będzie współdziałać z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wstępnie zdefiniowanych powiązań, <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Projektowanie usługi  
 Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> w pełni kwalifikowaną nazwę elementu treści komunikatu protokołu SOAP, a nie w nagłówku SOAPAction HTTP na podstawie atrybutu powoduje, że komunikaty kierowane do metody. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa nagłówka SOAPAction HTTP dla routingu wiadomości.  
  
## <a name="data-representation"></a>Reprezentacja wartości danych  
 Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje typu domyślnie jest semantycznie identyczne z pliku XML, do którego <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podana przestrzeni nazw XML jest jawnie zdefiniowany. Gdy Definiowanie typu danych do użycia z sieci Web ASP.NET usług w oczekiwaniu przyjęcia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w przyszłości, wykonaj następujące czynności:  
  
1.  Zdefiniuj typ, za pomocą klasy .NET Framework, a nie schematu XML.  
  
2.  Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawnie zdefiniuj przestrzeń nazw dla typu. Czy nie dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób klasy .NET Framework jest można przetłumaczyć XML.  
  
 Przyjmując takie podejście, powinno być możliwe dokonanie później klasy platformy .NET w kontraktach danych z uwzględnieniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klas są serializowane do przesłania. Typy używane w komunikatach przez usługi sieci Web ASP.NET będzie można przetwarzać jako kontraktów danych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji reaguje, między innymi korzyści, lepszej wydajności w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.  
  
## <a name="security"></a>Zabezpieczenia  
 Unikaj używania opcji uwierzytelniania dostępnych przez Internet Information Services (IIS). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Klienci nie obsługują je. Jeśli usługa musi być zabezpieczony, użyj opcji dostarczanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ponieważ te opcje są bardziej rozbudowane i są oparte na standardowych protokołów.  
  
## <a name="see-also"></a>Zobacz też  
 [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie przyszłych migracji.](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
