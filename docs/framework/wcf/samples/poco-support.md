---
title: Obsługa obiektów POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: a9f8d185c58b22e68f7a8c11954e0e534c4bd48f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600467"
---
# <a name="poco-support"></a>Obsługa obiektów POCO
Ten przykład pokazuje obsługę serializacji dla nieoznaczonych typów; oznacza to, że typy, do których nie zastosowano atrybutów serializacji, czasami określane jako zwykły typ obiektów CLR (POCO). <xref:System.Runtime.Serialization.DataContractSerializer>Wnioskuje o umowę danych dla wszystkich publicznych nieoznaczonych typów, które mają konstruktora bez parametrów. Kontrakty danych umożliwiają przekazywanie danych strukturalnych do i z usług. Aby uzyskać więcej informacji na temat typów nieoznaczonych, zobacz typy możliwe do [serializacji](../feature-details/serializable-types.md).  
  
 Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md), ale używa liczb złożonych zamiast pierwotnych typów liczbowych. Jest również podobna do podstawowego przykładu [kontraktu danych](basic-data-contract.md) , z tą różnicą, że <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty i nie są używane.  
  
 Usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 `ComplexNumber`Klasa jest używana w `ServiceContract` . `ComplexNumber`Typ nie ma <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów i, jak pokazano w poniższym przykładowym kodzie. Domyślnie wszystkie właściwości publiczne i pola są serializowane.  
  
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
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Typy z możliwością serializowania](../feature-details/serializable-types.md)
