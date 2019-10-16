---
title: Wysyłanie i odbieranie błędów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: dc9dcb5d8e36984d1e5a2e5c5124e74509de7f3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320228"
---
# <a name="sending-and-receiving-faults"></a>Wysyłanie i odbieranie błędów

Błędy protokołu SOAP umożliwiają przekazywanie informacji o stanie błędu z usługi do klienta i w przypadku dupleksu od klienta do usługi w sposób interoperacyjny. Zazwyczaj usługa definiuje niestandardową zawartość błędów i określa, które operacje mogą je zwrócić. (Aby uzyskać więcej informacji, zobacz [Definiowanie i określanie błędów](defining-and-specifying-faults.md)). W tym temacie omówiono, jak usługa lub klient dupleksowy może wysyłać te błędy, gdy wystąpił odpowiedni warunek błędu i sposób obsługi tych błędów przez klienta lub aplikację usługi. Omówienie obsługi błędów w aplikacjach Windows Communication Foundation (WCF) zawiera temat [określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="sending-soap-faults"></a>Wysyłanie błędów SOAP

Zadeklarowane błędy protokołu SOAP to te, w których operacja ma <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>, która określa niestandardowy typ błędu SOAP. Niezadeklarowane błędy SOAP to te, które nie są określone w kontrakcie dla operacji.

### <a name="sending-declared-faults"></a>Wysyłanie zadeklarowanych błędów

Aby wysłać zadeklarowany błąd protokołu SOAP, należy wykryć warunek błędu, dla którego jest odpowiedni błąd protokołu SOAP i zgłosić nowy <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>, gdzie parametr typu jest nowym obiektem typu określonego w <xref:System.ServiceModel.FaultContractAttribute> dla tej operacji. Poniższy przykład kodu pokazuje użycie <xref:System.ServiceModel.FaultContractAttribute>, aby określić, że operacja `SampleMethod` może zwrócić błąd protokołu SOAP z typem szczegółowym `GreetingFault`.

[!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
[!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

Aby przekazać klientowi informacje o błędzie `GreetingFault`, należy przechwycić odpowiedni warunek błędu i zgłosić nową <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault` z nowym obiektem `GreetingFault` jako argument, jak w poniższym przykładzie kodu. Jeśli klient jest aplikacją kliencką WCF, działa jako wyjątek zarządzany, gdzie typ jest <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault`.

[!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
[!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

### <a name="sending-undeclared-faults"></a>Wysyłanie niezadeklarowanych błędów

Wysyłanie niezadeklarowanych błędów może być bardzo przydatne, aby szybko zdiagnozować i debugować problemy w aplikacjach WCF, ale jego użyteczność jako narzędzie debugowania jest ograniczone. Ogólnie rzecz biorąc, podczas debugowania zaleca się użycie właściwości <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType>. Gdy ta wartość zostanie ustawiona na wartość true, klienci napotykają takie błędy jako wyjątki <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>.

> [!IMPORTANT]
> Ponieważ zarządzane wyjątki mogą uwidaczniać wewnętrzne informacje o aplikacji, ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> na `true` może pozwolić klientom WCF uzyskać informacje o wyjątkach operacji usługi wewnętrznej, w tym identyfikowalnych przez użytkownika lub innych poufnych zawartych.
>
> W związku z tym ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> do `true` jest zalecane tylko jako sposób tymczasowego debugowania aplikacji usługi. Ponadto WSDL dla metody, która zwraca Nieobsłużone wyjątki zarządzane w ten sposób, nie zawiera kontraktu dla <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienci muszą oczekiwać wystąpienia nieznanego błędu protokołu SOAP (zwracanego do klientów WCF jako obiektów <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>) w celu poprawnego uzyskania informacji o debugowaniu.

Aby wysłać niezadeklarowany błąd protokołu SOAP, zgłoś obiekt <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> (czyli nie typ ogólny <xref:System.ServiceModel.FaultException%601>) i przekaż ciąg do konstruktora. Jest on narażony na aplikacje klienckie programu WCF jako zgłoszony wyjątek <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>, gdzie jest dostępny ciąg, wywołując metodę <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.

> [!NOTE]
> Jeśli zadeklarujesz błąd protokołu SOAP typu String, a następnie throw to w usłudze jako <xref:System.ServiceModel.FaultException%601>, gdzie parametr typu jest <xref:System.String?displayProperty=nameWithType> wartość ciągu jest przypisana do właściwości <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> i nie jest dostępna w <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.

## <a name="handling-faults"></a>Obsługa błędów

W przypadku klientów programu WCF błędy protokołu SOAP występujące podczas komunikacji, które są istotne dla aplikacji klienckich, są wywoływane jako wyjątki zarządzane. Chociaż istnieje wiele wyjątków, które mogą wystąpić podczas wykonywania dowolnego programu, aplikacje korzystające z modelu programowania klienta WCF mogą oczekiwać wyjątków następujących dwóch typów w wyniku komunikacji.

- <xref:System.TimeoutException>

- <xref:System.ServiceModel.CommunicationException>

obiekty <xref:System.TimeoutException> są generowane, gdy operacja przekroczy określony przedział czasu.

obiekty <xref:System.ServiceModel.CommunicationException> są generowane, gdy istnieje jakiś możliwy do odzyskania błąd komunikacji usługi lub klienta.

Klasa <xref:System.ServiceModel.CommunicationException> ma dwa ważne typy pochodne, <xref:System.ServiceModel.FaultException> i rodzajowy <xref:System.ServiceModel.FaultException%601>.

wyjątki <xref:System.ServiceModel.FaultException> są generowane, gdy odbiornik otrzymuje błąd, który nie jest oczekiwany lub określony w kontrakcie operacji; zwykle zdarza się to, gdy aplikacja jest debugowana, a usługa ma właściwość <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ustawioną na `true`.

wyjątki <xref:System.ServiceModel.FaultException%601> są zgłaszane na kliencie, gdy błąd określony w umowie operacji jest odbierany w odpowiedzi na operację dwukierunkową (czyli metodę z atrybutem <xref:System.ServiceModel.OperationContractAttribute> z <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> ustawionym na `false`).

> [!NOTE]
> Jeśli dla usługi WCF Właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ma ustawioną wartość `true`, klient ten napotyka jako niezadeklarowany <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienci mogą przechwycić ten konkretny błąd lub obsłużyć błąd w bloku catch dla <xref:System.ServiceModel.FaultException>.

Zwykle tylko <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException> i <xref:System.ServiceModel.CommunicationException> są istotne dla klientów i usług.

> [!NOTE]
> Inne wyjątki są oczywiście wykonywane. Nieoczekiwane wyjątki obejmują błędy katastrofalne, takie jak <xref:System.OutOfMemoryException?displayProperty=nameWithType>; Zazwyczaj aplikacje nie powinny przechwytywać takich metod.

### <a name="catch-fault-exceptions-in-the-correct-order"></a>Przechwyć wyjątki błędów w poprawnej kolejności

Ponieważ <xref:System.ServiceModel.FaultException%601> pochodzi z <xref:System.ServiceModel.FaultException>, a <xref:System.ServiceModel.FaultException> pochodzi od <xref:System.ServiceModel.CommunicationException>, ważne jest, aby przechwytywać te wyjątki w odpowiedniej kolejności. Jeśli na przykład masz blok try/catch, w którym najpierw jest przechwytywany <xref:System.ServiceModel.CommunicationException>, wszystkie określone i nieokreślone błędy protokołu SOAP są obsługiwane. wszystkie kolejne bloki catch obsługujące niestandardowy wyjątek <xref:System.ServiceModel.FaultException%601> nigdy nie są wywoływane.

Należy pamiętać, że jedna operacja może zwracać dowolną liczbę błędów. Każdy błąd jest unikatowym typem i musi być obsłużony osobno.

### <a name="handle-exceptions-when-closing-the-channel"></a>Obsługuj wyjątki podczas zamykania kanału

W większości powyższych dyskusji należy wykonać błędy wysyłane w trakcie przetwarzania komunikatów aplikacji, czyli komunikaty jawnie wysyłane przez klienta, gdy aplikacja kliencka wywoła operacje na obiekcie klienta WCF.

Nawet z obiektami lokalnymi, które usuwają obiekt, może wywoływać lub maskować Wyjątki występujące podczas procesu odtwarzania. W przypadku korzystania z obiektów klienta WCF mogą wystąpić podobne wystąpienia. Gdy wywołujesz operacje, wysyłasz komunikaty przez ustanowione połączenie. Zamknięcie kanału może zgłosić wyjątki, jeśli połączenie nie może być czyste zamknięte lub zostało już zamknięte, nawet jeśli wszystkie operacje zostały zwrócone prawidłowo.

Zazwyczaj kanały obiektów klienta są zamknięte w jeden z następujących sposobów:

- Gdy obiekt klienta WCF zostanie odtworzony.

- Gdy aplikacja kliencka wywoła <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.

- Gdy aplikacja kliencka wywoła <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.

- Gdy aplikacja kliencka wywołuje operację, która jest operacją kończącą dla sesji.

We wszystkich przypadkach zamknięcie kanału powoduje, że kanał zaczyna zamykać wszystkie kanały bazowe, które mogą wysyłać komunikaty do obsługi złożonych funkcji na poziomie aplikacji. Na przykład gdy kontrakt wymaga sesji, powiązanie próbuje ustanowić sesję przez wymianę komunikatów z kanałem usługi do momentu ustanowienia sesji. Po zamknięciu kanału podstawowy kanał sesji powiadamia usługę o przerwaniu sesji. W takim przypadku, jeśli kanał został już przerwany, zamknięty lub nie można go użyć (na przykład w przypadku odłączenia kabla sieciowego), kanał klienta nie może poinformować kanału usługi o przerwaniu sesji i może spowodować wyjątek.

### <a name="abort-the-channel-if-necessary"></a>Przerywanie kanału w razie potrzeby

Ponieważ zamknięcie kanału może również generować wyjątki, zaleca się, aby oprócz przechwytywania wyjątków błędów w prawidłowej kolejności, należy przerwać kanał, który został użyty podczas wykonywania wywołania w bloku catch.

Jeśli błąd przekazuje informacje o błędzie specyficzne dla operacji i nadal jest możliwe, że mogą go używać inne osoby, nie ma potrzeby przerywania kanału (Chociaż te przypadki są rzadkie). We wszystkich innych przypadkach zaleca się przerwanie tego kanału. Aby uzyskać przykład pokazujący wszystkie te punkty, zobacz [oczekiwane wyjątki](./samples/expected-exceptions.md).

Poniższy przykład kodu pokazuje, jak obsłużyć wyjątki błędów SOAP w podstawowej aplikacji klienckiej, łącznie z zadeklarowanym błędem i niezadeklarowanym błędem.

> [!NOTE]
> Ten przykładowy kod nie używa konstrukcji `using`. Ponieważ zamykające kanały mogą generować wyjątki, zaleca się, aby najpierw utworzyć klienta programu WCF, a następnie otworzyć, użyć i zamknąć klienta WCF w tym samym bloku try. Aby uzyskać szczegółowe informacje, zobacz [Omówienie klienta programu WCF](wcf-client-overview.md) i [Używanie funkcji Close i Abort w celu zwolnienia zasobów klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).

[!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
[!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Oczekiwane wyjątki](./samples/expected-exceptions.md)
- [Użyj Zamknij i Przerwij, aby zwolnić zasoby klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md)
