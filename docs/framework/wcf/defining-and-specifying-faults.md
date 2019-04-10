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
ms.openlocfilehash: 24c05bf41152fba2f54636cd0c15dde6fa71aa2b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299335"
---
# <a name="defining-and-specifying-faults"></a>Definiowanie i określanie błędów
Błędach SOAP obejmują warunku informacje o błędzie z usługi do klienta, a w przypadku dupleksowy, od klienta do usługi w sposób interoperacyjny. W tym temacie omówiono, kiedy i jak zdefiniować zawartości niestandardowych błędów i określić, jakie operacje można przywrócić je. Aby uzyskać więcej informacji na temat jak usługi lub dupleks klient może wysyłać te błędy i jak aplikacja klienta lub usługę obsługuje te błędy, zobacz [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md). Aby uzyskać omówienie obsługi błędów w aplikacji Windows Communication Foundation (WCF), zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Omówienie  
 Zadeklarowane w błędach SOAP są te, w których jest operacją <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> , który określa typ niestandardowy błędu protokołu SOAP. Niezadeklarowany błędach SOAP są te, które nie zostały określone w umowie dla danej operacji. W tym temacie pomaga zidentyfikować te warunki błędów i tworzenie usterek kontraktu usługi używanego przez klientów aby prawidłowo obsługiwać te warunki błędów zgłoszonych przez niestandardowych błędach SOAP. Podstawowe zadania są w kolejności:  
  
1. Zdefiniuj warunki błędów, które należy wiedzieć, klient usługi.  
  
2. Definiowanie zawartości niestandardowych błędach SOAP dla tych warunków błędu.  
  
3. Oznacz operacje tak, aby określonych błędach SOAP, które zgłaszają są widoczne dla klientów w języku WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definiowanie warunków błędów, których klientów należy wiedzieć o  
 Błędy protokołu SOAP są publicznie opisano komunikaty, które zawierają informacje o błędzie dla określonej operacji. Ponieważ zostały one opisane oraz inne komunikaty operacji w języku WSDL, klienci wiedzieć i dlatego należy oczekiwać obsłużyć takie błędy podczas wywoływania operacji. Ale ponieważ usług WCF są zapisywane w kodzie zarządzanym przy wyborze rozwiązania, które błąd warunków w kodzie zarządzanym są do przekonwertowania na błędy i zwracany do klienta zapewnia możliwość oddzielenia warunki błędów i usterki w usłudze sprawność po błędzie formalne Konwersacja należy za pomocą klienta.  
  
 Na przykład poniższy przykład kodu pokazuje operacji, która przyjmuje dwóch liczb całkowitych i zwraca inną liczbę całkowitą. Kilka wyjątki mogą zostać wygenerowane w tym miejscu, dzięki czemu podczas projektowania kontrakt błędu, należy określić warunki błędów, które są ważne dla klienta. W tym przypadku usługa powinna wykryć <xref:System.DivideByZeroException?displayProperty=nameWithType> wyjątku.  
  
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
    <OperationContract]> _  
    Public Function Divide(ByVal a As Integer, ByVal b As Integer) _  
       As Integer  
      If (b==0) Then   
            Throw New Exception("Division by zero!")  
      Return a/b  
    End Function  
