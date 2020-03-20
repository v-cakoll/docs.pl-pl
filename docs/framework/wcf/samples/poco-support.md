---
title: Obsługa obiektów POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: e94f6d9576ed96613d975a66c1965820002f94ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183416"
---
# <a name="poco-support"></a>Obsługa obiektów POCO
W tym przykładzie pokazano obsługę serializacji dla nieoznaczonych typów; oznacza to, że typy, do których atrybuty serializacji nie zostały zastosowane, czasami określane jako zwykły stary obiekt CLR (POCO) typy. Wnioskuje <xref:System.Runtime.Serialization.DataContractSerializer> kontrakt danych dla wszystkich publicznych nieoznaczonych typów, które mają konstruktora bez parametrów. Kontrakty danych umożliwiają przekazywanie danych strukturalnych do i z usług. Aby uzyskać więcej informacji na temat typów nieoznaczonych, zobacz [Typy serializable](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md)ale używa liczby zespolonej zamiast pierwotnych typów liczbowych. Jest również podobny do próbki [umowy danych podstawowych,](../../../../docs/framework/wcf/samples/basic-data-contract.md) z tą różnicą, <xref:System.Runtime.Serialization.DataContractAttribute> że i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty nie są używane.  
  
 Usługa jest obsługiwana przez internetowe usługi informacyjne (IIS), a klient jest aplikacją konsoli (.exe).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa `ComplexNumber` jest używana `ServiceContract`w . Typ `ComplexNumber` nie ma <xref:System.Runtime.Serialization.DataContractAttribute> atrybutów i, <xref:System.Runtime.Serialization.DataMemberAttribute> jak pokazano w poniższym przykładowym kodzie. Domyślnie wszystkie właściwości publiczne i pola są serializowane.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Typy z możliwością serializowania](../../../../docs/framework/wcf/feature-details/serializable-types.md)
