---
title: Znane typy
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: dae271384905df890b2f42196d6e0aadad66be6f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591842"
---
# <a name="known-types"></a>Znane typy
Ten przykład pokazuje, jak określić informacje o typach pochodnych w kontrakcie danych. Kontrakty danych umożliwiają przekazywanie danych strukturalnych do i z usług. W programowaniu zorientowanym na obiekt, typ, który dziedziczy z innego typu, może być użyty zamiast oryginalnego typu. W programowaniu zorientowanym na usługę, schematy, a nie typy, są przekazywane i w związku z tym relacja między typami nie jest zachowywana. Ten <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut umożliwia uwzględnienie informacji o typach pochodnych w kontrakcie danych. Jeśli ten mechanizm nie jest używany, nie można wysłać ani odebrać typu pochodnego, gdzie oczekiwany jest typ podstawowy.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt usługi dla usługi używa liczb zespolonych, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <xref:System.Runtime.Serialization.DataContractAttribute>I <xref:System.Runtime.Serialization.DataMemberAttribute> jest stosowany do klasy, `ComplexNumber` Aby wskazać, które pola klasy mogą być przesyłane między klientem a usługą. Klasa pochodna `ComplexNumberWithMagnitude` może być używana zamiast `ComplexNumber` . <xref:System.Runtime.Serialization.KnownTypeAttribute>Atrybut tego `ComplexNumber` typu wskazuje na to.  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
[KnownType(typeof(ComplexNumberWithMagnitude))]  
public class ComplexNumber  
{  
    [DataMember]  
    public double Real = 0.0D;  
    [DataMember]  
    public double Imaginary = 0.0D;  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
 `ComplexNumberWithMagnitude`Typ pochodzi z `ComplexNumber` , ale dodaje dodatkowy element członkowski danych, `Magnitude` .  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumberWithMagnitude : ComplexNumber  
{  
    public ComplexNumberWithMagnitude(double real, double imaginary) :  
        base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary*Imaginary  + Real*Real); }  
        set { throw new NotImplementedException(); }  
    }  
}  
```  
  
 Aby przedstawić funkcję znanych typów, usługa jest zaimplementowana w taki sposób, że zwraca `ComplexNumberWithMagnitude` tylko do dodawania i odejmowania. (Mimo że kontrakt Określa `ComplexNumber` , jest to dozwolone z powodu `KnownTypeAttribute` atrybutu). Mnożenie i dzielenie nadal zwracają `ComplexNumber` Typ podstawowy.  
  
```csharp
public class DataContractCalculatorService : IDataContractCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real,  
                                      n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real,
                                 n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        //Return the base type.  
        return new ComplexNumber(real1 + real2, imaginary1 +
                                                  imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real,
                                     -1*n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
        //Return the base type.  
        return new ComplexNumber(numerator.Real / denominator.Real,  
                                             numerator.Imaginary);  
    }  
}  
```  
  
 Na kliencie zarówno kontrakt usługi, jak i kontrakt danych są zdefiniowane w pliku źródłowym generatedClient.cs, który jest generowany przez [Narzędzie narzędzia metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z metadanych usługi. Ponieważ <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut jest określony w kontrakcie danych usługi, klient może odbierać zarówno `ComplexNumber` klasy, jak i przy `ComplexNumberWithMagnitude` użyciu usługi. Klient wykrywa, czy pobrano `ComplexNumberWithMagnitude` i wygenerował odpowiednie dane wyjściowe:  
  
```csharp
// Create a client  
DataContractCalculatorClient client =
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber() { real = 1, imaginary = 2 };  
ComplexNumber value2 = new ComplexNumber() { real = 3, imaginary = 4 };  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.real, value1.imaginary, value2.real, value2.imaginary,  
    result.real, result.imaginary);  
if (result is ComplexNumberWithMagnitude)  
{  
    Console.WriteLine("Magnitude: {0}",
        ((ComplexNumberWithMagnitude)result).Magnitude);  
}  
else  
{  
    Console.WriteLine("No magnitude was sent from the service");  
}  
```  
  
 Po uruchomieniu przykładu żądania i odpowiedzi operacji są wyświetlane w oknie konsoli klienta. Należy zauważyć, że wielkość jest drukowana do dodawania i odejmowania, ale nie do mnożenia i dzielenia ze względu na sposób implementacji usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
    Press <ENTER> to terminate client.  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
