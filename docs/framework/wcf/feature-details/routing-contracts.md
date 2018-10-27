---
title: Kontrakty routingu
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 17bdd4556533b33b635f80b9aec3f16d0f256843
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191012"
---
# <a name="routing-contracts"></a>Kontrakty routingu
Kontrakty routingu zdefiniować wzorców wiadomości, które może przetworzyć usługa routingu.  Każdej umowy jest formatów i umożliwia usłudze komunikat bez znajomości schematu wiadomości lub akcji. Dzięki temu usługa routingu do ogólnej kierowanie komunikatów w postaci bez dodatkowej konfiguracji, aby uzyskać szczegółowe informacje na temat podstawowych komunikaty przesyłane.  
  
## <a name="routing-contracts"></a>Kontrakty routingu  
 Ponieważ usługa routingu akceptuje to obiekt rodzajowy wiadomości WCF, najważniejsze brany pod uwagę podczas wybierania kontrakt jest kształtu kanału, który będzie używany podczas komunikacji z klientami i usługami. Podczas przetwarzania komunikatów, usługa routingu używa pompy komunikatów symetryczne, więc zazwyczaj kształt przychodzącego kontraktu musi być zgodna kształt wychodzącego kontraktu. Jednakże istnieją przypadki, gdzie dyspozytora Model usług można zmodyfikować kształtów, na przykład w przypadku dispatcher konwertuje Kanał dupleksowy do kanału "żądanie-odpowiedź" lub usuwa obsługę sesji z kanału, gdy nie jest wymagana i nie jest używana (to znaczy gdy **SessionMode.Allowed**, konwertowania **IInputSessionChannel** do **IInputChannel**).  
  
 Na potrzeby obsługi tych pompy komunikatów, usługa routingu udostępnia umów <xref:System.ServiceModel.Routing> przestrzeni nazw, które muszą być używane podczas definiowania punktów końcowych usługi używane przez usługę routingu. Umowy te są formatów, która umożliwia odbieranie dowolnego typu komunikatu lub akcji i umożliwia usługa routingu do obsługi wiadomości, bez znajomości schematu szczegółowy komunikat o błędzie. Aby uzyskać więcej informacji na temat umów używane przez usługę routingu, zobacz [kontrakty routingu](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Kontrakty udostępniane przez usługę routingu znajdują się w <xref:System.ServiceModel.Routing> przestrzeni nazw i są opisane w poniższej tabeli.  
  
|Kontrakt|Kształt|Kształtu kanału|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true<br /><br /> Ustawienie właściwości IsOneWay = true|IInputChannel -> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode.Required<br /><br /> AsyncPattern = true<br /><br /> Ustawienie właściwości IsOneWay = true|IInputSessionChannel -> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true|IReplyChannel -> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> Ustawienie właściwości IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|IDuplexSessionChannel -> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa routingu](../../../../docs/framework/wcf/feature-details/routing-service.md)  
 [Wprowadzenie do routingu](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
