---
title: Obsługa obiektów POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 2962fa8a9eb824bbfbbb2f1e9347f8988b50ddcd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716543"
---
# <a name="poco-support"></a>Obsługa obiektów POCO
Ten przykład pokazuje obsługę serializacji dla nieoznaczonych typów; oznacza to, że typy, do których nie zastosowano atrybutów serializacji, czasami określane jako zwykły typ obiektów CLR (POCO). <xref:System.Runtime.Serialization.DataContractSerializer> wnioskuje o umowę danych dla wszystkich publicznych nieoznaczonych typów, które mają konstruktora bez parametrów. Kontrakty danych umożliwiają przekazywanie danych strukturalnych do i z usług. Aby uzyskać więcej informacji na temat typów nieoznaczonych, zobacz typy możliwe do [serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale używa liczb złożonych zamiast pierwotnych typów liczbowych. Jest również podobna do podstawowego przykładu [kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md) , z tą różnicą, że atrybuty <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> nie są używane.  
  
 Usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa `ComplexNumber` jest używana w `ServiceContract`. Typ `ComplexNumber` nie ma atrybutów <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute>, jak pokazano w poniższym przykładowym kodzie. Domyślnie wszystkie właściwości publiczne i pola są serializowane.  
  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Typy z możliwością serializowania](../../../../docs/framework/wcf/feature-details/serializable-types.md)
