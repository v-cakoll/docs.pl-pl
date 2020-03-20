---
title: 'Samouczek: Korzystanie z klienta programu Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: d2357c134aef8da204dcdb19d6c1fc93cfdc068c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184014"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="1f355-102">Samouczek: Korzystanie z klienta programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1f355-102">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="1f355-103">W tym samouczku opisano ostatnie z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1f355-103">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="1f355-104">Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1f355-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="1f355-105">Po utworzeniu i skonfigurowaniu serwera proxy Windows Communication Foundation (WCF) należy utworzyć wystąpienie klienta i skompilować aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="1f355-105">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="1f355-106">Następnie można go używać do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="1f355-106">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="1f355-107">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1f355-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1f355-108">Dodaj kod, aby użyć klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1f355-108">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="1f355-109">Przetestuj klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1f355-109">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="1f355-110">Dodaj kod, aby użyć klienta WCF</span><span class="sxs-lookup"><span data-stu-id="1f355-110">Add code to use the WCF client</span></span>

<span data-ttu-id="1f355-111">Kod klienta wykonuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1f355-111">The client code does the following steps:</span></span>

- <span data-ttu-id="1f355-112">Wystąpienia klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1f355-112">Instantiates the WCF client.</span></span>
- <span data-ttu-id="1f355-113">Wywołuje operacje usługi z wygenerowanego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="1f355-113">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="1f355-114">Zamyka klienta po zakończeniu wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="1f355-114">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="1f355-115">Otwórz plik **Program.cs** lub **Module1.vb** z projektu **GettingStartedClient** i zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="1f355-115">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

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

<span data-ttu-id="1f355-116">Zwróć `using` uwagę na (dla `Imports` języka Visual C#) lub `GettingStartedClient.ServiceReference1`(dla języka Visual Basic) instrukcję importowania .</span><span class="sxs-lookup"><span data-stu-id="1f355-116">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="1f355-117">Ta instrukcja importuje kod wygenerowany przez program Visual Studio za pomocą funkcji **Dodaj odwołanie do usługi.**</span><span class="sxs-lookup"><span data-stu-id="1f355-117">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="1f355-118">Kod wywołuje serwer proxy WCF i wywołuje każdą z operacji usługi, które udostępnia usługa kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="1f355-118">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="1f355-119">Następnie zamyka serwer proxy i kończy program.</span><span class="sxs-lookup"><span data-stu-id="1f355-119">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="1f355-120">Testowanie klienta WCF</span><span class="sxs-lookup"><span data-stu-id="1f355-120">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="1f355-121">Testowanie aplikacji z programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1f355-121">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="1f355-122">Zapisz i skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="1f355-122">Save and build the solution.</span></span>

2. <span data-ttu-id="1f355-123">Wybierz folder **GettingStartedLib,** a następnie z menu skrótów wybierz polecenie **Ustaw jako projekt startowy.**</span><span class="sxs-lookup"><span data-stu-id="1f355-123">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="1f355-124">W **obszarze Projekty startowe**wybierz pozycję **GettingStartedLib** z listy rozwijanej, a następnie wybierz pozycję **Uruchom** lub naciśnij **klawisz F5**.</span><span class="sxs-lookup"><span data-stu-id="1f355-124">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="1f355-125">Testowanie aplikacji z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="1f355-125">Test the application from a command prompt</span></span>

1. <span data-ttu-id="1f355-126">Otwórz wiersz polecenia jako administrator, a następnie przejdź do katalogu rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f355-126">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="1f355-127">Aby uruchomić usługę: wprowadź *plik GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span><span class="sxs-lookup"><span data-stu-id="1f355-127">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="1f355-128">Aby uruchomić klienta: Otwórz inny wiersz polecenia, przejdź do katalogu rozwiązania programu Visual Studio, a następnie wprowadź *plik GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="1f355-128">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="1f355-129">*Program GettingStartedHost.exe* daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1f355-129">*GettingStartedHost.exe* produces the following output:</span></span>

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

   <span data-ttu-id="1f355-130">*Program GettingStartedClient.exe* daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1f355-130">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="1f355-131">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1f355-131">Next steps</span></span>

<span data-ttu-id="1f355-132">Teraz ukończono wszystkie zadania w samouczku WCF wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="1f355-132">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="1f355-133">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1f355-133">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="1f355-134">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1f355-134">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1f355-135">Dodaj kod, aby użyć klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1f355-135">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="1f355-136">Przetestuj klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1f355-136">Test the WCF client.</span></span>

<span data-ttu-id="1f355-137">Jeśli masz problemy lub błędy w dowolnym z kroków, wykonaj kroki opisane w artykule rozwiązywania problemów, aby je naprawić.</span><span class="sxs-lookup"><span data-stu-id="1f355-137">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1f355-138">Rozwiązywanie problemów z samouczkami Wprowadzenie do WCF</span><span class="sxs-lookup"><span data-stu-id="1f355-138">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
