---
title: "Instrukcje: Implementowanie kontraktu usługi WCF (Windows Communication Foundation)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
caps.latest.revision: "38"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c8ef9d97d9ed76175c0ca4c4d5ba40ca401f8f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="03f57-102">Instrukcje: Implementowanie kontraktu usługi WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="03f57-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="03f57-103">Jest to drugi sześć zadania wymagane do utworzenia podstawowego [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi i klienta, który można wywołać usługi.</span><span class="sxs-lookup"><span data-stu-id="03f57-103">This is the second of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service and a client that can call the service.</span></span> <span data-ttu-id="03f57-104">Przegląd wszystkich sześciu zadań, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="03f57-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="03f57-105">Następnym krokiem w tworzeniu aplikacji WCF jest zaimplementowanie interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="03f57-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="03f57-106">To związane z utworzeniem klasy o nazwie `CalculatorService` z zaimplementowanym interfejsem użytkownika `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="03f57-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>  
  
### <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="03f57-107">Aby zaimplementować kontrakt usługi WCF</span><span class="sxs-lookup"><span data-stu-id="03f57-107">To implement a WCF service contract</span></span>  
  
1.  <span data-ttu-id="03f57-108">Otwórz plik Service1.cs lub Service1.vb i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="03f57-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>  
  
    ```csharp  
    //Service1.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
        public class CalculatorService : ICalculator  
        {  
            public double Add(double n1, double n2)  
            {  
                double result = n1 + n2;  
                Console.WriteLine("Received Add({0},{1})", n1, n2);  
                // Code added to write output to the console window.  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Subtract(double n1, double n2)  
            {  
                double result = n1 - n2;  
                Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Multiply(double n1, double n2)  
            {  
                double result = n1 * n2;  
                Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Divide(double n1, double n2)  
            {  
                double result = n1 / n2;  
                Console.WriteLine("Received Divide({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
        }  
    }  
    ```  
  
    ```vb
    ‘Service1.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        Public Class CalculatorService  
            Implements ICalculator  
  
            Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
                Dim result As Double = n1 + n2  
                ' Code added to write output to the console window.  
                Console.WriteLine("Received Add({0},{1})", n1, n2)  
                Console.WriteLine("Return: {0}", result)  
                Return result  
            End Function  
  
            Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
                Dim result As Double = n1 - n2  
                Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
                Console.WriteLine("Return: {0}", result)  
                Return result  
  
            End Function  
  
            Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
                Dim result As Double = n1 * n2  
                Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
                Console.WriteLine("Return: {0}", result)  
                Return result  
  
            End Function  
  
            Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
                Dim result As Double = n1 / n2  
                Console.WriteLine("Received Divide({0},{1})", n1, n2)  
                Console.WriteLine("Return: {0}", result)  
                Return result  
  
            End Function  
        End Class  
    End Namespace  
    ```  
  
     <span data-ttu-id="03f57-109">Każda metoda implementuje operację Kalkulator i zapisuje tekst konsolę, aby ułatwić testowanie.</span><span class="sxs-lookup"><span data-stu-id="03f57-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03f57-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="03f57-110">Example</span></span>  
 <span data-ttu-id="03f57-111">Poniższy kod przedstawia zarówno Interfejs definiujący kontrakt i implementacja interfejsu.</span><span class="sxs-lookup"><span data-stu-id="03f57-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
        public interface ICalculator  
        {  
            [OperationContract]  
            double Add(double n1, double n2);  
            [OperationContract]  
            double Subtract(double n1, double n2);  
            [OperationContract]  
            double Multiply(double n1, double n2);  
            [OperationContract]  
            double Divide(double n1, double n2);  
        }  
}  
```  
  
```csharp
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            // Code added to write output to the console window.  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```vb
‘IService.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
    Public Interface ICalculator  
  
        <OperationContract()> _  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
End Namespace  
```  
  
```vb
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    Public Class CalculatorService  
        Implements ICalculator  
  
        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
            Dim result As Double = n1 + n2  
            ' Code added to write output to the console window.  
            Console.WriteLine("Received Add({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
        End Function  
  
        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
            Dim result As Double = n1 - n2  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
            Dim result As Double = n1 * n2  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
            Dim result As Double = n1 / n2  
            Console.WriteLine("Received Divide({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
    End Class  
End Namespace  
```  
  
 <span data-ttu-id="03f57-112">Kontrakt usługi jest teraz utworzony i zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="03f57-112">Now the service contract is created and implemented.</span></span> <span data-ttu-id="03f57-113">Skompiluj rozwiązanie, aby upewnić się, nie ma żadnych błędów kompilacji, a następnie przejdź do [porady: hostowanie i uruchamianie podstawowej usługi](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md) do uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="03f57-113">Build the solution to ensure there are no compilation errors and then proceed to [How to: Host and Run a Basic Service](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md) to run the service.</span></span> <span data-ttu-id="03f57-114">Aby uzyskać informacje dotyczące rozwiązywania problemów, zobacz [Rozwiązywanie problemów z Samouczek wprowadzający](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="03f57-114">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03f57-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="03f57-115">Compiling the Code</span></span>  
 <span data-ttu-id="03f57-116">Jeśli używasz programu Visual Studio w menu kompilacji kliknij Kompiluj rozwiązanie (lub naciśnij klawisze CTRL + SHIFT + B).</span><span class="sxs-lookup"><span data-stu-id="03f57-116">If you are using Visual Studio, on the Build menu click Build Solution (or press CTRL+SHIFT+B).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f57-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03f57-117">See Also</span></span>  
 [<span data-ttu-id="03f57-118">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="03f57-118">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="03f57-119">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="03f57-119">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
