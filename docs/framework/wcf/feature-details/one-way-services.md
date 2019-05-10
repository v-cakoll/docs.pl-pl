---
title: Usługi jednokierunkowe
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: b29585eabcc2549876f4b50e6b6e55a7f8ef2eee
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621343"
---
# <a name="one-way-services"></a>Usługi jednokierunkowe
Domyślnym zachowaniem operacji usługi jest wzorzec "żądanie-odpowiedź". We wzorcu "żądanie-odpowiedź" klient czeka na komunikat odpowiedzi, nawet, jeśli operacja usługi jest reprezentowana w kodzie jako `void` metody. Za pomocą operacji jednokierunkowych są przesyłane tylko jeden komunikat. Odbiornik nie wysyła komunikat odpowiedzi nie jest nadawca oczekiwany jeden.  
  
 Użyj wzorca projektowego jednokierunkowe:  
  
- Gdy klient musi wywoływanie operacji i nie występuje w wyniku operacji na poziomie operacji.  
  
- Korzystając z <xref:System.ServiceModel.NetMsmqBinding> lub <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> klasy. (Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Gdy operacja jest jednokierunkowa, nie ma odpowiedzi do przenoszenia informacji o błędzie do klienta. Warunki błędów może wykryć, korzystając z funkcji podstawowych powiązania, takich jak niezawodnej sesji lub Projektując kontrakt usługi dwustronnej, które używa dwóch operacji jednokierunkowych — kontraktu jednokierunkowego od klienta do usługi do wywołania operacji usługi, a drugi jednokierunkowa Umowę między usługą i klienta, aby usługa może wysyłać błędy wstecz do klienta przy użyciu wywołania zwrotnego, który implementuje klienta.  
  
 Aby utworzyć kontrakt usługi jednokierunkowej, definiowanie kontraktu usługi, usługi, zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji, a następnie ustaw <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true`, jak pokazano w poniższym przykładowym kodzie.  
  
```  
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
  
 Aby uzyskać kompletny przykład, zobacz [jednokierunkowe](../../../../docs/framework/wcf/samples/one-way.md) próbki.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Klienci z blokowaniem za pomocą operacji jednokierunkowych  
 Należy weź pod uwagę, że mimo że niektóre aplikacje jednokierunkowe zwraca zaraz po danych wychodzących są zapisywane do połączenia sieciowego w kilku scenariuszach wdrożenia powiązania lub usługi może spowodować klienta WCF zablokować używanie operacji jednokierunkowych. W aplikacjach klienckich usługi WCF obiekt klienta WCF nie zwraca do momentu połączenia sieciowego został zapisany danych wychodzących. Ta zasada obowiązuje dla wszystkich typów wymiany wiadomości, łącznie z jednokierunkową; oznacza to, że każdy problem zapisu czy dane do transportu uniemożliwi zwracanie przez klienta. W zależności od problemu, może się zdarzyć, wyjątek lub opóźnienie podczas wysyłania komunikatów do usługi.  
  
 Na przykład, jeśli transport nie można odnaleźć punktu końcowego <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> wyjątek bez dużego opóźnienia. Jednak jest również możliwe, że usługa jest nie można odczytać danych poza przewodowy jakiegoś powodu, co uniemożliwia transport klienta wysyłać operację, zwraca. W takich przypadkach Jeśli <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> kropki na transport klienta wiązanie zostanie przekroczony, <xref:System.TimeoutException?displayProperty=nameWithType> zgłaszany —, ale nie do czasu został przekroczony limit czasu. Istnieje również możliwość fire tak wiele wiadomości powinna być usługa, że usługa nie może przetworzyć je po pewnym. W tym przypadku, bloki klienta jednokierunkowe aż usługa może przetwarzać komunikatów, lub do momentu jest zgłaszany wyjątek.  
  
 Inna wersja jest sytuacja, w której usługa <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.ServiceModel.ConcurrencyMode.Single> i powiązanie używa sesji. W tym przypadku Dyspozytor wymusza kolejność na komunikaty przychodzące (wymaganie sesji), co zapobiega kolejnych komunikatów odczytywanych z sieci, aż usługa został przetworzony poprzedni komunikat w ramach danej sesji. Ponownie bloków klienta, ale czy wystąpi wyjątek zależy od tego, czy usługa jest w stanie przetwarzać dane oczekiwania przed ustawienia limitu czasu na komputerze klienckim.  
  
 Można ograniczyć część tego problemu, wstawiając bufora między obiektu klienta i operację wysyłania transportu klienta. Na przykład obiekt klienta szybko powrócić można włączyć za pomocą wywołania asynchronicznego lub kolejki komunikatów w pamięci. Oba podejścia może zwiększyć funkcjonalność, ale rozmiar puli wątków i kolejki komunikatów nadal wymuszanie limitów.  
  
 Jest to zalecane, zamiast tego należy zbadać różne formanty w usłudze, a także na komputerze klienckim, a następnie przetestować swoich scenariuszy aplikacji, aby określić najlepszą konfigurację po obu stronach. Na przykład, jeśli korzystanie z sesji blokuje przetwarzanie komunikatów w usłudze, możesz ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.InstanceContextMode.PerCall> tak, aby każdy komunikat może przetwarzane przez utworzone wystąpienie innej usługi i ustaw <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> do <xref:System.ServiceModel.ConcurrencyMode.Multiple> Aby zezwolić na więcej niż jeden wątek do wysyłania wiadomości w czasie. Innym rozwiązaniem jest zwiększyć te limity odczytu powiązań usługi i klienta.  
  
## <a name="see-also"></a>Zobacz także

- [Komunikacja jednokierunkowa](../../../../docs/framework/wcf/samples/one-way.md)
