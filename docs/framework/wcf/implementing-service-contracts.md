---
title: Implementowanie kontraktów usług
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196323"
---
# <a name="implementing-service-contracts"></a>Implementowanie kontraktów usług
Usługa jest klasa, która udostępnia funkcje dostępne dla klientów w jednej lub więcej punktów końcowych. Aby utworzyć usługę, należy napisać klasę, która implementuje kontraktu usługi Windows Communication Foundation (WCF). Można zrobić to w jednym z dwóch sposobów. Można zdefiniować kontrakt oddzielnie jako interfejs, a następnie Utwórz klasę, która implementuje ten interfejs. Alternatywnie można utworzyć klasy i umowę bezpośrednio przez umieszczenie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu w samej klasy i <xref:System.ServiceModel.OperationContractAttribute> atrybutu metody dostępne dla klientów usługi.  
  
## <a name="creating-a-service-class"></a>Tworzenie klasy usługi  
 Oto przykład to usługa, która implementuje `IMath` kontraktu, który został zdefiniowany oddzielnie.  
  
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
  
 Alternatywnie usługa może bezpośrednio ujawnianie kontraktu. Oto przykład klasy usługi, który definiuje i implementuje `MathService` kontraktu.  
  
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
  
 Należy pamiętać, że wcześniej wymienionych usług uwidaczniać różnymi umowami, ponieważ nazwy kontraktu różnią się. W pierwszym przypadku narażonych umowy o nazwie "`IMath`"a w drugim przypadku nosi nazwę kontraktu"`MathService`".  
  
 Możesz ustawić kilka rzeczy na usługi i operacji poziomy implementacji, takich jak współbieżność i wystąpień. Aby uzyskać więcej informacji, zobacz [projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Po zaimplementowaniu kontraktu usługi, należy utworzyć jeden lub więcej punktów końcowych usługi. Aby uzyskać więcej informacji, zobacz [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md). Aby uzyskać więcej informacji na temat sposobu uruchamiania usługi, zobacz [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie i implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Instrukcje: tworzenie usługi za pomocą klasy kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Instrukcje: tworzenie usługi przy użyciu interfejsu kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Określanie zachowania środowiska uruchomieniowego usługi](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
