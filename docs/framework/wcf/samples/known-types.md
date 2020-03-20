---
title: Znane typy
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: b75f540694eaeea90367f1720d5747f71d0a392d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144620"
---
# <a name="known-types"></a><span data-ttu-id="1aa3c-102">Znane typy</span><span class="sxs-lookup"><span data-stu-id="1aa3c-102">Known Types</span></span>
<span data-ttu-id="1aa3c-103">W tym przykładzie pokazano, jak określić informacje o typach pochodnych w umowie dotyczącej danych.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="1aa3c-104">Kontrakty danych umożliwiają przekazywanie danych strukturalnych do i z usług.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="1aa3c-105">W programowaniu obiektowym można użyć typu dziedziczącego z innego typu zamiast oryginalnego typu.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="1aa3c-106">W programowaniu zorientowanym na usługi schematy zamiast typów są przekazywane i dlatego relacja między typami nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="1aa3c-107">Atrybut <xref:System.Runtime.Serialization.KnownTypeAttribute> umożliwia informacje o typach pochodnych, które mają być zawarte w umowie danych.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="1aa3c-108">Jeśli ten mechanizm nie jest używany, typ pochodny nie można wysłać lub odebrane, gdy oczekuje się typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1aa3c-109">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1aa3c-110">Umowa serwisowa dla usługi używa liczb zespolonych, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1aa3c-111">I jest stosowany do `ComplexNumber` klasy, aby wskazać, które pola klasy mogą być przekazywane między klientem a usługą. <xref:System.Runtime.Serialization.DataMemberAttribute> <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="1aa3c-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="1aa3c-112">Klasa pochodna `ComplexNumberWithMagnitude` może być używana `ComplexNumber`zamiast .</span><span class="sxs-lookup"><span data-stu-id="1aa3c-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="1aa3c-113">Atrybut <xref:System.Runtime.Serialization.KnownTypeAttribute> na typ `ComplexNumber` wskazuje to.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
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
  
 <span data-ttu-id="1aa3c-114">Typ `ComplexNumberWithMagnitude` pochodzi od `ComplexNumber` ale dodaje dodatkowy `Magnitude`element członkowski danych, .</span><span class="sxs-lookup"><span data-stu-id="1aa3c-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
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
  
 <span data-ttu-id="1aa3c-115">Aby zademonstrować znane typy funkcji, usługa jest implementowana `ComplexNumberWithMagnitude` w taki sposób, że zwraca tylko do dodawania i odejmowania.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="1aa3c-116">(Mimo że umowa `ComplexNumber`określa , jest to `KnownTypeAttribute` dozwolone ze względu na atrybut).</span><span class="sxs-lookup"><span data-stu-id="1aa3c-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="1aa3c-117">Mnożenie i dzielenie `ComplexNumber` nadal zwracają typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
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
  
 <span data-ttu-id="1aa3c-118">Na kliencie zarówno umowy serwisowej, jak i umowy danych są zdefiniowane w pliku źródłowym generatedClient.cs, który jest generowany przez [Narzędzie narzędzia Metadane ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="1aa3c-119">Ponieważ <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut jest określony w umowie danych usługi, klient może odbierać zarówno `ComplexNumber` i `ComplexNumberWithMagnitude` klas podczas korzystania z usługi.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="1aa3c-120">Klient wykrywa, czy uzyskał `ComplexNumberWithMagnitude` a i wygeneruje odpowiednie dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1aa3c-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
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
  
 <span data-ttu-id="1aa3c-121">Po uruchomieniu próbki żądania i odpowiedzi operacji są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="1aa3c-122">Należy zauważyć, że wielkość jest drukowana do dodawania i odejmowania, ale nie dla mnożenia i dzielenia ze względu na sposób, w jaki usługa została zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="1aa3c-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-123">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1aa3c-124">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="1aa3c-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1aa3c-125">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1aa3c-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1aa3c-126">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1aa3c-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1aa3c-127">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1aa3c-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1aa3c-128">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1aa3c-129">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1aa3c-130">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1aa3c-131">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
