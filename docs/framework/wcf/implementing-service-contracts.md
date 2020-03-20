---
title: Implementowanie kontraktów usług
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: aefe146a8941d98d7d9138e4ece83c330c967034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184003"
---
# <a name="implementing-service-contracts"></a>Implementowanie kontraktów usług
Usługa jest klasą, która udostępnia funkcje dostępne dla klientów w jednym lub więcej punktów końcowych. Aby utworzyć usługę, napisz klasę, która implementuje kontrakt programu Windows Communication Foundation (WCF). Możesz to zrobić na dwa sposoby. Kontrakt można zdefiniować oddzielnie jako interfejs, a następnie utworzyć klasę, która implementuje ten interfejs. Alternatywnie można utworzyć klasę i kontrakt bezpośrednio, <xref:System.ServiceModel.ServiceContractAttribute> umieszczając atrybut na samej klasie i <xref:System.ServiceModel.OperationContractAttribute> atrybut na metody dostępne dla klientów usługi.  
  
## <a name="creating-a-service-class"></a>Tworzenie klasy usługi  
 Poniżej przedstawiono przykład usługi, która `IMath` implementuje kontrakt, który został zdefiniowany oddzielnie.  
  
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
  
 Alternatywnie usługa może ujawnić umowy bezpośrednio. Poniżej przedstawiono przykład klasy usługi, która definiuje `MathService` i implementuje kontrakt.  
  
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
  
 Należy zauważyć, że poprzednie usługi uwidaczniają różne kontrakty, ponieważ nazwy kontraktów są różne. W pierwszym przypadku wystawiona umowa`IMath`nosi nazwę " ", podczas gdy`MathService`w drugim przypadku umowa nosi nazwę " ".  
  
 Można ustawić kilka rzeczy na poziomie wykonania usługi i operacji, takich jak współbieżność i instancing. Aby uzyskać więcej informacji, zobacz [Projektowanie i wdrażanie usług](designing-and-implementing-services.md).  
  
 Po zaimplementowanie umowy serwisowej należy utworzyć jeden lub więcej punktów końcowych dla usługi. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia punktu końcowego](endpoint-creation-overview.md). Aby uzyskać więcej informacji na temat uruchamiania usługi, zobacz [Usługi hostingowe](hosting-services.md).  
  
## <a name="see-also"></a>Zobacz też

- [Projektowanie i implementowanie usług](designing-and-implementing-services.md)
- [Instrukcje: tworzenie usługi za pomocą klasy kontraktu](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Określanie zachowania środowiska uruchomieniowego usługi](specifying-service-run-time-behavior.md)
