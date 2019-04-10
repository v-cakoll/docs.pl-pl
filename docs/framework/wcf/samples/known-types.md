---
title: Znane typy
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: 2d2818dc78829bd201aeeba9b0df1d2f3b356250
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203603"
---
# <a name="known-types"></a><span data-ttu-id="fcc05-102">Znane typy</span><span class="sxs-lookup"><span data-stu-id="fcc05-102">Known Types</span></span>
<span data-ttu-id="fcc05-103">W tym przykładzie pokazano, jak Podaj informacje o typach pochodnych w kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="fcc05-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="fcc05-104">Kontrakty danych umożliwia przekazanie ze strukturą danych do i z usługi.</span><span class="sxs-lookup"><span data-stu-id="fcc05-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="fcc05-105">W programowanie zorientowane obiektowo, typu, który dziedziczy z innego typu, może służyć zamiast oryginalnego typu.</span><span class="sxs-lookup"><span data-stu-id="fcc05-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="fcc05-106">Podczas programowania zorientowanego na usługi, schematów, a nie typy są przekazywane, a w związku z tym, nie są zachowywane relacji między typami.</span><span class="sxs-lookup"><span data-stu-id="fcc05-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="fcc05-107"><xref:System.Runtime.Serialization.KnownTypeAttribute> Atrybut umożliwia informacji na temat typów pochodnych, które mają zostać uwzględnione w kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="fcc05-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="fcc05-108">Mechanizm ten nie jest używany, typem pochodnym nie wysyłane lub odbierane, gdy oczekiwany jest typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="fcc05-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcc05-109">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fcc05-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fcc05-110">Umowa serwisowa usługi używa liczby zespolone, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fcc05-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="fcc05-111"><xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> jest stosowany do `ComplexNumber` klasy, aby wskazać, które pola klasy mogą być przekazywane między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="fcc05-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="fcc05-112">Pochodnej `ComplexNumberWithMagnitude` klasa może być używana zamiast `ComplexNumber`.</span><span class="sxs-lookup"><span data-stu-id="fcc05-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="fcc05-113"><xref:System.Runtime.Serialization.KnownTypeAttribute> Atrybutu na `ComplexNumber` typ wskazuje na to.</span><span class="sxs-lookup"><span data-stu-id="fcc05-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
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
  
 <span data-ttu-id="fcc05-114">`ComplexNumberWithMagnitude` Typ pochodzi z `ComplexNumber` , ale dodaje element członkowski danych dodatkowych `Magnitude`.</span><span class="sxs-lookup"><span data-stu-id="fcc05-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
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
  
 <span data-ttu-id="fcc05-115">Aby zademonstrować tę funkcję znane typy, usługa jest wdrażana w taki sposób, który zwraca `ComplexNumberWithMagnitude` tylko w przypadku dodawania i odejmowania.</span><span class="sxs-lookup"><span data-stu-id="fcc05-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="fcc05-116">(Mimo że kontrakt Określa `ComplexNumber`, jest to dozwolone z powodu `KnownTypeAttribute` atrybutu).</span><span class="sxs-lookup"><span data-stu-id="fcc05-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="fcc05-117">Mnożenia i dzielenia, nadal zwracają base `ComplexNumber` typu.</span><span class="sxs-lookup"><span data-stu-id="fcc05-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
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
  
 <span data-ttu-id="fcc05-118">Na komputerze klienckim, kontrakt usługi i kontraktu danych są zdefiniowane w generatedClient.cs pliku źródłowego, który jest generowany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="fcc05-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="fcc05-119">Ponieważ <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut jest określony w umowie danych usługi, klient jest możliwość odbierania zarówno `ComplexNumber` i `ComplexNumberWithMagnitude` klasy podczas korzystania z usługi.</span><span class="sxs-lookup"><span data-stu-id="fcc05-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="fcc05-120">Klient wykrywa, czy masz `ComplexNumberWithMagnitude` i wygenerować odpowiednie dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="fcc05-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
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
  
 <span data-ttu-id="fcc05-121">Po uruchomieniu przykładu, żądań i odpowiedzi operacji są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="fcc05-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="fcc05-122">Należy pamiętać, że powstanie zostanie wydrukowany do dodawania i odejmowania, ale nie dla mnożenia i dzielenia, ze względu na sposób usługa została zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="fcc05-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="fcc05-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="fcc05-123">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fcc05-124">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="fcc05-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fcc05-125">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fcc05-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fcc05-126">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fcc05-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="fcc05-127">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fcc05-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fcc05-128">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fcc05-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fcc05-129">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fcc05-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fcc05-130">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="fcc05-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fcc05-131">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fcc05-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
