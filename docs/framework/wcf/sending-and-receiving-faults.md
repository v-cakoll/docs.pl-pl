---
title: Wysyłanie i odbieranie błędów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: f093229af96cba679959fa052bd6b5809d347f4b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606025"
---
# <a name="sending-and-receiving-faults"></a>Wysyłanie i odbieranie błędów
Błędach SOAP obejmują warunku informacje o błędzie z usługi do klienta, a w przypadku dwukierunkowego od klienta do usługi w sposób interoperacyjny. Zazwyczaj usługa definiuje zawartość błędów niestandardowych i określa, jakie operacje można przywrócić je. (Aby uzyskać więcej informacji, zobacz [definiowanie i określanie błędów](../../../docs/framework/wcf/defining-and-specifying-faults.md).) W tym temacie omówiono, jak usługi lub klienta dwukierunkowego może wysyłać te błędy Jeśli nastąpiła odpowiadającego warunku błędu i jak klient lub aplikacja usługi obsługuje te błędy. Aby uzyskać omówienie obsługi błędów w aplikacji Windows Communication Foundation (WCF), zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>Wysyłanie błędów SOAP  
 Zadeklarowane w błędach SOAP są te, w których jest operacją <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> , który określa typ niestandardowy błędu protokołu SOAP. Niezadeklarowany błędach SOAP są te, które nie zostały określone w umowie dla danej operacji.  
  
### <a name="sending-declared-faults"></a>Wysyłanie błędów zadeklarowanych  
 Do wysyłania zadeklarowane błąd protokołu SOAP, wykrywanie warunku błędu, dla którego jest błąd protokołu SOAP i zgłosić nową <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> gdzie parametr typu jest nowy obiekt o typie określonym w <xref:System.ServiceModel.FaultContractAttribute> dla tej operacji. Poniższy przykład kodu pokazuje użycie <xref:System.ServiceModel.FaultContractAttribute> Aby określić, że `SampleMethod` operacji może zwrócić błąd protokołu SOAP z typem szczegółów `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 W celu przekazania `GreetingFault` informacje o błędzie do klienta, przechwytywać warunek odpowiedni komunikat o błędzie i zgłaszać nowe <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault` dzięki nowemu `GreetingFault` obiekt jako argumentu, jak w poniższym przykładzie kodu. Jeśli klient znajduje się aplikacja klienta WCF, go to napotyka jako zarządzanego wyjątku, gdy typ jest <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Wysyłanie błędów niezadeklarowany  
 Wysyłanie błędów niezadeklarowany może być bardzo przydatne szybko zdiagnozować i debugowanie problemów w aplikacji WCF, ale jego użyteczność, jako narzędzie debugowania jest ograniczona. Ogólnie rzecz biorąc, jeśli debugowanie jest zaleca się używanie <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwości. Ta wartość jest ustawiona na wartość true, klienci wystąpić takie błędy jako <xref:System.ServiceModel.FaultException%601> wyjątków typu <xref:System.ServiceModel.ExceptionDetail>.  
  
> [!IMPORTANT]
>  Ponieważ zarządzane wyjątki mogą ujawniać informacje o wewnętrznych aplikacji, ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` może pozwolić na WCF klientom uzyskanie informacji o wyjątkach operację usługi wewnętrznej, w tym osobiście danych osobowych lub inne poufne informacje.  
>   
>  W związku z tym, ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` jest zalecane tylko jako sposób tymczasowo debugowania aplikacji usługi. Ponadto pliku WSDL dla zarządzanych przy użyciu metody, która zwraca nieobsługiwanych wyjątków w ten sposób nie zawiera kontrakt dla <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienci muszą oczekują możliwości nieznany błąd protokołu SOAP (zwracane do klientów programu WCF jako <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektów) Aby uzyskać informacje o debugowaniu prawidłowo.  
  
 Aby wysłać niezadeklarowany błąd protokołu SOAP, throw <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektu (oznacza to, że nie ogólny typ <xref:System.ServiceModel.FaultException%601>) i przekazać ciągu do konstruktora. To jest widoczna dla aplikacji klienckich programu WCF jako zgłoszenia <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> wyjątków, na których ten ciąg jest dostępny, wywołując <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> metody.  
  
