---
title: 'Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 8a09c265c77edc584b591477e64314f1e76e332b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593441"
---
# <a name="how-to-create-a-request-reply-contract"></a>Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”
Kontrakt typu żądanie-odpowiedź określa metodę, która zwraca odpowiedź. Odpowiedź musi być wysłana i skorelowane do żądania zgodnie z warunkami tego kontraktu. Nawet jeśli metoda nie zwróci odpowiedzi ( `void` w języku C# lub `Sub` w Visual Basic), infrastruktura tworzy i wysyła pusty komunikat do obiektu wywołującego. Aby zapobiec wysyłaniu pustego komunikatu odpowiedzi, użyj kontraktu jednokierunkowego dla operacji.  
  
### <a name="to-create-a-request-reply-contract"></a>Aby utworzyć kontrakt typu żądanie-odpowiedź  
  
1. Utwórz interfejs w wybranym języku programowania.  
  
2. Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybut do interfejsu.  
  
3. Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybut do poszczególnych metod, które mogą być wywoływane przez klientów.  
  
4. Opcjonalny. Ustaw wartość <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości na `true` , aby zapobiec wysyłaniu pustego komunikatu odpowiedzi. Domyślnie wszystkie operacje są kontraktami żądanie-odpowiedź.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje kontrakt usługi kalkulatora, która dostarcza `Add` `Subtract` metody i. `Multiply`Metoda nie jest częścią kontraktu, ponieważ nie jest oznaczona przez <xref:System.ServiceModel.OperationContractAttribute> klasę i dlatego nie jest dostępna dla klientów.  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- Aby uzyskać więcej informacji na temat określania kontraktów operacji, zobacz <xref:System.ServiceModel.OperationContractAttribute> Klasa i <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> Właściwość.  
  
- Zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutów i <xref:System.ServiceModel.OperationContractAttribute> powoduje automatyczne generowanie definicji kontraktu usługi w dokumencie Web Services Description Language (WSDL) po wdrożeniu usługi. Dokument zostanie pobrany przez dołączenie `?wsdl` do podstawowego adresu http dla usługi. Na przykład: `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.OperationContractAttribute>
- [Projektowanie kontraktów usług](../designing-service-contracts.md)
- [Instrukcje: tworzenie kontraktu dwukierunkowego](how-to-create-a-duplex-contract.md)
