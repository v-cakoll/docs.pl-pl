---
title: "Usługi jednokierunkowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12913a9afc0003b041b260379a55e469273c5910
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="one-way-services"></a>Usługi jednokierunkowe
Domyślne zachowanie operacji usługi jest wzorzec żądanie odpowiedź. We wzorcu żądanie odpowiedź, klient oczekuje na komunikat odpowiedzi nawet wtedy, gdy operacja usługi jest reprezentowana w kodzie jako `void` metody. Z operacji jednokierunkowych są przesyłane tylko jeden komunikat. Odbiornik nie wysyła komunikat odpowiedzi nie jest nadawca oczekiwany jeden.  
  
 Użyj wzorca projektowego jednokierunkowe:  
  
-   Gdy klient musi wywołać operacji i nie ma wpływu na wynik operacji na poziomie operacji.  
  
-   Korzystając z <xref:System.ServiceModel.NetMsmqBinding> lub <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> klasy. ([!INCLUDE[crabout](../../../../includes/crabout-md.md)] tego scenariusza, zobacz [kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Podczas operacji jest jednokierunkowa, nie ma odpowiedzi do przenoszenia informacje o błędzie do klienta. Warunki błędów można wykryć za pomocą funkcji podstawowych powiązania, takich jak niezawodnej sesji lub Projektując kontrakt usługi dwustronnej, która używa dwóch operacji jednokierunkowych — kontraktu jednokierunkowego od klienta do usługi do wywołania operacji usługi, a drugi jednokierunkowe kontraktu między usługą i klienta, dzięki czemu usługa może wysyłać błędy wstecz do klienta przy użyciu wywołania zwrotnego, który implementuje klienta.  
  
 Aby utworzyć kontrakt usługi jednokierunkowe, zdefiniuj dany kontrakt usługi, zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji i ustaw <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true`, jak pokazano w poniższym kodzie próbki.  
  
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
  
 Pełny przykład, zobacz [jednokierunkowe](../../../../docs/framework/wcf/samples/one-way.md) próbki.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Klienci z blokowaniem za pomocą operacji jednokierunkowych  
 Ważne jest, aby należy pamiętać, że mimo że niektóre aplikacje jednokierunkowe zwraca jak wychodzących dane są zapisywane do połączenia z siecią, w kilku scenariuszach wdrażania powiązania lub usługi może spowodować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta mają być blokowane przy użyciu jednokierunkowego operacje. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje klienckie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie może zwracać obiektu klienta do momentu danych wychodzących został zapisany do połączenia sieciowego. Dotyczy to wszystkich wzorców wymiany wiadomości, w tym przypadku operacji jednokierunkowych; oznacza to, że wszystkie problem z zapisywaniem się, że dane do transportu uniemożliwi zwracanie przez klienta. W zależności od tego problemu, wynik może być wyjątku lub opóźnienia podczas wysyłania komunikatów do usługi.  
  
 Na przykład, jeśli transport nie można odnaleźć punktu końcowego <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> wyjątek bez dużego opóźnienia. Jednak również jest możliwe, że usługa jest nie można odczytać danych ze przewodowy jakiegoś powodu, co uniemożliwia transport klienta operacji wysyłania zwracanie. W takich przypadkach Jeśli <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> okresu dla transportu klienta przekroczeniu powiązania <xref:System.TimeoutException?displayProperty=nameWithType> jest zgłaszany —, ale nie do czasu został przekroczony limit czasu. Istnieje również możliwość uruchomienie tak wiele komunikatów w punkcie usług, że usługa nie może ich przetworzyć po pewnym. W takim przypadku, bloki jednokierunkowe klienta usługi może przetwarzać komunikatów lub do momentu jest zgłaszany wyjątek.  
  
 Zmiana innego jest sytuacja, w którym usługa <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.ServiceModel.ConcurrencyMode.Single> i powiązania używa sesji. W takim przypadku Dyspozytor wymusza porządkowanie dla komunikatów przychodzących (wymaganie sesje), co zapobiega kolejnych komunikatów odczytywane poza siecią, dopóki usługa została przetworzona poprzedni komunikat dla tej sesji. Ponownie, bloki klienta, ale czy wystąpi wyjątek zależy od tego, czy usługa jest w stanie przetwarzać dane oczekiwania przed ustawienia limitu czasu na kliencie.  
  
 Można ograniczyć niektóre ten problem, wstawiając buforu między obiektem klienta i operację wysyłania transportu klienta. Na przykład obiekt klienta szybko powrócić można włączyć za pomocą wywołania asynchroniczne lub kolejki komunikatów w pamięci. W obu przypadkach efekt może zwiększyć funkcji, ale rozmiar puli wątków i kolejki wiadomości nadal wymuszać ograniczenia.  
  
 Jest to zalecane, zamiast tego należy zbadać różnych formantów w usłudze, a także na kliencie, a następnie przetestować scenariusze aplikacji w celu ustalenia najlepszej konfiguracji po obu stronach. Na przykład, jeśli użycie sesji blokuje przetwarzanie komunikatów w usłudze, możesz ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.InstanceContextMode.PerCall> tak, aby każdy komunikat może przetworzone przez wystąpienie innej usługi i ustaw <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> do <xref:System.ServiceModel.ConcurrencyMode.Multiple> Aby umożliwić więcej niż jeden wątek na wysyłanie wiadomości w czasie. Innym rozwiązaniem jest zwiększenie odczytu przydziały powiązania usługi i klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Jednokierunkowe](../../../../docs/framework/wcf/samples/one-way.md)