> [!NOTE]
>  Jeśli zadeklarować typu ciąg błędu protokołu SOAP, a następnie generują to w usłudze jako <xref:System.ServiceModel.FaultException%601> gdzie parametr typu jest <xref:System.String?displayProperty=nameWithType> wartość ciągu jest przypisywana do <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> właściwości i nie jest dostępny z <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Obsługa błędów  
 Klienci WCF błędach SOAP, które występują podczas komunikacji, które mają znaczenie w odniesieniu do aplikacji klienckich są zgłaszane jako zarządzane wyjątki. Dostępnych jest wiele wyjątków, które mogą wystąpić podczas wykonywania programu, aplikacje za pomocą modelu programowania klienta WCF można oczekiwać, że obsłużyć wyjątki następujących dwóch typów komunikacji w wyniku.  
  
- <xref:System.TimeoutException>  
  
- <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException> obiekty są zgłaszane, gdy operacja przekracza określony limit czasu.  
  
 <xref:System.ServiceModel.CommunicationException> obiekty są zgłaszane po jakiegoś warunku błędu komunikacji możliwe do odzyskania na usługi lub klienta.  
  
 <xref:System.ServiceModel.CommunicationException> Klasa ma dwie ważne typy pochodne <xref:System.ServiceModel.FaultException> i ogólnego <xref:System.ServiceModel.FaultException%601> typu.  
  
 <xref:System.ServiceModel.FaultException> są zgłaszane wyjątki, gdy odbiornik otrzymuje błędów, nie jest oczekiwana lub określone w umowie operacji; Zwykle dzieje się tak podczas debugowania aplikacji i usługa ma <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwością `true`.  
  
 <xref:System.ServiceModel.FaultException%601> Po odebraniu błędów, który jest określony w kontrakt operacji w odpowiedzi na dwukierunkowe operacji na komputerze klienckim są zgłaszane wyjątki (czyli metody z <xref:System.ServiceModel.OperationContractAttribute> atrybutem <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> równa `false`).  
  
> [!NOTE]
>  Gdy usługa WCF ma <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwością `true` klienta napotka to jako niezadeklarowany <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klientów można przechwytywać tego określonego błędu lub obsługi błędów w bloku catch dla <xref:System.ServiceModel.FaultException>.  
  
 Zwykle tylko <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException>, i <xref:System.ServiceModel.CommunicationException> wyjątki mają znaczenie w odniesieniu do klientów i usług.  
  
> [!NOTE]
>  Oczywiście wystąpić inne wyjątki. Nieoczekiwane wyjątki obejmują katastrofalnych awarii, takich jak <xref:System.OutOfMemoryException?displayProperty=nameWithType>; zazwyczaj aplikacje nie należy przechwytywać tych metod.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Przechwytuj wyjątki błędów w odpowiedniej kolejności  
 Ponieważ <xref:System.ServiceModel.FaultException%601> pochodzi od klasy <xref:System.ServiceModel.FaultException>, i <xref:System.ServiceModel.FaultException> pochodzi od klasy <xref:System.ServiceModel.CommunicationException>, ważne jest, aby przechwytywać te wyjątki w odpowiedniej kolejności. Jeśli na przykład, posiadasz try/catch block, w którym najpierw catch <xref:System.ServiceModel.CommunicationException>, wszystkie określone i są obsługiwane w błędach SOAP nieokreślony do obsługi niestandardowej istnieje; wszelkich bloków catch kolejnych <xref:System.ServiceModel.FaultException%601> wyjątek nigdy nie są wywoływane.  
  
 Należy pamiętać, że jedna operacja może zwrócić dowolną liczbę błędów określony. Każdy błąd to unikatowy typ i musi być obsługiwane osobno.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Obsługa wyjątków podczas zamykania kanał  
 Większość poprzednich dyskusji związana z błędów wysyłanych w trakcie przetwarzania komunikatów aplikacji, oznacza to, że komunikaty jawnie wysłane przez klienta, gdy aplikacja kliencka wywołuje operacje na obiekcie klienta WCF.  
  
 Nawet w przypadku obiektów lokalnych usuwania obiektu można zgłosić lub maskować wyjątki, które występują podczas odtwarzania procesu. Podobne może wystąpić, gdy używasz obiekty klienta programu WCF. Podczas wywoływania operacji są wysyłane komunikaty za pośrednictwem nawiązane połączenie. Zamknięcie kanału może generować wyjątki, jeśli połączenie nie może prawidłowo zamknięte lub jest już zamknięty, nawet, jeśli wszystkie operacje zwracana prawidłowo.  
  
 Zazwyczaj kanały obiektu klienta są zamknięte w jednej z następujących sposobów:  
  
