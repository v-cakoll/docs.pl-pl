---
title: 'Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fa8c5457c636d7f37215f0d4b4fdbb1c96c9481e
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463621"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="e76d3-102">Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e76d3-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="e76d3-103">W tym samouczku opisano drugi pięć zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e76d3-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="e76d3-104">Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="e76d3-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="e76d3-105">Następnym krokiem do tworzenia aplikacji WCF jest Dodaj kod do implementacji interfejsu usługi WCF, który został utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="e76d3-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="e76d3-106">W tym kroku opisano tworzenie klasę o nazwie `CalculatorService` implementującej zdefiniowany przez użytkownika `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e76d3-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="e76d3-107">Każda metoda w poniższym kodzie wywołuje działania kalkulatora i zapisuje tekst w konsoli, aby ją przetestować.</span><span class="sxs-lookup"><span data-stu-id="e76d3-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="e76d3-108">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e76d3-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="e76d3-109">Dodaj kod implementacji kontraktu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e76d3-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="e76d3-110">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e76d3-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="e76d3-111">Dodaj kod implementacji kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="e76d3-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="e76d3-112">W **GettingStartedLib**, otwórz **Service1.cs** lub **Service1.vb** i zastąp jego kod poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="e76d3-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="e76d3-113">Edytowanie pliku App.config</span><span class="sxs-lookup"><span data-stu-id="e76d3-113">Edit App.config</span></span>

<span data-ttu-id="e76d3-114">Edytuj **App.config** w **GettingStartedLib** aby odzwierciedlić zmiany wprowadzone do kodu.</span><span class="sxs-lookup"><span data-stu-id="e76d3-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>
- <span data-ttu-id="e76d3-115">Dla elementu wizualnego C# projektów:</span><span class="sxs-lookup"><span data-stu-id="e76d3-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="e76d3-116">Zmień wiersz 14 `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="e76d3-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="e76d3-117">Zmień wiersz 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="e76d3-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="e76d3-118">Zmień wiersz 22 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="e76d3-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="e76d3-119">Dla projektów języka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="e76d3-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="e76d3-120">Zmień wiersz 14 `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="e76d3-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="e76d3-121">Zmień wiersz 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="e76d3-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="e76d3-122">Zmień wiersz 22 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="e76d3-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="e76d3-123">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="e76d3-123">Compile the code</span></span>

<span data-ttu-id="e76d3-124">Kompiluj rozwiązanie, aby sprawdzić, czy nie ma żadnych błędów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e76d3-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="e76d3-125">Jeśli używasz programu Visual Studio na **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie** (lub naciśnij **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="e76d3-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e76d3-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e76d3-126">Next steps</span></span>

<span data-ttu-id="e76d3-127">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e76d3-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="e76d3-128">Dodaj kod implementacji kontraktu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e76d3-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="e76d3-129">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e76d3-129">Build the solution.</span></span>

<span data-ttu-id="e76d3-130">Przejdź do następnego samouczka, aby dowiedzieć się, jak uruchomić usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e76d3-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e76d3-131">Samouczek: Hostowanie i uruchamianie podstawowej usługi WCF</span><span class="sxs-lookup"><span data-stu-id="e76d3-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
