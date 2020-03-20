---
title: 'Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 793f7214f8319e87c3e344990577841fc029bc55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185029"
---
# <a name="how-to-create-a-request-reply-contract"></a>Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”
Umowa żądanie odpowiedź określa metodę, która zwraca odpowiedź. Odpowiedź musi być wysłana i skorelowana z wnioskiem zgodnie z warunkami niniejszej umowy. Nawet jeśli metoda zwraca`void` odpowiedź (w języku `Sub` C# lub w języku Visual Basic), infrastruktura tworzy i wysyła pustą wiadomość do wywołującego. Aby zapobiec wysyłaniu pustej wiadomości odpowiedzi, użyj kontraktu jednokierunkowego dla operacji.  
  
### <a name="to-create-a-request-reply-contract"></a>Aby utworzyć umowę żądanie-odpowiedź  
  
1. Utwórz interfejs w wybranym języku programowania.  
  
2. Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybut do interfejsu.  
  
3. Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybut do każdej metody, która klienci mogą wywoływać.  
  
4. Element opcjonalny. Ustaw wartość właściwości, <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` aby zapobiec wysyłaniu pustej wiadomości odpowiedzi. Domyślnie wszystkie operacje są kontrakty żądanie odpowiedzi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje kontrakt dla usługi kalkulatora, który zapewnia `Add` i `Subtract` metody. Metoda `Multiply` nie jest częścią umowy, ponieważ nie <xref:System.ServiceModel.OperationContractAttribute> jest oznaczony przez klasę, a więc nie jest dostępny dla klientów.  
  
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
  
- Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.OperationContractAttribute> określania <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> umów operacji, zobacz klasę i właściwość.  
  
- Zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty powoduje automatyczne generowanie definicji umowy serwisowej w dokumencie języka opisu usług sieci Web (WSDL) po wdrożeniu usługi. Dokument jest pobierany przez `?wsdl` dołączenie do adresu podstawowego HTTP dla usługi. Na przykład: `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.OperationContractAttribute>
- [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
