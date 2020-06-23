---
title: 'Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation'
description: Dowiedz się, jak dodać kod w celu zaimplementowania interfejsu usługi WCF w ramach serii artykułów, które ułatwiają rozpoczęcie tworzenia aplikacji WCF.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 89f97610cccd42c2a5d298baa667327d077fd472
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244650"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="13ebb-103">Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="13ebb-103">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="13ebb-104">W tym samouczku opisano dwa z pięciu zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="13ebb-104">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="13ebb-105">Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="13ebb-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="13ebb-106">Następnym krokiem tworzenia aplikacji WCF jest dodanie kodu w celu zaimplementowania interfejsu usługi WCF, który został utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="13ebb-106">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="13ebb-107">W tym kroku utworzysz klasę o nazwie `CalculatorService` implementującej interfejs zdefiniowany przez użytkownika `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="13ebb-107">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="13ebb-108">Każda metoda w poniższym kodzie wywołuje operację kalkulatora i zapisuje tekst w konsoli programu w celu jej przetestowania.</span><span class="sxs-lookup"><span data-stu-id="13ebb-108">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="13ebb-109">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="13ebb-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="13ebb-110">Dodaj kod, aby zaimplementować kontrakt usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="13ebb-110">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="13ebb-111">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="13ebb-111">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="13ebb-112">Dodawanie kodu w celu zaimplementowania kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="13ebb-112">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="13ebb-113">W **GettingStartedLib**otwórz plik **Service1.cs** lub **Service1. vb** i Zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="13ebb-113">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="13ebb-114">Edytuj App.config</span><span class="sxs-lookup"><span data-stu-id="13ebb-114">Edit App.config</span></span>

<span data-ttu-id="13ebb-115">Edytuj **App.config** w **GettingStartedLib** , aby odzwierciedlić zmiany wprowadzone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="13ebb-115">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="13ebb-116">W przypadku projektów Visual C#:</span><span class="sxs-lookup"><span data-stu-id="13ebb-116">For Visual C# projects:</span></span>
  - <span data-ttu-id="13ebb-117">Zmień wiersz 14 na`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="13ebb-117">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="13ebb-118">Zmień wiersz 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="13ebb-118">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="13ebb-119">Zmień wiersz 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="13ebb-119">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="13ebb-120">Projekty Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="13ebb-120">For Visual Basic projects:</span></span>
  - <span data-ttu-id="13ebb-121">Zmień wiersz 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="13ebb-121">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="13ebb-122">Zmień wiersz 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="13ebb-122">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="13ebb-123">Zmień wiersz 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="13ebb-123">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="13ebb-124">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="13ebb-124">Compile the code</span></span>

<span data-ttu-id="13ebb-125">Skompiluj rozwiązanie, aby upewnić się, że nie występują żadne błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13ebb-125">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="13ebb-126">Jeśli używasz programu Visual Studio, w menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie** (lub naciśnij **klawisze CTRL** + **SHIFT** + **B**).</span><span class="sxs-lookup"><span data-stu-id="13ebb-126">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="13ebb-127">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="13ebb-127">Next steps</span></span>

<span data-ttu-id="13ebb-128">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="13ebb-128">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="13ebb-129">Dodaj kod, aby zaimplementować kontrakt usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="13ebb-129">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="13ebb-130">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="13ebb-130">Build the solution.</span></span>

<span data-ttu-id="13ebb-131">Przejdź do następnego samouczka, aby dowiedzieć się, jak uruchomić usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="13ebb-131">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="13ebb-132">Samouczek: Hostowanie i uruchamianie podstawowej usługi WCF</span><span class="sxs-lookup"><span data-stu-id="13ebb-132">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
