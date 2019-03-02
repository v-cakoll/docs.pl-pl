---
title: 'Instrukcje: Używanie klienta programu Windows Communication Foundation'
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 780a51e3e0f61f292c997202614e43a85dd90820
ms.sourcegitcommit: a532e8314c3a4b5b039656567fedff9787a31957
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57250926"
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>Instrukcje: Używanie klienta programu Windows Communication Foundation

Jest to ostatnich sześciu zadań podrzędnych, wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.

Po utworzeniu i skonfigurowaniu serwera proxy usług Windows Communication Foundation (WCF) można utworzyć wystąpienia klienta, a aplikacja kliencka może zostanie skompilowany i używany do komunikacji z usługą WCF. W tym temacie opisano procedury tworzenia wystąpienia i przy użyciu klienta programu WCF. Ta procedura wykonuje trzy rzeczy:

1.  Tworzy wystąpienie klienta programu WCF.

2.  Wywołania operacji usługi z wygenerowany serwer proxy.

3.  Zamyka klienta po zakończeniu wywołania operacji.

## <a name="use-a-windows-communication-foundation-client"></a>Używanie klienta programu Windows Communication Foundation

Otwórz plik Program.cs lub Program.vb z projektu GettingStartedClient i Zastąp istniejący kod następującym kodem:

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

            //Step 3: Closing the client gracefully closes the connection and cleans up resources.
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
Imports GettingStartedClientVB2.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy
        Dim Client As New CalculatorClient()

        'Step 2: Call the service operations.
        'Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        'Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        'Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        'Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Closing the client gracefully closes the connection and cleans up resources.
        Client.Close()

        Console.WriteLine()
        Console.WriteLine("Press <ENTER> to terminate client.")
        Console.ReadLine()

    End Sub

End Module
```

Zwróć uwagę `using` lub `Imports` instrukcję, która importuje `GettingStartedClient.ServiceReference1`. Importuje to kod wygenerowany przez **Dodaj odwołanie do usługi** w programie Visual Studio. Kod tworzy serwer proxy usługi WCF i następnie wywołuje każdą z operacji usługi udostępniane przez usługę Kalkulator, zamyka serwera proxy i kończy.

Ukończono samouczek. Definicja kontraktu usługi, zaimplementować kontrakt usługi, wygenerowany serwer proxy usługi WCF, skonfigurować aplikację klienta WCF i następnie używany serwer proxy do wywołania operacji usługi. Do przetestowania aplikacji, należy najpierw uruchomić GettingStartedHost, aby uruchomić usługę, a następnie uruchom GettingStartedClient.

Dane wyjściowe z GettingStartedHost powinien wyglądać następująco:

```text
The service is ready.
Press <ENTER> to terminate service.

Received Add(100,15.99)
Return: 115.99
Received Subtract(145,76.54)
Return: 68.46
Received Multiply(9,81.25)
Return: 731.25
Received Divide(22,7)
Return: 3.14285714285714
```

Dane wyjściowe z GettingStartedClient powinien wyglądać następująco:

```text
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

## <a name="see-also"></a>Zobacz także

- [Kompilowanie klientów](../../../docs/framework/wcf/building-clients.md)
- [Instrukcje: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md)
- [Podstawy programowania przy użyciu programu WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Instrukcje: Tworzenie kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
