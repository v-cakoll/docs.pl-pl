---
title: 'Samouczek: Używanie klienta programu Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: fa9aa3612a8dc72623fc4ea4b1ea337ac773fa26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169978"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Samouczek: Używanie klienta programu Windows Communication Foundation

W tym samouczku opisano ostatnich pięciu zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).

Po utworzeniu i skonfigurować serwer proxy usług Windows Communication Foundation (WCF), Utwórz wystąpienie klienta i kompilowania aplikacji klienckiej. Możesz następnie użyć go do komunikacji z usługą WCF. 

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Dodaj kod, aby używać klienta platformy WCF.
> - Testowanie klienta platformy WCF.

## <a name="add-code-to-use-the-wcf-client"></a>Dodaj kod, aby za pomocą klienta WCF

Kod klienta wykonuje następujące czynności:
- Tworzy wystąpienie klienta platformy WCF.
- Wywołania operacji usługi z wygenerowany serwer proxy.
- Zamyka klienta po zakończeniu wywołania operacji.

Otwórz **Program.cs** lub **Module1.vb** plik wchodzącej w skład **GettingStartedClient** projektu i zastąp jego kod poniższym kodem:

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
Imports System
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

Zwróć uwagę `using` (wizualizacji C#) lub `Imports` (dla języka Visual Basic) instrukcja, która importuje `GettingStartedClient.ServiceReference1`. Ta instrukcja imports kodu wygenerowanego przez Visual Studio za pomocą **Dodaj odwołanie do usługi** funkcji. Ten kod tworzy serwer proxy usługi WCF i wywołuje każdą z operacji usługi, które uwidacznia usługa kalkulatora. Następnie zamyka serwera proxy i zamknięcie programu.

## <a name="test-the-wcf-client"></a>Testowanie klienta WCF

### <a name="test-the-application-from-visual-studio"></a>Testowanie aplikacji z programu Visual Studio

1. Zapisz i Kompiluj rozwiązanie.

2. Wybierz **GettingStartedLib** folder, a następnie wybierz **Ustaw jako projekt startowy** z menu skrótów.

3. Z **projektów startowych**, wybierz opcję **GettingStartedLib** z listy rozwijanej wybierz **Uruchom** lub naciśnij **F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Testowanie aplikacji z poziomu wiersza polecenia

1. Otwórz wiersz polecenia jako administrator, a następnie przejdź do katalogu rozwiązania programu Visual Studio. 

2. Aby uruchomić usługę: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.

3. Aby uruchomić klienta: Otwórz wiersz polecenia z innego, przejdź do katalogu rozwiązania programu Visual Studio, a następnie wprowadź *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.

   *GettingStartedHost.exe* generuje następujące wyniki:

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

   *GettingStartedClient.exe* generuje następujące wyniki:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Następne kroki

Już teraz wykonane zadania z usługi WCF samouczek z wprowadzeniem. W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Dodaj kod, aby używać klienta platformy WCF.
> - Testowanie klienta platformy WCF.

Jeśli masz problemy lub błędy w jednym z kroków, wykonaj kroki w artykule rozwiązywania problemów, aby to naprawić.

> [!div class="nextstepaction"]
> [Rozwiązywanie problemów z Get pracę z samouczków usługi WCF](troubleshooting-the-getting-started-tutorial.md)
