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
# <a name="poco-support"></a><span data-ttu-id="6d4f7-102">Obsługa obiektów POCO</span><span class="sxs-lookup"><span data-stu-id="6d4f7-102">POCO Support</span></span>
<span data-ttu-id="6d4f7-103">Ten przykład pokazuje obsługę serializacji dla nieoznaczonych typów; oznacza to, że typy, do których nie zastosowano atrybutów serializacji, czasami określane jako zwykły typ obiektów CLR (POCO).</span><span class="sxs-lookup"><span data-stu-id="6d4f7-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="6d4f7-104"><xref:System.Runtime.Serialization.DataContractSerializer>Wnioskuje o umowę danych dla wszystkich publicznych nieoznaczonych typów, które mają konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="6d4f7-105">Kontrakty danych umożliwiają przekazywanie danych strukturalnych do i z usług.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="6d4f7-106">Aby uzyskać więcej informacji na temat typów nieoznaczonych, zobacz typy możliwe do [serializacji](../feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="6d4f7-106">For more information about unmarked types, see [Serializable Types](../feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="6d4f7-107">Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md), ale używa liczb złożonych zamiast pierwotnych typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-107">This sample is based on the [Getting Started](getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="6d4f7-108">Jest również podobna do podstawowego przykładu [kontraktu danych](basic-data-contract.md) , z tą różnicą, że <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty i nie są używane.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-108">It is also similar to the [Basic Data Contract](basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="6d4f7-109">Usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).</span><span class="sxs-lookup"><span data-stu-id="6d4f7-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d4f7-110">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6d4f7-111">`ComplexNumber`Klasa jest używana w `ServiceContract` .</span><span class="sxs-lookup"><span data-stu-id="6d4f7-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="6d4f7-112">`ComplexNumber`Typ nie ma <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów i, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="6d4f7-113">Domyślnie wszystkie właściwości publiczne i pola są serializowane.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-113">By default, all public properties and fields are serialized.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6d4f7-114">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="6d4f7-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6d4f7-115">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d4f7-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6d4f7-116">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d4f7-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6d4f7-117">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d4f7-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6d4f7-118">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6d4f7-119">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="6d4f7-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6d4f7-120">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d4f7-121">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6d4f7-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="6d4f7-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d4f7-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="6d4f7-123">Typy z możliwością serializowania</span><span class="sxs-lookup"><span data-stu-id="6d4f7-123">Serializable Types</span></span>](../feature-details/serializable-types.md)
