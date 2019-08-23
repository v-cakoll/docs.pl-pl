---
title: Obsługa obiektów POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 90b55362c1958ea5677e3bc0cdca906bb3af6b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965554"
---
# <a name="poco-support"></a><span data-ttu-id="124ad-102">Obsługa obiektów POCO</span><span class="sxs-lookup"><span data-stu-id="124ad-102">POCO Support</span></span>
<span data-ttu-id="124ad-103">Ten przykład pokazuje obsługę serializacji dla nieoznaczonych typów; oznacza to, że typy, do których nie zastosowano atrybutów serializacji, czasami określane jako zwykły typ obiektów CLR (POCO).</span><span class="sxs-lookup"><span data-stu-id="124ad-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="124ad-104"><xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje o umowę danych dla wszystkich publicznych nieoznaczonych typów, które mają konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="124ad-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="124ad-105">Kontrakty danych umożliwiają przekazywanie danych strukturalnych do i z usług.</span><span class="sxs-lookup"><span data-stu-id="124ad-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="124ad-106">Aby uzyskać więcej informacji na temat typów nieoznaczonych, zobacz typy możliwe do [serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="124ad-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="124ad-107">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale używa liczb złożonych zamiast pierwotnych typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="124ad-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="124ad-108">Jest również podobna do podstawowego przykładu [kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md) , z tą różnicą <xref:System.Runtime.Serialization.DataContractAttribute> , <xref:System.Runtime.Serialization.DataMemberAttribute> że atrybuty i nie są używane.</span><span class="sxs-lookup"><span data-stu-id="124ad-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="124ad-109">Usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).</span><span class="sxs-lookup"><span data-stu-id="124ad-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="124ad-110">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="124ad-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="124ad-111">Klasa jest używana `ServiceContract`w. `ComplexNumber`</span><span class="sxs-lookup"><span data-stu-id="124ad-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="124ad-112">Typ nie ma atrybutów <xref:System.Runtime.Serialization.DataMemberAttribute> i, jak pokazano w poniższym przykładowym kodzie. <xref:System.Runtime.Serialization.DataContractAttribute> `ComplexNumber`</span><span class="sxs-lookup"><span data-stu-id="124ad-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="124ad-113">Domyślnie wszystkie właściwości publiczne i pola są serializowane.</span><span class="sxs-lookup"><span data-stu-id="124ad-113">By default, all public properties and fields are serialized.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="124ad-114">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="124ad-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="124ad-115">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="124ad-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="124ad-116">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="124ad-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="124ad-117">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="124ad-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="124ad-118">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="124ad-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="124ad-119">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="124ad-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="124ad-120">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="124ad-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="124ad-121">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="124ad-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="124ad-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="124ad-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="124ad-123">Typy z możliwością serializowania</span><span class="sxs-lookup"><span data-stu-id="124ad-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
