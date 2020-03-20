---
title: 'Samouczek: Zaimplementowanie umowy serwisowej programu Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184067"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="df9b8-102">Samouczek: Zaimplementowanie umowy serwisowej programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="df9b8-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="df9b8-103">W tym samouczku opisano drugie z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="df9b8-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="df9b8-104">Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="df9b8-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="df9b8-105">Następnym krokiem do tworzenia aplikacji WCF jest dodanie kodu do zaimplementowania interfejsu usługi WCF, który został utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="df9b8-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="df9b8-106">W tym kroku należy utworzyć `CalculatorService` klasę o nazwie, `ICalculator` która implementuje interfejs zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df9b8-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="df9b8-107">Każda metoda w poniższym kodzie wywołuje operację kalkulatora i zapisuje tekst w konsoli, aby ją przetestować.</span><span class="sxs-lookup"><span data-stu-id="df9b8-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="df9b8-108">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="df9b8-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="df9b8-109">Dodaj kod, aby zaimplementować kontrakt serwisowy WCF.</span><span class="sxs-lookup"><span data-stu-id="df9b8-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="df9b8-110">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="df9b8-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="df9b8-111">Dodaj kod do zaimplementowania umowy serwisowej WCF</span><span class="sxs-lookup"><span data-stu-id="df9b8-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="df9b8-112">W **gettingstartedlib**otwórz plik **Service1.cs** lub **Service1.vb** i zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="df9b8-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="df9b8-113">Edytuj plik App.config</span><span class="sxs-lookup"><span data-stu-id="df9b8-113">Edit App.config</span></span>

<span data-ttu-id="df9b8-114">Edytuj **app.config** w **GettingStartedLib,** aby odzwierciedlić zmiany wprowadzone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="df9b8-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="df9b8-115">W przypadku projektów visual c#:</span><span class="sxs-lookup"><span data-stu-id="df9b8-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="df9b8-116">Zmień linię 14 na`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="df9b8-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="df9b8-117">Zmień linię 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="df9b8-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="df9b8-118">Zmień linię 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="df9b8-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="df9b8-119">W przypadku projektów visual basic:</span><span class="sxs-lookup"><span data-stu-id="df9b8-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="df9b8-120">Zmień linię 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="df9b8-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="df9b8-121">Zmień linię 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="df9b8-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="df9b8-122">Zmień linię 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="df9b8-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="df9b8-123">Skompiluj kod</span><span class="sxs-lookup"><span data-stu-id="df9b8-123">Compile the code</span></span>

<span data-ttu-id="df9b8-124">Skompiluj rozwiązanie, aby sprawdzić, czy nie ma żadnych błędów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="df9b8-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="df9b8-125">Jeśli używasz programu Visual Studio, w menu **Kompilacja** wybierz opcję **Kompilacja rozwiązania** (lub naciśnij klawisz **Ctrl**+**Shift**+**B**).</span><span class="sxs-lookup"><span data-stu-id="df9b8-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="df9b8-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="df9b8-126">Next steps</span></span>

<span data-ttu-id="df9b8-127">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="df9b8-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="df9b8-128">Dodaj kod, aby zaimplementować kontrakt serwisowy WCF.</span><span class="sxs-lookup"><span data-stu-id="df9b8-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="df9b8-129">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="df9b8-129">Build the solution.</span></span>

<span data-ttu-id="df9b8-130">Przejdź do następnego samouczka, aby dowiedzieć się, jak uruchomić usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="df9b8-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df9b8-131">Samouczek: Host i uruchom podstawową usługę WCF</span><span class="sxs-lookup"><span data-stu-id="df9b8-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
