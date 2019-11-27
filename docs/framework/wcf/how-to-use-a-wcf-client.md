---
title: 'Samouczek: korzystanie z klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: d0ef525db16b2b2cedeea5fa03376fb4f3489a4a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346769"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Samouczek: korzystanie z klienta Windows Communication Foundation

W tym samouczku opisano ostatnie pięć zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).

Po utworzeniu i skonfigurowaniu serwera proxy programu Windows Communication Foundation (WCF) można utworzyć wystąpienie klienta i skompilować aplikację kliencką. Następnie użyjesz go do komunikowania się z usługą WCF. 

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Dodaj kod, aby użyć klienta WCF.
> - Przetestuj klienta WCF.

## <a name="add-code-to-use-the-wcf-client"></a>Dodawanie kodu do korzystania z klienta WCF

Kod klienta wykonuje następujące czynności:

- Tworzy wystąpienie klienta WCF.
- Wywołuje operacje usługi z wygenerowanego serwera proxy.
- Zamyka klienta po zakończeniu wywołania operacji.

Otwórz plik **program.cs** lub **Module1. vb** z projektu **GettingStartedClient** i Zastąp jego kod następującym kodem:

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

Zwróć uwagę na instrukcję `using` ( C#dla wizualizacji) lub `Imports` (for Visual Basic), która importuje `GettingStartedClient.ServiceReference1`. Ta instrukcja importuje kod, który program Visual Studio wygenerował z funkcją **Dodaj odwołanie do usługi** . Kod tworzy wystąpienie serwera proxy programu WCF i wywołuje każdą operację usługi, którą uwidacznia usługa Kalkulator. Następnie zamknie serwer proxy i zakończy działanie programu.

## <a name="test-the-wcf-client"></a>Testowanie klienta WCF

### <a name="test-the-application-from-visual-studio"></a>Testowanie aplikacji z programu Visual Studio

1. Zapisz i skompiluj rozwiązanie.

2. Wybierz folder **GettingStartedLib** , a następnie wybierz pozycję **Ustaw jako projekt startowy** z menu skrótów.

3. Z **projektów uruchamiania**wybierz pozycję **GettingStartedLib** z listy rozwijanej, a następnie wybierz pozycję **Uruchom** lub naciśnij klawisz **F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Testowanie aplikacji z poziomu wiersza polecenia

1. Otwórz wiersz polecenia jako administrator, a następnie przejdź do katalogu rozwiązania programu Visual Studio. 

2. Aby uruchomić usługę: wprowadź *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.

3. Aby uruchomić klienta: Otwórz inny wiersz polecenia, przejdź do katalogu rozwiązania programu Visual Studio, a następnie wprowadź *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.

   *GettingStartedHost. exe* generuje następujące dane wyjściowe:

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

   *GettingStartedClient. exe* generuje następujące dane wyjściowe:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Kolejne kroki

Wszystkie zadania zostały wykonane w samouczku wprowadzenie do usługi WCF. W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Dodaj kod, aby użyć klienta WCF.
> - Przetestuj klienta WCF.

Jeśli masz problemy lub błędy w którymkolwiek z kroków, wykonaj kroki opisane w artykule dotyczącym rozwiązywania problemów, aby je rozwiązać.

> [!div class="nextstepaction"]
> [Rozwiązywanie problemów z samouczkami wprowadzenie do usługi WCF](troubleshooting-the-getting-started-tutorial.md)
