---
title: Kontrakty routingu
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 69dff2c82f67a16d51e11a92052c59672a054e04
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601078"
---
# <a name="routing-contracts"></a>Kontrakty routingu
Kontrakty routingu definiują wzorce komunikatów, które usługa routingu może przetworzyć.  Każdy kontrakt jest beztypu i umożliwia usłudze otrzymywanie wiadomości bez znajomości schematu lub akcji wiadomości. Dzięki temu usługa routingu ogólnie kieruje komunikaty bez dodatkowej konfiguracji dla określonych źródłowych komunikatów, które są przesyłane.  
  
## <a name="routing-contracts"></a>Kontrakty routingu  
 Ponieważ usługa routingu akceptuje ogólny obiekt komunikatów WCF, najważniejszym zagadnieniem podczas wybierania kontraktu jest kształt kanału, który będzie używany podczas komunikowania się z klientami i usługami. Podczas przetwarzania wiadomości usługa routingu używa symetrycznej pompki komunikatów, dlatego kształt kontraktu przychodzącego musi być zgodny z kształtem kontraktu wychodzącego. Istnieją jednak przypadki, w których Dyspozytor modelu usług może modyfikować kształty, na przykład gdy Dyspozytor przekształci kanał dupleksowy w kanale żądanie-odpowiedź lub usuwa obsługę sesji z kanału, gdy nie jest to wymagane i nie jest używana (to jest, w trakcie **sesjimode. dozwolone**, konwertowanie **IInputSessionChannel** na **IInputChannel**).  
  
 Aby zapewnić obsługę tych pomp komunikatów, usługa routingu udostępnia kontrakty w <xref:System.ServiceModel.Routing> przestrzeni nazw, które muszą być używane podczas definiowania punktów końcowych usługi używanych przez usługę routingu. Te kontrakty są beztypu, co umożliwia otrzymanie dowolnego typu komunikatu lub akcji, a także umożliwia usłudze routingu obsługę komunikatów bez znajomości określonego schematu komunikatów. Aby uzyskać więcej informacji na temat kontraktów używanych przez usługę routingu, zobacz [Kontrakty routingu](routing-contracts.md).  
  
 Kontrakty udostępniane przez usługę routingu znajdują się w <xref:System.ServiceModel.Routing> przestrzeni nazw i są opisane w poniższej tabeli.  
  
|Kontrakt|Kształt|Kształt kanału|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode. dozwolone<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel — > IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode. Required<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel — > IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode. dozwolone<br /><br /> AsyncPattern = true|IReplyChannel — > IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode = SessionMode. Required<br /><br /> CallbackContract = typeof (ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow (parametru TransactionFlowOption. dozwolone)|IDuplexSessionChannel — > IDuplexSessionChannel|  
  
## <a name="see-also"></a>Zobacz też

- [Usługa routingu](routing-service.md)
- [Wprowadzenie do routingu](routing-introduction.md)
