---
title: 'Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 05923dc0a2223da5e5fcda483abc1ee1dd2d643f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928709"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="9515f-102">Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9515f-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="9515f-103">W tym samouczku opisano dwa z pięciu zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9515f-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="9515f-104">Aby zapoznać się z omówieniem samouczków, [zobacz Samouczek: Rozpocznij pracę z aplikacjami](getting-started-tutorial.md)Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="9515f-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="9515f-105">Następnym krokiem tworzenia aplikacji WCF jest dodanie kodu w celu zaimplementowania interfejsu usługi WCF, który został utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="9515f-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="9515f-106">W tym kroku utworzysz klasę o nazwie `CalculatorService` implementującej interfejs zdefiniowany `ICalculator` przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9515f-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="9515f-107">Każda metoda w poniższym kodzie wywołuje operację kalkulatora i zapisuje tekst w konsoli programu w celu jej przetestowania.</span><span class="sxs-lookup"><span data-stu-id="9515f-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="9515f-108">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9515f-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="9515f-109">Dodaj kod, aby zaimplementować kontrakt usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="9515f-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="9515f-110">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="9515f-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="9515f-111">Dodawanie kodu w celu zaimplementowania kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="9515f-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="9515f-112">W **GettingStartedLib**otwórz plik **Service1.cs** lub **Service1. vb** i Zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9515f-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="9515f-113">Edytuj plik App. config</span><span class="sxs-lookup"><span data-stu-id="9515f-113">Edit App.config</span></span>

<span data-ttu-id="9515f-114">Edytuj **plik App. config** w programie **GettingStartedLib** , aby odzwierciedlić zmiany wprowadzone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9515f-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="9515f-115">Dla projektów C# wizualnych:</span><span class="sxs-lookup"><span data-stu-id="9515f-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="9515f-116">Zmień wiersz 14 na`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="9515f-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="9515f-117">Zmień wiersz 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="9515f-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="9515f-118">Zmień wiersz 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="9515f-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="9515f-119">Projekty Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9515f-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="9515f-120">Zmień wiersz 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="9515f-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="9515f-121">Zmień wiersz 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="9515f-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="9515f-122">Zmień wiersz 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="9515f-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="9515f-123">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="9515f-123">Compile the code</span></span>

<span data-ttu-id="9515f-124">Skompiluj rozwiązanie, aby upewnić się, że nie występują żadne błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9515f-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="9515f-125">Jeśli używasz programu Visual Studio, w menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie** (lub naciśnij **klawisze CTRL**+**SHIFT**+**B**).</span><span class="sxs-lookup"><span data-stu-id="9515f-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9515f-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9515f-126">Next steps</span></span>

<span data-ttu-id="9515f-127">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9515f-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="9515f-128">Dodaj kod, aby zaimplementować kontrakt usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="9515f-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="9515f-129">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="9515f-129">Build the solution.</span></span>

<span data-ttu-id="9515f-130">Przejdź do następnego samouczka, aby dowiedzieć się, jak uruchomić usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="9515f-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9515f-131">Samouczek: Hostowanie i uruchamianie podstawowej usługi WCF</span><span class="sxs-lookup"><span data-stu-id="9515f-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
