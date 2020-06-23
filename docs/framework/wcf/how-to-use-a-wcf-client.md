---
title: 'Samouczek: korzystanie z klienta Windows Communication Foundation'
description: Dowiedz się, jak utworzyć wystąpienie klienta, skompilować aplikację i komunikować się z usługą w ramach serii artykułów dotyczących tworzenia aplikacji WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c94d5f8af679580c4194aaaadeda759098953d2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244338"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="3ccaa-103">Samouczek: korzystanie z klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3ccaa-103">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="3ccaa-104">W tym samouczku opisano ostatnie pięć zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ccaa-104">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="3ccaa-105">Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="3ccaa-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="3ccaa-106">Po utworzeniu i skonfigurowaniu serwera proxy programu Windows Communication Foundation (WCF) można utworzyć wystąpienie klienta i skompilować aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-106">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="3ccaa-107">Następnie użyjesz go do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-107">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="3ccaa-108">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="3ccaa-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="3ccaa-109">Dodaj kod, aby użyć klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-109">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="3ccaa-110">Przetestuj klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-110">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="3ccaa-111">Dodawanie kodu do korzystania z klienta WCF</span><span class="sxs-lookup"><span data-stu-id="3ccaa-111">Add code to use the WCF client</span></span>

<span data-ttu-id="3ccaa-112">Kod klienta wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="3ccaa-112">The client code does the following steps:</span></span>

- <span data-ttu-id="3ccaa-113">Tworzy wystąpienie klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-113">Instantiates the WCF client.</span></span>
- <span data-ttu-id="3ccaa-114">Wywołuje operacje usługi z wygenerowanego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-114">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="3ccaa-115">Zamyka klienta po zakończeniu wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-115">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="3ccaa-116">Otwórz plik **program.cs** lub **Module1. vb** z projektu **GettingStartedClient** i Zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="3ccaa-116">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

<span data-ttu-id="3ccaa-117">Zwróć uwagę na `using` instrukcję (for Visual C#) lub `Imports` (for Visual Basic), która importuje `GettingStartedClient.ServiceReference1` .</span><span class="sxs-lookup"><span data-stu-id="3ccaa-117">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="3ccaa-118">Ta instrukcja importuje kod, który program Visual Studio wygenerował z funkcją **Dodaj odwołanie do usługi** .</span><span class="sxs-lookup"><span data-stu-id="3ccaa-118">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="3ccaa-119">Kod tworzy wystąpienie serwera proxy programu WCF i wywołuje każdą operację usługi, którą uwidacznia usługa Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-119">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="3ccaa-120">Następnie zamknie serwer proxy i zakończy działanie programu.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-120">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="3ccaa-121">Testowanie klienta WCF</span><span class="sxs-lookup"><span data-stu-id="3ccaa-121">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="3ccaa-122">Testowanie aplikacji z programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3ccaa-122">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="3ccaa-123">Zapisz i skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-123">Save and build the solution.</span></span>

2. <span data-ttu-id="3ccaa-124">Wybierz folder **GettingStartedLib** , a następnie wybierz pozycję **Ustaw jako projekt startowy** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-124">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="3ccaa-125">Z **projektów uruchamiania**wybierz pozycję **GettingStartedLib** z listy rozwijanej, a następnie wybierz pozycję **Uruchom** lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-125">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="3ccaa-126">Testowanie aplikacji z poziomu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="3ccaa-126">Test the application from a command prompt</span></span>

1. <span data-ttu-id="3ccaa-127">Otwórz wiersz polecenia jako administrator, a następnie przejdź do katalogu rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-127">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="3ccaa-128">Aby uruchomić usługę: wprowadź *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-128">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="3ccaa-129">Aby uruchomić klienta: Otwórz inny wiersz polecenia, przejdź do katalogu rozwiązania programu Visual Studio, a następnie wprowadź *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-129">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="3ccaa-130">*GettingStartedHost.exe* generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3ccaa-130">*GettingStartedHost.exe* produces the following output:</span></span>

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   <span data-ttu-id="3ccaa-131">*GettingStartedClient.exe* generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3ccaa-131">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="3ccaa-132">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3ccaa-132">Next steps</span></span>

<span data-ttu-id="3ccaa-133">Wszystkie zadania zostały wykonane w samouczku wprowadzenie do usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-133">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="3ccaa-134">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="3ccaa-134">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="3ccaa-135">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="3ccaa-135">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="3ccaa-136">Dodaj kod, aby użyć klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-136">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="3ccaa-137">Przetestuj klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-137">Test the WCF client.</span></span>

<span data-ttu-id="3ccaa-138">Jeśli masz problemy lub błędy w którymkolwiek z kroków, wykonaj kroki opisane w artykule dotyczącym rozwiązywania problemów, aby je rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="3ccaa-138">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3ccaa-139">Rozwiązywanie problemów z samouczkami wprowadzenie do usługi WCF</span><span class="sxs-lookup"><span data-stu-id="3ccaa-139">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
