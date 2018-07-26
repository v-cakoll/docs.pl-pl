---
title: 'Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 0d41973d04fc75f70011505a3361e71e89a05276
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220987"
---
# <a name="how-to-create-a-request-reply-contract"></a>Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”
Kontraktu "żądanie-odpowiedź" Określa metodę, która zwraca odpowiedź. Odpowiedź musi być wysyłane i skorelowane żądanie zgodnie z warunkami niniejszej Umowy. Nawet jeśli metoda nie zwraca żadnej odpowiedzi (`void` w języku C# lub `Sub` w języku Visual Basic), infrastruktury, tworzy i wysyła pustego komunikatu do obiektu wywołującego. Aby uniemożliwić wysyłanie odpowiedzi pusty komunikat, należy użyć kontraktu jednokierunkowego dla tej operacji.  
  
### <a name="to-create-a-request-reply-contract"></a>Tworzenie kontraktu "żądanie-odpowiedź"  
  
1.  Tworzenie interfejsu w wybranym języku programowania.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do interfejsu.  
  
3.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybut do każdej metody, które mogą być wywoływane przez klientów.  
  
4.  Opcjonalna. Ustaw wartość <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwość `true` aby uniemożliwić wysyłanie odpowiedzi pusty komunikat. Domyślnie wszystkie operacje są kontraktów "żądanie odpowiedź".  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje kontrakt usługi Kalkulator, która zapewnia `Add` i `Subtract` metody. `Multiply` Metoda nie jest częścią kontraktu, ponieważ nie jest oznaczony za <xref:System.ServiceModel.OperationContractAttribute> klasy, a zatem nie jest dostępna dla klientów.  
  
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
  
-   Aby uzyskać więcej informacji na temat sposobu określania kontrakty operacji, zobacz <xref:System.ServiceModel.OperationContractAttribute> klasy i <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości.  
  
-   Stosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty powoduje automatyczne generowanie definicje kontraktu usługi w dokumencie usługi sieci Web Services Description Language (WSDL), po wdrożeniu usługi. Dokument zostanie pobrana przez dołączenie `?wsdl` HTTP podstawowy adres usługi. Na przykład:`http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
