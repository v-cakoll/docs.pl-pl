---
title: Implementowanie kontraktów usług
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: ac27329278edc2b9ca693aa15bcc5bb58edffe05
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320160"
---
# <a name="implementing-service-contracts"></a>Implementowanie kontraktów usług
Usługa jest klasą, która udostępnia klientom funkcje dostępne dla klientów w co najmniej jednym punkcie końcowym. Aby utworzyć usługę, napisz klasę implementującą kontrakt Windows Communication Foundation (WCF). Można to zrobić na jeden z dwóch sposobów. Kontrakt można zdefiniować oddzielnie jako interfejs, a następnie utworzyć klasę, która implementuje ten interfejs. Alternatywnie można utworzyć klasę i umowę bezpośrednio przez umieszczenie atrybutu <xref:System.ServiceModel.ServiceContractAttribute> w samej klasie i atrybutu <xref:System.ServiceModel.OperationContractAttribute> w metodach dostępnych dla klientów usługi.  
  
## <a name="creating-a-service-class"></a>Tworzenie klasy usługi  
 Poniżej znajduje się przykład usługi implementującej kontrakt `IMath`, który został zdefiniowany osobno.  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Alternatywnie usługa może bezpośrednio uwidocznić umowę. Poniżej znajduje się przykład klasy usługi, która definiuje i implementuje kontrakt `MathService`.  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Należy pamiętać, że poprzednie usługi uwidaczniają różne kontrakty, ponieważ nazwy kontraktów są różne. W pierwszym przypadku umowa o nazwie "`IMath`" występuje w drugim przypadku kontraktu o nazwie "`MathService`".  
  
 Można ustawić kilka rzeczy na poziomach implementacji usługi i operacji, takich jak współbieżność i Tworzenie wystąpień. Aby uzyskać więcej informacji, zobacz [projektowanie i implementowanie usług](designing-and-implementing-services.md).  
  
 Po wdrożeniu kontraktu usługi należy utworzyć co najmniej jeden punkt końcowy dla usługi. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia punktów końcowych](endpoint-creation-overview.md). Aby uzyskać więcej informacji na temat sposobu uruchamiania usługi, zobacz [usługi hostingu](hosting-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie i implementowanie usług](designing-and-implementing-services.md)
- [Instrukcje: tworzenie usługi za pomocą klasy kontraktu](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Instrukcje: tworzenie usługi przy użyciu interfejsu kontraktu](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Określanie zachowania środowiska uruchomieniowego usługi](specifying-service-run-time-behavior.md)
