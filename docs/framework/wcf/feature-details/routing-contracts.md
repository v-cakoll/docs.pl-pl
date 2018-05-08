---
title: Kontrakty routingu
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 64ebb673b17159967bb4acd4e3a5e0a3f89142f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="routing-contracts"></a>Kontrakty routingu
Kontrakty routingu zdefiniuj wzorce wiadomości, które może przetworzyć usługi routingu.  Każdej umowy jest bez typu i umożliwia usłudze komunikat bez wiedzy o schematu wiadomości lub akcji. Dzięki temu usługa routingu objęty rozesłać komunikaty bez dodatkowej konfiguracji, aby uzyskać szczegółowe informacje na temat podstawowej wiadomości przesyłane.  
  
## <a name="routing-contracts"></a>Kontrakty routingu  
 Ponieważ usługa routingu akceptuje obiektu ogólnego wiadomości WCF, najważniejszych brany pod uwagę podczas wybierania kontrakt jest kształtu kanału, który będzie używany podczas komunikacji z klientami i usługami. Podczas przetwarzania komunikatów, usługa routingu używa pomp symetryczne wiadomości, więc zazwyczaj kształtu dla ruchu przychodzącego kontraktu musi być zgodna kształtu wychodzącego kontraktu. Istnieją jednak przypadki, w którym dyspozytora Model usług można zmodyfikować kształtów, na przykład w przypadku Dyspozytor konwertuje Kanał dupleksowy do kanału żądanie odpowiedź lub usuwa obsługę sesji z kanału, kiedy nie jest wymagana i nie jest używana (czyli gdy **SessionMode.Allowed**, konwertowania **IInputSessionChannel** do **IInputChannel**).  
  
 Do obsługi tych pomp wiadomości, usługa routingu umożliwia kontrakty w <xref:System.ServiceModel.Routing> przestrzeni nazw, które muszą być używane podczas definiowania punktów końcowych usługi używane przez usługi routingu. Umowy te są bez typu, który umożliwia odbieranie dowolnego typu komunikatu lub akcji i pozwala usługa routingu do obsługi komunikatów bez wiedzy o schemacie określonego komunikatu. Aby uzyskać więcej informacji na temat kontraktów używane przez usługę Routing zobacz [kontrakty routingu](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Umów, usługa routingu znajdują się w <xref:System.ServiceModel.Routing> przestrzeni nazw i są opisane w poniższej tabeli.  
  
|Kontrakt|Kształt|Kształtu kanału|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true<br /><br /> Ustawienie właściwości IsOneWay = true|IInputChannel -> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode.Required<br /><br /> AsyncPattern = true<br /><br /> Ustawienie właściwości IsOneWay = true|IInputSessionChannel -> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true|Element IReplyChannel -> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> Ustawienie właściwości IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|IDuplexSessionChannel -> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa routingu](http://msdn.microsoft.com/library/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)  
 [Wprowadzenie do routingu](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