End Class  
```  
  
 W powyższym przykładzie operacji można albo zwraca niestandardowy błąd protokołu SOAP, które są specyficzne dla dzielenie przez zero, niestandardowych błędów, który jest specyficzny dla operacji matematycznych, ale który zawiera informacje dotyczące dzielenia przez zero, wiele błędów dla kilku różnych sytuacje, lub nie błąd protokołu SOAP w ogóle.  
  
### <a name="define-the-content-of-error-conditions"></a>Definiowanie zawartości warunki błędów  
 Gdy wystąpi warunek błędu została zidentyfikowana jako taki, który skutecznie może zwrócić niestandardowy błąd protokołu SOAP, następnym krokiem jest do definiowania zawartości tego błędu i upewnij się, struktura zawartości może być serializowany. Przykład kodu w poprzedniej sekcji pokazuje błąd, specyficzne dla `Divide` operacji, ale jeśli istnieją inne operacje na `Calculator` usługi, a następnie pojedynczego niestandardowy błąd protokołu SOAP mogą informować klienta o wszystkie błędy Kalkulator `Divide`uwzględnione. W poniższym przykładzie kodu pokazano tworzenie obiektu niestandardowego błędu protokołu SOAP `MathFault`, który z nich mogą raportować błędy, które zostało nawiązane przy użyciu wszystkie operacje zapisu matematycznego, w tym `Divide`. Podczas tej klasy można określić operacji ( `Operation` właściwości) i wartość, która opisuje problem ( `ProblemType` właściwości), klasy i właściwości te muszą być możliwy do serializacji do przekazania do klienta w niestandardowy błąd protokołu SOAP. W związku z tym <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> i <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atrybuty są wykorzystywane do wytwarzania typu i jego właściwości, możliwy do serializacji i interoperacyjne, jak to możliwe.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Aby uzyskać więcej informacji na temat jak zapewnić danych jest możliwy do serializacji, zobacz [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Aby uzyskać listę serializacji obsługuje <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> udostępnia, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Oznacz operacji w celu ustalenia kontrakt błędu  
 Gdy struktury danych możliwych do serializacji, który jest zwracany jako część niestandardowego błąd protokołu SOAP jest zdefiniowany, ostatnim krokiem jest do oznaczania swoje kontrakt operacji jako zgłaszanie błędu protokołu SOAP tego typu. Aby to zrobić, należy użyć <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atrybutu i przekazać typ niestandardowego typu danych, które zostały zbudowane. Poniższy przykład kodu pokazuje sposób użycia <xref:System.ServiceModel.FaultContractAttribute> atrybutu, aby określić, że `Divide` operacji może zwrócić błąd protokołu SOAP, typu `MathFault`. Inne operacje matematyczne na podstawie można teraz również określić czy może zwrócić `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Operacji można określić, że zwraca więcej niż jeden błąd niestandardowy, oznaczając tej operacji z więcej niż jednym <xref:System.ServiceModel.FaultContractAttribute> atrybutu.  
  
 Następnym krokiem, aby zaimplementować kontrakt błędu w danej implementacji operacji jest opisana w temacie [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>Protokołu SOAP, WSDL i zagadnienia dotyczące współdziałania  
 W pewnych okolicznościach szczególnie podczas współpracy z platformami, może być ważne, aby kontrolować sposób wyświetlania błędów w komunikacie protokołu SOAP lub sposób jest opisany w metadanych WSDL.  
  
 <xref:System.ServiceModel.FaultContractAttribute> Atrybut ma <xref:System.ServiceModel.FaultContractAttribute.Name%2A> właściwość, która zapewnia kontrolę nad nazwy elementu błędów WSDL, który jest generowany w metadanych dla tego błędu.  
  
 Zgodnie ze standardem protokołu SOAP usterka może mieć `Action`, `Code`, a `Reason`. `Action` Jest kontrolowana przez <xref:System.ServiceModel.FaultContractAttribute.Action%2A> właściwości. <xref:System.ServiceModel.FaultException.Code%2A> Właściwości i <xref:System.ServiceModel.FaultException.Reason%2A> właściwości są obie właściwości <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> klasy, która jest klasą nadrzędną ogólnego <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. `Code` Zawiera właściwość <xref:System.ServiceModel.FaultCode.SubCode%2A> elementu członkowskiego.  
  
 Podczas uzyskiwania dostępu do innych usług, które generowanie błędów, istnieją pewne ograniczenia. WCF obsługuje tylko błędy z typami szczegółowo opisujący schematu i które są zgodne z kontraktów danych. Na przykład jak wspomniano powyżej, usługi WCF nie obsługuje błędy, które Użyj atrybutów XML w ich typach szczegółów lub błędów przy użyciu więcej niż jeden element najwyższego poziomu w sekcji szczegółów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md)
- [Instrukcje: Deklarowanie błędów w kontraktach usługi](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)
- [Omówienie poziomów ochrony](../../../docs/framework/wcf/understanding-protection-level.md)
- [Instrukcje: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
