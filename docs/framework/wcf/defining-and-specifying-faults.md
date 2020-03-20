---
title: Definiowanie i określanie błędów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
ms.openlocfilehash: 10fc045cab995cca8d78e470d74ec9341e167308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176698"
---
# <a name="defining-and-specifying-faults"></a>Definiowanie i określanie błędów
Błędy protokołu SOAP przekazują informacje o stanie błędu z usługi do klienta, a w przypadku dupleksu z klienta do usługi w sposób interoperacyjny. W tym temacie omówiono, kiedy i jak zdefiniować niestandardową zawartość błędów i określić, które operacje mogą je zwracać. Aby uzyskać więcej informacji o tym, jak usługa lub klient dupleksu może wysyłać te błędy i jak aplikacja klienta lub usługi obsługuje te usterki, zobacz [Wysyłanie i odbieranie błędów](sending-and-receiving-faults.md). Aby zapoznać się z omówieniem obsługi błędów w aplikacjach Windows Communication Foundation (WCF), zobacz [Określanie i obsługa błędów w umowach i usługach](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Omówienie  
 Zadeklarowane błędy protokołu SOAP to te, w których operacja ma, <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> który określa niestandardowy typ błędu PROTOKOŁU SOAP. Niezadeklarowane błędy protokołu SOAP to te, które nie są określone w umowie dla operacji. W tym temacie pomaga zidentyfikować te warunki błędu i utworzyć kontrakt błędów dla usługi, które klienci mogą używać do prawidłowego obsługi tych warunków błędu, gdy są powiadamiane przez niestandardowe błędy PROTOKOŁU SOAP. Podstawowe zadania są, w kolejności:  
  
1. Zdefiniuj warunki błędu, o których powinien wiedzieć klient usługi.  
  
2. Zdefiniuj niestandardową zawartość błędów PROTOKOŁU SOAP dla tych warunków błędu.  
  
3. Oznacz swoje operacje, tak aby określone błędy protokołu SOAP, które zgłaszają, były udostępniane klientom w programie WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definiowanie warunków błędu, o których klienci powinni wiedzieć  
 Błędy protokołu SOAP są publicznie opisane komunikaty, które zawierają informacje o błędach dla określonej operacji. Ponieważ są one opisane wraz z innymi komunikatami operacyjnymi w WSDL, klienci wiedzą i w związku z tym oczekują obsługi takich błędów podczas wywoływania operacji. Ale ponieważ usługi WCF są zapisywane w kodzie zarządzanym, decydując, które warunki błędu w kodzie zarządzanym mają być konwertowane na błędy i zwracane klientowi, daje możliwość oddzielenia warunków błędów i błędów w usłudze od błędu formalnego rozmowy z klientem.  
  
 Na przykład w poniższym przykładzie kodu pokazano operację, która przyjmuje dwie liczby całkowite i zwraca inną liczbę całkowitą. Kilka wyjątków można w tym miejscu, więc podczas projektowania umowy błędów, należy określić, które warunki błędu są ważne dla klienta. W takim przypadku usługa powinna <xref:System.DivideByZeroException?displayProperty=nameWithType> wykryć wyjątek.  
  
```csharp  
[ServiceContract]  
public class CalculatorService  
{  
    [OperationContract]
    int Divide(int a, int b)  
    {  
      if (b==0) throw new Exception("Division by zero!");  
      return a/b;  
    }  
}  
```  
  
```vb
<ServiceContract> _
Public Class CalculatorService
    <OperationContract> _
    Public Function Divide(a As Integer, b As Integer) As Integer
        If b = 0 Then Throw New DivideByZeroException("Division by zero!")
        Return a / b
    End Function
End Class
```
  
 W poprzednim przykładzie operacja może albo zwrócić niestandardowy błąd PROTOKOŁU SOAP, który jest specyficzny dla dzielenia przez zero, błąd niestandardowy, który jest specyficzny dla operacji matematycznych, ale który zawiera informacje specyficzne dla podziału przez zero, wiele błędów dla kilku różnych lub brak błędu SOAP.  
  
### <a name="define-the-content-of-error-conditions"></a>Definiowanie zawartości warunków błędu  
 Po zidentyfikowaniu warunku błędu jako warunek, który może z pożytkiem zwrócić niestandardowy błąd PROTOKOŁU SOAP, następnym krokiem jest zdefiniowanie zawartości tego błędu i zapewnienie, że struktura zawartości może być serializowana. Przykład kodu w poprzedniej sekcji pokazuje błąd `Divide` specyficzny dla operacji, ale jeśli `Calculator` istnieją inne operacje w usłudze, a następnie pojedynczy `Divide` niestandardowy błąd PROTOKOŁU SOAP może poinformować klienta o wszystkich warunkach błędu kalkulatora, w tym. Poniższy przykład kodu pokazuje utworzenie niestandardowego `MathFault`błędu PROTOKOŁU SOAP, który może zgłaszać błędy popełniane przy użyciu wszystkich operacji matematycznych, w tym `Divide`. Podczas gdy klasa może określić operację `Operation` (właściwość) i `ProblemType` wartość, która opisuje problem (właściwość), klasa i te właściwości muszą być serializable być przeniesione do klienta w niestandardowym błędem PROTOKOŁU SOAP. W związku <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> z <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> tym i atrybuty są używane do typu i jego właściwości serializable i jak interoperacyjne, jak to możliwe.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Aby uzyskać więcej informacji na temat sposobu zapewnienia serializacji danych, zobacz [Określanie transferu danych w umowach serwisowych](./feature-details/specifying-data-transfer-in-service-contracts.md). Aby uzyskać listę obsługi serializacji, która <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> zapewnia, zobacz [typy obsługiwane przez serializatora kontraktów danych](./feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Oznacz operacje w celu ustalenia kontraktu z usterką  
 Po serializable struktury danych, który jest zwracany jako część niestandardowego błędu PROTOKOŁU SOAP jest zdefiniowany, ostatnim krokiem jest oznaczenie umowy operacji jako rzucanie błędu PROTOKOŁU SOAP tego typu. Aby to zrobić, <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> należy użyć atrybutu i przekazać typ niestandardowego typu danych, który został skonstruowany. W poniższym przykładzie kodu <xref:System.ServiceModel.FaultContractAttribute> pokazano, jak `Divide` użyć atrybutu, aby `MathFault`określić, że operacja może zwrócić błąd typu SOAP . Inne operacje oparte na matematyce można `MathFault`teraz również określić, że mogą zwracać .  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Operacja może określić, że zwraca więcej niż jeden błąd <xref:System.ServiceModel.FaultContractAttribute> niestandardowy, oznaczając tę operację więcej niż jednym atrybutem.  
  
 Następny krok, aby zaimplementować kontrakt z usterką w implementacji operacji, jest opisany w temacie [Wysyłanie i odbieranie usterek](sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>Zagadnienia dotyczące mydła, WSDL i interoperacyjności  
 W niektórych okolicznościach, zwłaszcza podczas współpracy z innymi platformami, może być ważne, aby kontrolować sposób, w jaki błąd pojawia się w wiadomości SOAP lub sposób, w jaki jest opisany w metadanych WSDL.  
  
 Atrybut <xref:System.ServiceModel.FaultContractAttribute> ma <xref:System.ServiceModel.FaultContractAttribute.Name%2A> właściwość, która umożliwia kontrolę nad nazwą elementu błędu WSDL, który jest generowany w metadanych dla tego błędu.  
  
 Zgodnie ze standardem SOAP, usterka `Code`może `Reason`mieć `Action`, , i . Obiekt `Action` jest kontrolowany <xref:System.ServiceModel.FaultContractAttribute.Action%2A> przez obiekt. Właściwość <xref:System.ServiceModel.FaultException.Code%2A> <xref:System.ServiceModel.FaultException.Reason%2A> i właściwość są <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> właściwości klasy, która jest klasą nadrzędną generic <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. W `Code` obiekcie <xref:System.ServiceModel.FaultCode.SubCode%2A> znajduje się członek.  
  
 Podczas uzyskiwania dostępu do usług innych niż usługi, które generują błędy, istnieją pewne ograniczenia. WCF obsługuje tylko błędy z typów szczegółów, które opisuje schemat i które są zgodne z kontraktów danych. Na przykład, jak wspomniano powyżej, WCF nie obsługuje błędów, które używają atrybutów XML w ich typach szczegółów lub błędów z więcej niż jednym elementem najwyższego poziomu w sekcji szczegółów.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md)
- [Wysyłanie i odbieranie błędów](sending-and-receiving-faults.md)
- [Deklarowanie błędów w kontraktach usługi](how-to-declare-faults-in-service-contracts.md)
- [Omówienie poziomów ochrony](understanding-protection-level.md)
- [Instrukcje: ustawianie właściwości ProtectionLevel](how-to-set-the-protectionlevel-property.md)
- [Określanie transferu danych w kontraktach usług](./feature-details/specifying-data-transfer-in-service-contracts.md)
