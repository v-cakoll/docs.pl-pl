---
title: Usługi jednokierunkowe
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: d567674baa92ad096b10a1199fa3f04f05939df5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991171"
---
# <a name="one-way-services"></a>Usługi jednokierunkowe
Domyślnym zachowaniem operacji usługi jest wzorzec żądanie-odpowiedź. W wzorcu żądanie-odpowiedź klient czeka na komunikat odpowiedzi, nawet jeśli operacja usługi jest reprezentowana w kodzie jako `void` Metoda. Z jednokierunkową operacją jest przesyłany tylko jeden komunikat. Odbiorca nie wysyła komunikatu odpowiedzi ani nie oczekuje takiego nadawcy.  
  
 Użyj wzorca projektowego jednokierunkowego:  
  
- Gdy klient musi wywoływać operacje i nie ma wpływ na wynik operacji na poziomie operacji.  
  
- Przy użyciu <xref:System.ServiceModel.NetMsmqBinding> <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> lub klasy. (Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [kolejki w programie WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)).  
  
 Gdy operacja jest jednokierunkowa, nie ma komunikatu odpowiedzi, aby uzyskać informacje o błędzie z powrotem do klienta. Można wykrywać błędy przy użyciu funkcji powiązania bazowego, takich jak Sesje niezawodne lub przez zaprojektowanie kontraktu usługi dupleksowej, który używa operacji 2 1-kierunkowych — jednokierunkowego kontraktu z klientem do usługi w celu wywołania operacji usługi i innej jednokierunkowa Umowa między usługą a klientem, dzięki czemu usługa może wysyłać błędy do klienta przy użyciu wywołania zwrotnego, które implementuje klient.  
  
 Aby utworzyć kontrakt usługi jednokierunkowej, zdefiniuj kontrakt usługi, Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej operacji i <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> ustaw właściwość na `true`, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Pełny przykład można znaleźć w przykładach [jednokierunkowych](../../../../docs/framework/wcf/samples/one-way.md) .  
  
## <a name="clients-blocking-with-one-way-operations"></a>Klienci blokujący operacje jednokierunkowe  
 Należy pamiętać, że podczas gdy pewne aplikacje jednokierunkowe zwracają się zaraz po zapisaniu danych wychodzących do połączenia sieciowego, w kilku scenariuszach implementacja powiązania lub usługi może spowodować, że klient programu WCF będzie blokował przy użyciu operacji jednokierunkowych. W aplikacjach klienckich WCF obiekt klienta WCF nie zwraca do momentu zapisania danych wychodzących do połączenia sieciowego. Dotyczy to wszystkich wzorców wymiany komunikatów, w tym operacji jednokierunkowych; oznacza to, że wszelkie problemy z zapisywaniem danych w transporcie uniemożliwiają zwrócenie przez klienta. W zależności od tego problemu wynikiem może być wyjątek lub opóźnienie wysyłania komunikatów do usługi.  
  
 Na przykład jeśli transport nie może znaleźć punktu końcowego, <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> wyjątek jest zgłaszany bez opóźnień. Istnieje również możliwość, że usługa nie będzie mogła odczytywać danych z sieci z jakiegoś powodu, co zapobiega zwracaniu przez nie operacji wysyłania przez klienta. W takich przypadkach, jeśli <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> zostanie przekroczony okres powiązania transportu klienta <xref:System.TimeoutException?displayProperty=nameWithType> , jest zgłaszany, ale nie do czasu przekroczenia limitu czasu. Możliwe jest również wyzwolenie tego wielu komunikatów w usłudze, że usługa nie może przetworzyć ich poza określonym punktem. W tym przypadku jest to również blok klienta jednokierunkowego do momentu, gdy usługa będzie mogła przetwarzać komunikaty lub do momentu wyrzucania wyjątku.  
  
 Inna odmiana to sytuacja, w której właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> usługi jest ustawiona na <xref:System.ServiceModel.ConcurrencyMode.Single> , a powiązanie używa sesji. W takim przypadku Dyspozytor wymusza porządkowanie komunikatów przychodzących (wymaganie sesji), które uniemożliwiają odczytanie kolejnych komunikatów z sieci do czasu przetworzenia przez usługę powyższej wiadomości dla danej sesji. Ponownie, bloki klienta, ale niezależnie od tego, czy występuje wyjątek, zależy od tego, czy usługa może przetwarzać dane oczekujące przed ustawieniami limitu czasu na kliencie.  
  
 Możesz złagodzić jakiś problem, wstawiając bufor między obiektem klienta a operacją wysyłania przez klienta. Na przykład za pomocą wywołań asynchronicznych lub przy użyciu kolejki komunikatów w pamięci można umożliwić szybkie zwracanie obiektu klienckiego. Obie metody mogą zwiększyć funkcjonalność, ale rozmiar puli wątków i kolejki komunikatów nadal wymusza limity.  
  
 Zaleca się, aby przeanalizować różne kontrolki usługi, a także na kliencie, a następnie przetestować scenariusze aplikacji, aby określić najlepszą konfigurację po obu stronach. Na przykład jeśli użycie sesji blokuje przetwarzanie komunikatów w usłudze <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> , można ustawić właściwość na <xref:System.ServiceModel.InstanceContextMode.PerCall> tak, aby każdy komunikat mógł być przetwarzany przez inne <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> wystąpienie usługi, i ustawić na <xref:System.ServiceModel.ConcurrencyMode.Multiple> w celu zezwalania więcej niż jednemu wątkowi na wysyłanie komunikatów jednocześnie. Innym podejściem jest zwiększenie przydziałów odczytu usługi i klienta.  
  
## <a name="see-also"></a>Zobacz także

- [Komunikacja jednokierunkowa](../../../../docs/framework/wcf/samples/one-way.md)
