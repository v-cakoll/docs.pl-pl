---
title: Wysyłanie i odbieranie błędów
description: Dowiedz się, jak usługa lub klient dupleksowy może wysyłać błędy SOAP w przypadku wystąpienia błędu i sposobu, w jaki aplikacja klienta lub usługi obsługuje te błędy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 23f63fde2755a29cd545d3aefe699cad8dbecb3b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244325"
---
# <a name="sending-and-receiving-faults"></a>Wysyłanie i odbieranie błędów

Błędy protokołu SOAP umożliwiają przekazywanie informacji o stanie błędu z usługi do klienta i w przypadku dupleksu od klienta do usługi w sposób interoperacyjny. Zazwyczaj usługa definiuje niestandardową zawartość błędów i określa, które operacje mogą je zwrócić. (Aby uzyskać więcej informacji, zobacz [Definiowanie i określanie błędów](defining-and-specifying-faults.md)). W tym temacie omówiono, jak usługa lub klient dupleksowy może wysyłać te błędy, gdy wystąpił odpowiedni warunek błędu i sposób obsługi tych błędów przez klienta lub aplikację usługi. Omówienie obsługi błędów w aplikacjach Windows Communication Foundation (WCF) zawiera temat [określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="sending-soap-faults"></a>Wysyłanie błędów SOAP

Zadeklarowane błędy protokołu SOAP to te, w których operacja ma <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> niestandardowy typ błędu SOAP. Niezadeklarowane błędy SOAP to te, które nie są określone w kontrakcie dla operacji.

### <a name="sending-declared-faults"></a>Wysyłanie zadeklarowanych błędów

Aby wysłać zadeklarowany błąd protokołu SOAP, należy wykryć warunek błędu, dla którego jest odpowiedni błąd protokołu SOAP, i zgłosić nowe <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> miejsce, gdzie parametr typu jest nowym obiektem typu określonego w <xref:System.ServiceModel.FaultContractAttribute> dla tej operacji. Poniższy przykład kodu pokazuje użycie, <xref:System.ServiceModel.FaultContractAttribute> Aby określić, że `SampleMethod` operacja może zwrócić błąd protokołu SOAP z typem szczegółowym `GreetingFault` .

[!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
[!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

Aby przekazać `GreetingFault` Informacje o błędzie do klienta, należy przechwytywać odpowiedni warunek błędu i zgłosić nowy <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> Typ `GreetingFault` z nowym `GreetingFault` obiektem jako argument, jak w poniższym przykładzie kodu. Jeśli klient jest aplikacją kliencką WCF, działa jako wyjątek zarządzany, gdzie typ jest <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typem `GreetingFault` .

[!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
[!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

### <a name="sending-undeclared-faults"></a>Wysyłanie niezadeklarowanych błędów

Wysyłanie niezadeklarowanych błędów może być bardzo przydatne, aby szybko zdiagnozować i debugować problemy w aplikacjach WCF, ale jego użyteczność jako narzędzie debugowania jest ograniczone. Ogólnie rzecz biorąc, podczas debugowania zaleca się użycie <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwości. Po ustawieniu tej wartości na wartość true klienci widzą takie błędy jako <xref:System.ServiceModel.FaultException%601> wyjątki typu <xref:System.ServiceModel.ExceptionDetail> .

> [!IMPORTANT]
> Ponieważ zarządzane wyjątki mogą uwidaczniać wewnętrzne informacje o aplikacji, ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> `true` Zezwalanie klientom WCF na uzyskanie informacji o wyjątkach wewnętrznych operacji usługi, w tym identyfikowalnych danych osobowych lub innych poufnych informacji.
>
> W związku z tym ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` jest zalecane tylko jako sposób tymczasowego debugowania aplikacji usługi. Ponadto WSDL dla metody, która zwraca Nieobsłużone wyjątki zarządzane w ten sposób, nie zawiera kontraktu dla <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail> . Klienci muszą oczekiwać wystąpienia nieznanego błędu protokołu SOAP (zwracanego do klientów programu WCF jako <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektów) w celu poprawnego uzyskania informacji o debugowaniu.

Aby wysłać niezadeklarowany błąd protokołu SOAP, zgłoś <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiekt (to nie jest typ ogólny <xref:System.ServiceModel.FaultException%601> ) i przekaż ciąg do konstruktora. Jest to narażone na aplikacje klienckie programu WCF jako zgłoszone <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> wyjątki, w przypadku których ciąg jest dostępny przez wywołanie <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> metody.

> [!NOTE]
> Jeśli zadeklarujesz błąd protokołu SOAP typu String, a następnie wygenerujesz to w usłudze jako <xref:System.ServiceModel.FaultException%601> parametr typu, który jest <xref:System.String?displayProperty=nameWithType> wartością ciągu, jest przypisywana do <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> właściwości i nie jest dostępna w <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> .

## <a name="handling-faults"></a>Obsługa błędów

W przypadku klientów programu WCF błędy protokołu SOAP występujące podczas komunikacji, które są istotne dla aplikacji klienckich, są wywoływane jako wyjątki zarządzane. Chociaż istnieje wiele wyjątków, które mogą wystąpić podczas wykonywania dowolnego programu, aplikacje korzystające z modelu programowania klienta WCF mogą oczekiwać wyjątków następujących dwóch typów w wyniku komunikacji.

- <xref:System.TimeoutException>

- <xref:System.ServiceModel.CommunicationException>

<xref:System.TimeoutException>obiekty są generowane, gdy operacja przekroczy określony przedział czasu.

<xref:System.ServiceModel.CommunicationException>obiekty są generowane, gdy istnieje jakiś możliwy do odzyskania błąd komunikacji usługi lub klienta.

<xref:System.ServiceModel.CommunicationException>Klasa ma dwa ważne typy pochodne <xref:System.ServiceModel.FaultException> i <xref:System.ServiceModel.FaultException%601> typ ogólny.

<xref:System.ServiceModel.FaultException>wyjątki są generowane, gdy odbiornik otrzymuje błąd, który nie jest oczekiwany lub określony w kontrakcie operacji; zwykle zdarza się to, gdy aplikacja jest debugowana, a usługa ma <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> Właściwość ustawioną na `true` .

<xref:System.ServiceModel.FaultException%601>wyjątki są zgłaszane na kliencie w przypadku otrzymania błędu określonego w kontrakcie operacji w odpowiedzi na operację dwukierunkową (czyli metodę z <xref:System.ServiceModel.OperationContractAttribute> atrybutem z <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> ustawioną na `false` ).

> [!NOTE]
> Gdy usługa WCF ma <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ustawioną dla klienta właściwość lub `true` jako niezadeklarowany <xref:System.ServiceModel.FaultException%601> Typ <xref:System.ServiceModel.ExceptionDetail> . Klienci mogą przechwycić ten konkretny błąd lub obsłużyć błąd w bloku catch dla <xref:System.ServiceModel.FaultException> .

Zwykle tylko, <xref:System.ServiceModel.FaultException%601> <xref:System.TimeoutException> , i <xref:System.ServiceModel.CommunicationException> wyjątki są przydatne dla klientów i usług.

> [!NOTE]
> Inne wyjątki są oczywiście wykonywane. Nieoczekiwane wyjątki obejmują błędy katastrofalne, takie jak <xref:System.OutOfMemoryException?displayProperty=nameWithType> ; zazwyczaj aplikacje nie powinny przechwytywać takich metod.

### <a name="catch-fault-exceptions-in-the-correct-order"></a>Przechwyć wyjątki błędów w poprawnej kolejności

Ponieważ <xref:System.ServiceModel.FaultException%601> pochodzi od, <xref:System.ServiceModel.FaultException> i <xref:System.ServiceModel.FaultException> pochodzi z <xref:System.ServiceModel.CommunicationException> , ważne jest, aby przechwytywać te wyjątki w odpowiedniej kolejności. Jeśli na przykład masz blok try/catch, w którym pierwsze przechwycenie <xref:System.ServiceModel.CommunicationException> , wszystkie określone i nieokreślone błędy protokołu SOAP są obsługiwane. wszystkie kolejne bloki catch obsługujące <xref:System.ServiceModel.FaultException%601> wyjątek niestandardowy nigdy nie są wywoływane.

Należy pamiętać, że jedna operacja może zwracać dowolną liczbę błędów. Każdy błąd jest unikatowym typem i musi być obsłużony osobno.

### <a name="handle-exceptions-when-closing-the-channel"></a>Obsługuj wyjątki podczas zamykania kanału

W większości powyższych dyskusji należy wykonać błędy wysyłane w trakcie przetwarzania komunikatów aplikacji, czyli komunikaty jawnie wysyłane przez klienta, gdy aplikacja kliencka wywoła operacje na obiekcie klienta WCF.

Nawet z obiektami lokalnymi, które usuwają obiekt, może wywoływać lub maskować Wyjątki występujące podczas procesu odtwarzania. W przypadku korzystania z obiektów klienta WCF mogą wystąpić podobne wystąpienia. Gdy wywołujesz operacje, wysyłasz komunikaty przez ustanowione połączenie. Zamknięcie kanału może zgłosić wyjątki, jeśli połączenie nie może być czyste zamknięte lub zostało już zamknięte, nawet jeśli wszystkie operacje zostały zwrócone prawidłowo.

Zazwyczaj kanały obiektów klienta są zamknięte w jeden z następujących sposobów:

- Gdy obiekt klienta WCF zostanie odtworzony.

- Gdy aplikacja kliencka wywołuje <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> .

- Gdy aplikacja kliencka wywołuje <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> .

- Gdy aplikacja kliencka wywołuje operację, która jest operacją kończącą dla sesji.

We wszystkich przypadkach zamknięcie kanału powoduje, że kanał zaczyna zamykać wszystkie kanały bazowe, które mogą wysyłać komunikaty do obsługi złożonych funkcji na poziomie aplikacji. Na przykład gdy kontrakt wymaga sesji, powiązanie próbuje ustanowić sesję przez wymianę komunikatów z kanałem usługi do momentu ustanowienia sesji. Po zamknięciu kanału podstawowy kanał sesji powiadamia usługę o przerwaniu sesji. W takim przypadku, jeśli kanał został już przerwany, zamknięty lub nie można go użyć (na przykład w przypadku odłączenia kabla sieciowego), kanał klienta nie może poinformować kanału usługi o przerwaniu sesji i może spowodować wyjątek.

### <a name="abort-the-channel-if-necessary"></a>Przerywanie kanału w razie potrzeby

Ponieważ zamknięcie kanału może również generować wyjątki, zaleca się, aby oprócz przechwytywania wyjątków błędów w prawidłowej kolejności, należy przerwać kanał, który został użyty podczas wykonywania wywołania w bloku catch.

Jeśli błąd przekazuje informacje o błędzie specyficzne dla operacji i nadal jest możliwe, że mogą go używać inne osoby, nie ma potrzeby przerywania kanału (Chociaż te przypadki są rzadkie). We wszystkich innych przypadkach zaleca się przerwanie tego kanału. Aby uzyskać przykład pokazujący wszystkie te punkty, zobacz [oczekiwane wyjątki](./samples/expected-exceptions.md).

Poniższy przykład kodu pokazuje, jak obsłużyć wyjątki błędów SOAP w podstawowej aplikacji klienckiej, łącznie z zadeklarowanym błędem i niezadeklarowanym błędem.

> [!NOTE]
> Ten przykładowy kod nie używa `using` konstrukcji. Ponieważ zamykające kanały mogą generować wyjątki, zaleca się, aby najpierw utworzyć klienta programu WCF, a następnie otworzyć, użyć i zamknąć klienta WCF w tym samym bloku try. Aby uzyskać szczegółowe informacje, zobacz [Omówienie klienta programu WCF](wcf-client-overview.md) i [Używanie funkcji Close i Abort w celu zwolnienia zasobów klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).

[!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
[!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Oczekiwane wyjątki](./samples/expected-exceptions.md)
- [Zwalnianie zasobów klienta programu WCF za pomocą poleceń Zamknij i Przerwij](./samples/use-close-abort-release-wcf-client-resources.md)
