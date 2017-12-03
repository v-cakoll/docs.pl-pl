---
title: "Wysyłanie i odbieranie błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5897d107fc27b56ffd1eb476dff1fa1d507f5de5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="sending-and-receiving-faults"></a>Wysyłanie i odbieranie błędów
Błędach SOAP przedstawienia warunku informacje o błędzie z usługi do klienta, a w przypadku dupleksu od klienta do usługi w sposób interoperacyjne. Zazwyczaj usługa definiuje zawartość błędów niestandardowych i określa, jakie operacje może zwracać je. (Aby uzyskać więcej informacji, zobacz [definiowanie i określanie usterek](../../../docs/framework/wcf/defining-and-specifying-faults.md).) W tym temacie omówiono sposób usługi lub dupleks klienta może wysyłać te błędy wystąpił odpowiedniego warunku błędu sposób i klienta lub usługę aplikacji obsługi tych błędów. Omówienie obsługi błędów w [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>Wysyłanie błędów SOAP  
 Zadeklarowany w błędach SOAP są te, w których ma operacji <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> , który określa typ niestandardowy błędu protokołu SOAP. Niezadeklarowany błędach SOAP są tymi, które nie są określone w umowie dla operacji.  
  
### <a name="sending-declared-faults"></a>Wysyłanie błędów zadeklarowana  
 Aby wysłać zadeklarowane błędu protokołu SOAP, wykrywanie warunku błędu, dla którego jest błędu protokołu SOAP i zgłosić nową <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> gdzie parametr typu jest nowy obiekt typu określonego w <xref:System.ServiceModel.FaultContractAttribute> dla tej operacji. W poniższym przykładzie pokazano sposób użycia <xref:System.ServiceModel.FaultContractAttribute> Aby określić, że `SampleMethod` operacji może zwrócić błąd SOAP z typem szczegółów `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 W celu przekazania `GreetingFault` informacje o błędzie do klienta, catch warunku błędu odpowiednie i zgłosić nową <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault` o nowe `GreetingFault` obiektu jako argument, jak w poniższym przykładzie kodu. Jeśli klient jest [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji klienckiej go napotka to jako zarządzanym wyjątku, której typ jest <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Wysyłanie błędów niezadeklarowany  
 Wysyłanie błędów niezadeklarowany może być bardzo przydatne szybkie diagnozowanie i debugowania problemów w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacje, ale jego użyteczności jako narzędzie do debugowania jest ograniczona. Ogólnie rzecz biorąc, gdy jej debugowanie jest zalecane używanie <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwości. Gdy ta wartość jest ustawiona na wartość true, klienci wystąpić błędów, takich jak <xref:System.ServiceModel.FaultException%601> wyjątki typu <xref:System.ServiceModel.ExceptionDetail>.  
  
> [!IMPORTANT]
>  Ponieważ zarządzane wyjątki może ujawnić informacje o wewnętrznych aplikacji, ustawianie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` zezwolić na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientów, aby uzyskać informacje dotyczące wyjątków operacji wewnętrzny usługi, w tym osobiście do zidentyfikowania lub inne poufne informacje.  
>   
>  W związku z tym ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` jest zalecane tylko w sposób tymczasowo debugowania aplikacji usługi. Ponadto WSDL dla metody, która zwraca nieobsługiwanych wyjątków w ten sposób zarządzanych nie zawiera kontraktu dla <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienci muszą oczekują możliwości nieznany błąd protokołu SOAP (Powrót do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientów jako <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektów) można uzyskać informacji o debugowaniu poprawnie.  
  
 Aby wysłać niezadeklarowany błędu protokołu SOAP, throw <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektu (to znaczy nie typ ogólny <xref:System.ServiceModel.FaultException%601>) i przekazać ciąg do konstruktora. To jest narażony na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji klienckich jako element zgłaszany <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> wyjątku, której ten ciąg jest dostępna przez wywołanie metody <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> metody.  
  
> [!NOTE]
>  Jeśli zadeklarować typu ciąg błędu protokołu SOAP i zgłosić to w usłudze jako <xref:System.ServiceModel.FaultException%601> gdzie parametr typu jest <xref:System.String?displayProperty=nameWithType> wartość ciągu jest przypisany do <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> właściwości i nie jest dostępny z <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Obsługa błędów  
 W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientów i błędach SOAP występujących podczas komunikacji interesujące dla aplikacji klienckich są zgłaszane jako zarządzane wyjątki. Gdy istnieje wiele wyjątków, które mogą wystąpić podczas wykonywania programu, aplikacje przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] model programowania klienta można oczekiwać, że do obsługi wyjątków następujące dwa typy wyniku komunikacji.  
  
-   <xref:System.TimeoutException>  
  
-   <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException>obiekty są zgłaszane, gdy operacja przekroczy określony limit czasu.  
  
 <xref:System.ServiceModel.CommunicationException>obiekty są zgłaszane po warunku błędu niektóre możliwe do odzyskania komunikacji na usługi lub klienta.  
  
 <xref:System.ServiceModel.CommunicationException> Klasa ma dwie ważne typy pochodne <xref:System.ServiceModel.FaultException> i ogólnych <xref:System.ServiceModel.FaultException%601> typu.  
  
 <xref:System.ServiceModel.FaultException>wyjątki są zgłaszane odebrania odbiornik błędów, który nie jest oczekiwany lub określone w umowie operacji; Zazwyczaj ten błąd występuje podczas debugowania aplikacji i usługa ma <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ustawioną właściwość `true`.  
  
 <xref:System.ServiceModel.FaultException%601>Po odebraniu w odpowiedzi na operację dwukierunkowe usterek, określonego w kontrakt operacji na komputerze klienckim są zgłaszane wyjątki (czyli metody z <xref:System.ServiceModel.OperationContractAttribute> atrybutem <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> ustawioną `false`).  
  
> [!NOTE]
>  Gdy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługa ma <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ustawioną właściwość `true` klienta napotka to jako niezadeklarowany <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klientów można przechwycić tego określonego błędu lub obsługi błędów w bloku catch dla <xref:System.ServiceModel.FaultException>.  
  
 Zwykle tylko <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException>, i <xref:System.ServiceModel.CommunicationException> wyjątki są przydatne do klientów i usług.  
  
> [!NOTE]
>  Oczywiście wystąpić inne wyjątki. Nieoczekiwany wyjątków należą poważnej awarii, takich jak <xref:System.OutOfMemoryException?displayProperty=nameWithType>; zazwyczaj aplikacje nie należy przechwytywać tych metod.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Przechwytywanie wyjątków błędów w odpowiedniej kolejności  
 Ponieważ <xref:System.ServiceModel.FaultException%601> pochodną <xref:System.ServiceModel.FaultException>, i <xref:System.ServiceModel.FaultException> pochodną <xref:System.ServiceModel.CommunicationException>, ważne jest, aby przechwytywać tych wyjątków w prawidłowej kolejności. Jeśli na przykład masz try/catch bloku, w którym najpierw catch <xref:System.ServiceModel.CommunicationException>, wszystkie określone i nieokreślony błędach SOAP są obsługiwane istnieje; bloków catch kolejnych do obsługi niestandardowej <xref:System.ServiceModel.FaultException%601> wyjątek nigdy nie są wywoływane.  
  
 Należy pamiętać, że jedna operacja może zwrócić dowolną liczbę błędów określonego. Każdy awarii jest typem unikatowy i muszą być obsługiwane oddzielnie.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Obsługa wyjątków podczas zamykania kanału  
 Większość poprzedniego dyskusji związana z błędy wysyłane w trakcie przetwarzania komunikatów aplikacji, czyli wiadomości jawnie wysłane przez klienta, gdy aplikacja klient wywołuje operacje na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta.  
  
 Nawet w przypadku lokalnych obiektów usuwania obiektu można wywołać lub maskować wyjątki, które występują w trakcie odtwarzania procesu. Podobnie może wystąpić, gdy używasz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektów klienta. Podczas wywoływania operacji wysyłania wiadomości przez nawiązane połączenie. Zamknięcie kanału można generują wyjątki, jeśli połączenie nie można prawidłowo zamknięty lub jest już zamknięty, nawet jeśli wszystkie operacje zwrócił poprawnie.  
  
 Zazwyczaj kanały obiektu klienta są zamknięte w jednym z następujących sposobów:  
  
-   Gdy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta zostanie odtworzony.  
  
-   Gdy aplikacja kliencka wywołuje <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
-   Gdy aplikacja kliencka wywołuje <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
-   Gdy aplikacja kliencka wywołuje operację który jest operacją zakończenia sesji.  
  
 We wszystkich przypadkach zamknięcie kanału nakazuje kanału, aby zamknąć wszystkie podstawowej kanałów, które może wysyłać wiadomości do obsługi złożonych funkcji na poziomie aplikacji. Na przykład gdy kontrakt wymaga sesje powiązania próbuje ustanowić sesję przez wymianę komunikaty z kanału usługi, dopóki nie zostanie nawiązane sesji. Podczas zamykania kanał podstawowego kanału sesji powiadamia usługę zakończenia sesji. W tym przypadku jeśli kanału już została przerwana, zamknięta, lub jest bezużyteczne (na przykład, gdy jest odłączony kabel sieciowy), kanału klienta nie może poinformować kanału usługi, sesja zostanie zakończona, który może spowodować wyjątek.  
  
### <a name="abort-the-channel-if-necessary"></a>Przerwij kanału w razie potrzeby  
 Ponieważ zamknięcie kanału można zgłaszają wyjątki, następnie, zalecane jest aby oprócz przechwytywanie wyjątków błędów we właściwej kolejności, ważne jest, aby przerwać kanału, który został użyty w wywołania w bloku catch.  
  
 Jeśli usterki przekazuje informacje o błędach specyficznych dla operacji i będzie możliwe, że inne może być używany, jest niepotrzebna przerwania kanał (mimo że te przypadki są rzadko). We wszystkich innych przypadkach zaleca się, że przerwać kanału. Dla przykładu, która przedstawia wszystkie punkty, zobacz [oczekiwane wyjątki](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 Poniższy przykład kodu pokazuje sposób obsługi wyjątków błędu protokołu SOAP w podstawowej aplikacji klienckiej, w tym zadeklarowane usterek i błędów niezadeklarowany.  
  
> [!NOTE]
>  Ten przykładowy kod nie używa `using` utworzenia. Ponieważ zamykania kanałów może zgłaszać wyjątki, zaleca się aplikacje tworzą [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta pierwszy, a następnie otwórz, używania i Zamknij [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, w tym samym bloku try. Aby uzyskać więcej informacji, zobacz [Przegląd klienta programu WCF](../../../docs/framework/wcf/wcf-client-overview.md) i [unikanie problemów z instrukcją Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultException%601>  
 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>  
 [Oczekiwane wyjątki](../../../docs/framework/wcf/samples/expected-exceptions.md)  
 [Unikanie problemów z instrukcją Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)
