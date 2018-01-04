---
title: "Definiowanie i określanie błędów"
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
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713b9594ac628c2c256e8592d3894feee8029332
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="defining-and-specifying-faults"></a>Definiowanie i określanie błędów
Błąd warunku informacji z usługi do klienta, a w przypadku dupleksowy, od klienta do usługi w sposób interoperacyjne przedstawienia błędach SOAP W tym temacie omówiono, kiedy i jak definiowanie zawartości błędów niestandardowych i określ, jakie operacje może zwracać je. [!INCLUDE[crabout](../../../includes/crabout-md.md)]usługi lub dupleks klient może wysyłać te błędy i sposób obsługi tych błędów w aplikacji klienta lub usługi, zobacz [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md). Omówienie obsługi błędów w [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Omówienie  
 Zadeklarowany w błędach SOAP są te, w których ma operacji <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> , który określa typ niestandardowy błędu protokołu SOAP. Niezadeklarowany błędach SOAP są tymi, które nie są określone w umowie dla operacji. Ten temat pomaga zidentyfikować te warunki błędów i tworzenie usterki kontraktu usługi używanego przez klientów do poprawnie obsługiwać te warunki błędów przy powiadomieniu przez niestandardowe błędach SOAP. Podstawowe zadania znajdują się w kolejności:  
  
1.  Zdefiniuj warunki błędów, które informacje o kliencie usługi.  
  
2.  Definiowanie niestandardowego zawartości o błędach SOAP dla tych warunków błędu.  
  
3.  Oznacz operacje, aby określonych błędach SOAP, które generują one są widoczne dla klientów w języku WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Zdefiniowanie warunków błędów, które klientów należy wiedzieć o  
 Błędach SOAP są publicznie opisane wiadomości, zawierających informacje o błędzie dla określonej operacji. Ponieważ są one opisane oraz inne komunikaty operacji w języku WSDL, klienci wiedzieć i w związku z tym spodziewać się do obsługi tych błędów podczas wywoływania operacji. Jednak ponieważ [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług są zapisywane w kodzie zarządzanym podejmowania decyzji o który błąd warunki w kodzie zarządzanym są do przekonwertowania na błędy i zwracany do klienta zapewnia możliwość oddzielenia warunki błędów i usterki w usłudze z posiadanie błąd konwersacji, z klienta.  
  
 Na przykład następujący przykładowy kod przedstawia operację, która ma dwie liczb całkowitych i zwraca inną liczbę całkowitą. Kilka wyjątków może zostać wygenerowany tutaj, aby podczas projektowania kontrakt błędu, należy określić warunki błędów, które są ważne w przypadku klienta. W takim przypadku usługa powinna wykryć <xref:System.DivideByZeroException?displayProperty=nameWithType> wyjątku.  
  
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
  
 W powyższym przykładzie operacji można zwrócenie niestandardowego błędu protokołu SOAP, specyficzne dla dzielenia przez zero, błąd niestandardowy, który jest specyficzne dla operacji matematycznych, ale zawiera informacje specyficzne dla dzielenia przez zero, wiele błędów dla wielu różnych Błąd sytuacje, lub nie błędu protokołu SOAP, co.  
  
### <a name="define-the-content-of-error-conditions"></a>Zdefiniuj zawartość warunki błędów  
 Po warunek błędu został zidentyfikowany jako jeden korzyścią mogą zwracać niestandardowego błędu protokołu SOAP, następnym krokiem jest zdefiniowanie zawartość tego błędu i upewnij się, że struktura zawartości może być Zserializowany. Przykładowy kod w poprzedniej sekcji pokazuje błąd, specyficzne dla `Divide` operacji, ale jeśli istnieją inne operacje na `Calculator` usługi, a następnie pojedynczego niestandardowego błędu protokołu SOAP może poinformować klienta wszystkie błędy Kalkulator `Divide`uwzględnione. W poniższym przykładzie kodu pokazano tworzenie obiektu niestandardowego błędu protokołu SOAP, `MathFault`, które mogą raportować błędy, utworzone za pomocą wszystkich operacji matematycznych, w tym `Divide`. Podczas tej klasy można określić operacji ( `Operation` właściwości) i wartości, który opisuje problem ( `ProblemType` właściwości), klasy i te właściwości musi być możliwy do serializacji do przekazania do klienta w niestandardowych błędu protokołu SOAP. W związku z tym <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> i <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atrybuty służą do typu i jego właściwości do serializacji i interoperacyjne jak to możliwe.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]jak zapewnić danych jest możliwy do serializacji, zobacz [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Aby uzyskać listę serializacji obsługuje <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> udostępnia, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Oznacz operacje w celu ustanowienia kontrakt błędu  
 Gdy struktura danych serializacji, zwracana ustalony część niestandardowego błędu protokołu SOAP, ostatnim krokiem jest oznaczenie dany kontrakt operacji jako zgłaszanie błędu protokołu SOAP tego typu. Aby to zrobić, użyj <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atrybutu i przekazać typ typu danych niestandardowych, które zostały utworzone. Poniższy przykładowy kod przedstawia sposób użycia <xref:System.ServiceModel.FaultContractAttribute> atrybutu, aby określić, że `Divide` operacji może zwrócić błędu protokołu SOAP, którego typ `MathFault`. Inne operacje na podstawie matematyczne można teraz dodawać funkcje te mogą zwracać `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Operację można określić zwraca więcej niż jeden błąd niestandardowy, oznaczając tej operacji z więcej niż jednym <xref:System.ServiceModel.FaultContractAttribute> atrybutu.  
  
 Następnym krokiem, aby zaimplementować kontrakt błędu w implementacji operacji jest opisana w temacie [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>SOAP, WSDL i zagadnienia dotyczące współdziałania  
 W pewnych okolicznościach szczególnie podczas współpracy z innych platform, może być ważne kontrolować sposób wyświetlania błąd w wiadomości SOAP lub sposób jest opisany w metadanych WSDL.  
  
 <xref:System.ServiceModel.FaultContractAttribute> Ma atrybut <xref:System.ServiceModel.FaultContractAttribute.Name%2A> właściwość, która zapewnia kontrolę nad nazwę elementu błędów WSDL, która jest generowana w metadanych dla tego błędu.  
  
 Zgodnie ze standardowego protokołu SOAP usterka może mieć `Action`, `Code`, a `Reason`. `Action` Jest kontrolowany przez <xref:System.ServiceModel.FaultContractAttribute.Action%2A> właściwości. <xref:System.ServiceModel.FaultException.Code%2A> Właściwości i <xref:System.ServiceModel.FaultException.Reason%2A> właściwości są obie właściwości <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> klasy, która jest klasą nadrzędną ogólnego <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. `Code` Zawiera właściwość <xref:System.ServiceModel.FaultCode.SubCode%2A> elementu członkowskiego.  
  
 Podczas uzyskiwania dostępu do innych niż usług, które generowanie błędów, istnieją pewne ograniczenia. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]obsługuje tylko błędy z typami szczegółowo opisujący schematu i które są zgodne z kontraktów danych. Na przykład, jak wspomniano powyżej [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] nie obsługuje usterki, które Użyj atrybutów XML w ich typach szczegółów lub błędów z więcej niż jeden element najwyższego poziomu w sekcji szczegółów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md)  
 [Deklarowanie błędów w kontraktach usługi](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)  
 [Omówienie poziomów ochrony](../../../docs/framework/wcf/understanding-protection-level.md)  
 [Instrukcje: ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
