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
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Samouczek: Korzystanie z klienta programu Windows Communication Foundation

W tym samouczku opisano ostatnie z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).

Po utworzeniu i skonfigurowaniu serwera proxy Windows Communication Foundation (WCF) należy utworzyć wystąpienie klienta i skompilować aplikację kliencką. Następnie można go używać do komunikowania się z usługą WCF.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Dodaj kod, aby użyć klienta WCF.
> - Przetestuj klienta WCF.

## <a name="add-code-to-use-the-wcf-client"></a>Dodaj kod, aby użyć klienta WCF

Kod klienta wykonuje następujące kroki:

- Wystąpienia klienta WCF.
- Wywołuje operacje usługi z wygenerowanego serwera proxy.
- Zamyka klienta po zakończeniu wywołania operacji.

Otwórz plik **Program.cs** lub **Module1.vb** z projektu **GettingStartedClient** i zastąp jego kod następującym kodem:

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

Zwróć `using` uwagę na (dla `Imports` języka Visual C#) lub `GettingStartedClient.ServiceReference1`(dla języka Visual Basic) instrukcję importowania . Ta instrukcja importuje kod wygenerowany przez program Visual Studio za pomocą funkcji **Dodaj odwołanie do usługi.** Kod wywołuje serwer proxy WCF i wywołuje każdą z operacji usługi, które udostępnia usługa kalkulatora. Następnie zamyka serwer proxy i kończy program.

## <a name="test-the-wcf-client"></a>Testowanie klienta WCF

### <a name="test-the-application-from-visual-studio"></a>Testowanie aplikacji z programu Visual Studio

1. Zapisz i skompiluj rozwiązanie.

2. Wybierz folder **GettingStartedLib,** a następnie z menu skrótów wybierz polecenie **Ustaw jako projekt startowy.**

3. W **obszarze Projekty startowe**wybierz pozycję **GettingStartedLib** z listy rozwijanej, a następnie wybierz pozycję **Uruchom** lub naciśnij **klawisz F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Testowanie aplikacji z wiersza polecenia

1. Otwórz wiersz polecenia jako administrator, a następnie przejdź do katalogu rozwiązania programu Visual Studio.

2. Aby uruchomić usługę: wprowadź *plik GettingStartedHost\bin\Debug\GettingStartedHost.exe*.

3. Aby uruchomić klienta: Otwórz inny wiersz polecenia, przejdź do katalogu rozwiązania programu Visual Studio, a następnie wprowadź *plik GettingStartedClient\bin\Debug\GettingStartedClient.exe*.

   *Program GettingStartedHost.exe* daje następujące dane wyjściowe:

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

   *Program GettingStartedClient.exe* daje następujące dane wyjściowe:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Następne kroki

Teraz ukończono wszystkie zadania w samouczku WCF wprowadzenie. W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Dodaj kod, aby użyć klienta WCF.
> - Przetestuj klienta WCF.

Jeśli masz problemy lub błędy w dowolnym z kroków, wykonaj kroki opisane w artykule rozwiązywania problemów, aby je naprawić.

> [!div class="nextstepaction"]
> [Rozwiązywanie problemów z samouczkami Wprowadzenie do WCF](troubleshooting-the-getting-started-tutorial.md)
