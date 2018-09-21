---
title: 'Instrukcje: Implementowanie kontraktu usługi WCF (Windows Communication Foundation)'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 569de6f49b56b46ccfeb22e9f0bd25bcf339b7e0
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46528791"
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="454ec-102">Instrukcje: Implementowanie kontraktu usługi WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="454ec-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="454ec-103">Jest to drugi z sześciu zadań podrzędnych, wymagane do utworzenia podstawowej usługi Windows Communication Foundation (WCF) i klienta, który można wywołać usługi.</span><span class="sxs-lookup"><span data-stu-id="454ec-103">This is the second of six tasks required to create a basic Windows Communication Foundation (WCF) service and a client that can call the service.</span></span> <span data-ttu-id="454ec-104">Aby uzyskać omówienie wszystkich sześciu zadań podrzędnych, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="454ec-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="454ec-105">Następnym krokiem w tworzeniu aplikacji WCF jest zaimplementowanie interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="454ec-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="454ec-106">To związane z utworzeniem klasy o nazwie `CalculatorService` implementującej zdefiniowany przez użytkownika `ICalculator` interfejs...</span><span class="sxs-lookup"><span data-stu-id="454ec-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>

## <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="454ec-107">Aby zaimplementować kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="454ec-107">To implement a WCF service contract</span></span>

<span data-ttu-id="454ec-108">Otwórz plik Service1.cs lub Service1.vb i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="454ec-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>

```csharp
using System;
using System.ServiceModel;

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

<span data-ttu-id="454ec-109">Każda metoda implementuje operację Kalkulator i zapisuje jakiś tekst do konsoli, aby ułatwić testowanie.</span><span class="sxs-lookup"><span data-stu-id="454ec-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>

## <a name="example"></a><span data-ttu-id="454ec-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="454ec-110">Example</span></span>

<span data-ttu-id="454ec-111">Poniższy kod przedstawia obie interfejs który definiuje kontrakt i implementacja interfejsu.</span><span class="sxs-lookup"><span data-stu-id="454ec-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>

```csharp
using System;
using System.ServiceModel;

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
using System;
using System.ServiceModel;

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

## <a name="compile-the-code"></a><span data-ttu-id="454ec-112">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="454ec-112">Compile the code</span></span>

<span data-ttu-id="454ec-113">Kompiluj rozwiązanie, aby upewnić się, że nie ma żadnych błędów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="454ec-113">Build the solution to ensure there are no compilation errors.</span></span> <span data-ttu-id="454ec-114">Jeśli używasz programu Visual Studio na **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie** (lub naciśnij **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="454ec-114">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="454ec-115">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="454ec-115">Next steps</span></span>

<span data-ttu-id="454ec-116">Kontrakt usługi jest utworzone i zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="454ec-116">Now the service contract is created and implemented.</span></span> <span data-ttu-id="454ec-117">W następnym kroku możesz uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="454ec-117">In the next step, you run the service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="454ec-118">Instrukcje: hostowanie i uruchamianie podstawowej usługi</span><span class="sxs-lookup"><span data-stu-id="454ec-118">How to: Host and Run a Basic Service</span></span>](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

<span data-ttu-id="454ec-119">Aby uzyskać informacje dotyczące rozwiązywania problemów, zobacz [Rozwiązywanie problemów z samouczka Wprowadzenie](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="454ec-119">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="454ec-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="454ec-120">See also</span></span>

- [<span data-ttu-id="454ec-121">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="454ec-121">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="454ec-122">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="454ec-122">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)