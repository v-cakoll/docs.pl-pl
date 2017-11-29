---
title: "Obsługa obiektów POCO"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0607ea270b32aa0ae02e6ed0b0eecfa6c4c0d054
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="poco-support"></a><span data-ttu-id="fbc26-102">Obsługa obiektów POCO</span><span class="sxs-lookup"><span data-stu-id="fbc26-102">POCO Support</span></span>
<span data-ttu-id="fbc26-103">W tym przykładzie przedstawiono obsługę serializacji nieoznaczone typy; oznacza to, że typy, do których nie zostały zastosowane atrybutów serializacji, czasami określane jako typy zwykłego obiektu CLR stary (POCO).</span><span class="sxs-lookup"><span data-stu-id="fbc26-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="fbc26-104"><xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje kontraktu danych dla wszystkich publicznych nieoznaczone typy, które ma domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fbc26-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a default constructor.</span></span> <span data-ttu-id="fbc26-105">Kontrakty danych umożliwiają przekazywania strukturalnych danych do i z usług.</span><span class="sxs-lookup"><span data-stu-id="fbc26-105">Data contracts allow you to pass structured data to and from services.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fbc26-106">nieoznaczone typy, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="fbc26-106"> unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="fbc26-107">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale używa liczby złożone zamiast liczbowych typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="fbc26-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="fbc26-108">Jest również podobne do [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md) przykładowe, z wyjątkiem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty nie są używane.</span><span class="sxs-lookup"><span data-stu-id="fbc26-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="fbc26-109">Usługa jest obsługiwana przez Internet Information Services (IIS) i klient jest aplikacji konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="fbc26-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbc26-110">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fbc26-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fbc26-111">`ComplexNumber` Klasa jest używana w `ServiceContract`.</span><span class="sxs-lookup"><span data-stu-id="fbc26-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="fbc26-112">`ComplexNumber` Typ nie ma <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="fbc26-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="fbc26-113">Domyślnie wszystkie właściwości publiczne i pola są serializowane.</span><span class="sxs-lookup"><span data-stu-id="fbc26-113">By default, all public properties and fields are serialized.</span></span>  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fbc26-114">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="fbc26-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fbc26-115">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbc26-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fbc26-116">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbc26-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="fbc26-117">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbc26-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fbc26-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fbc26-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fbc26-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fbc26-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fbc26-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="fbc26-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fbc26-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fbc26-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="fbc26-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbc26-122">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [<span data-ttu-id="fbc26-123">Typów możliwych do serializacji</span><span class="sxs-lookup"><span data-stu-id="fbc26-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
