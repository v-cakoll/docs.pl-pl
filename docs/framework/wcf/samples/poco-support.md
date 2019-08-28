---
title: Obsługa obiektów POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 6796d7948bd3ebe0a8b96a861c628b30b7540912
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044779"
---
# <a name="poco-support"></a>Obsługa obiektów POCO
Ten przykład pokazuje obsługę serializacji dla nieoznaczonych typów; oznacza to, że typy, do których nie zastosowano atrybutów serializacji, czasami określane jako zwykły typ obiektów CLR (POCO). <xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje o umowę danych dla wszystkich publicznych nieoznaczonych typów, które mają konstruktora bez parametrów. Kontrakty danych umożliwiają przekazywanie danych strukturalnych do i z usług. Aby uzyskać więcej informacji na temat typów nieoznaczonych, zobacz typy możliwe do [serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale używa liczb złożonych zamiast pierwotnych typów liczbowych. Jest również podobna do podstawowego przykładu [kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md) , z tą różnicą <xref:System.Runtime.Serialization.DataContractAttribute> , <xref:System.Runtime.Serialization.DataMemberAttribute> że atrybuty i nie są używane.  
  
 Usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa jest używana `ServiceContract`w. `ComplexNumber` Typ nie ma atrybutów <xref:System.Runtime.Serialization.DataMemberAttribute> i, jak pokazano w poniższym przykładowym kodzie. <xref:System.Runtime.Serialization.DataContractAttribute> `ComplexNumber` Domyślnie wszystkie właściwości publiczne i pola są serializowane.  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Typy z możliwością serializowania](../../../../docs/framework/wcf/feature-details/serializable-types.md)