- Gdy obiekt klienta WCF zostanie odtworzony.  
  
- Kiedy aplikacja kliencka wywołuje <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
- Kiedy aplikacja kliencka wywołuje <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
- Kiedy aplikacja kliencka wywołuje operacją, jest operacją powodujący zakończenie sesji.  
  
 We wszystkich przypadkach zamknięcie kanału powoduje, że kanał, aby zamknąć bazowego kanały, które może wysyłać komunikaty do obsługi złożonych funkcji na poziomie aplikacji. Na przykład gdy kontrakt wymaga użycia sesji powiązanie podejmuje próbę ustanowienia sesji przez wymianę wiadomości z kanału usługi, dopóki nie zostanie utworzona sesja. Podczas zamykania kanał podstawowego kanału sesji powiadamia usługę, sesja zostanie zakończona. W tym przypadku Jeśli kanał już została przerwana, zamknięta, lub w przeciwnym razie nie nadaje się (na przykład, gdy kabel sieciowy jest odłączony), kanału klienta nie informuje o kanału usługi, który sesja zostanie zakończona, i może spowodować wyjątek.  
  
### <a name="abort-the-channel-if-necessary"></a>Przerwij kanału, w razie potrzeby  
 Ponieważ zamknięcie kanału może generować wyjątki, następnie zalecane jest, oprócz przechwytywania wyjątków błędów w odpowiedniej kolejności, ważne jest, aby przerwać kanału, który był używany w wywołania w bloku catch.  
  
 Jeśli będzie to możliwe, że inne ich używać błędu powoduje błąd informacje specyficzne dla operacji, nie ma potrzeby przerwania kanału (mimo że te przypadki występują rzadko). We wszystkich innych przypadkach zalecane jest, aby przerwać kanału. Dla przykładu, który pokazuje wszystkie te punkty, zobacz [oczekiwane wyjątki](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 Poniższy przykład kodu pokazuje sposób obsługi wyjątków błędu protokołu SOAP w podstawowej aplikacji klienckiej, tym zadeklarowane błędów i niezadeklarowany błędów.  
  
> [!NOTE]
>  Ten przykładowy kod nie używać `using` konstruowania. Ponieważ zamykania kanałów mogą zgłaszać wyjątki, zaleca się, że aplikacje tworzą kliencie WCF Użyj pierwszego, a następnie otwórz i zamknij blok try klienta WCF, w tym samym. Aby uzyskać więcej informacji, zobacz [Przegląd klienta programu WCF](../../../docs/framework/wcf/wcf-client-overview.md) i [Użyj Zamknij i Abort, aby zwolnić zasoby klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Oczekiwane wyjątki](../../../docs/framework/wcf/samples/expected-exceptions.md)
- [Użyj Zamknij i Przerwij, aby zwolnić zasoby klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)
