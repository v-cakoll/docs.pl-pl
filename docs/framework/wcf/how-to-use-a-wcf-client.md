---
title: 'Instrukcje: Używanie klienta programu Windows Communication Foundation'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 6667a8e9862054d7d8d5b20e70dfbe699de02eab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>Instrukcje: Używanie klienta programu Windows Communication Foundation
Jest to ostatnich sześciu zadania wymagane do tworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Omówienie sześciu wszystkich zadań, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.  
  
 Gdy utworzono i skonfigurowano serwer proxy usług Windows Communication Foundation (WCF), można utworzyć wystąpienia klienta i aplikacja kliencka można skompilować i używany do komunikacji z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. W tym temacie opisano procedury tworzenia wystąpienia i przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta. Procedura ta nie trzy czynności:  
  
1.  Tworzy wystąpienie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta.  
  
2.  Wywołania operacji usługi z wygenerowany serwer proxy.  
  
3.  Zamyka klienta po zakończeniu wywołania operacji.  
  
### <a name="to-use-a-windows-communication-foundation-client"></a>Aby użyć klienta Windows Communication Foundation  
  
1.  Otwórz plik Program.cs lub Program.vb z projektu GettingStartedClient i zastąpić istniejący kod następującym kodem:  
  
    ```  
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
  
    ```  
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
  
     Zwróć uwagę, instrukcji za pomocą lub Importy, który importuje GettingStartedClient.ServiceReference1. Kod wygenerowany przez Dodaj odwołanie do usługi w programie Visual Studio zostaną zaimportowane. Kod tworzy WCF proxy wywołuje każdą z operacji usługi udostępniane przez usługi Kalkulator, zamyka serwera proxy i kończy.  
  
 Ukończono samouczka. Możesz definicja kontraktu usługi, zaimplementowana kontraktu usługi wygenerowany serwer proxy usługi WCF, skonfigurować aplikację klienta WCF i następnie użyć serwera proxy do wywołania operacji usługi. Aby przetestować aplikację, najpierw uruchom GettingStartedHost, aby uruchomić usługę, a następnie uruchom GettingStartedClient. Dane wyjściowe z GettingStartedHost powinien wyglądać następująco:  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 Dane wyjściowe z GettingStartedClient powinien wyglądać następująco:  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie klientów](../../../docs/framework/wcf/building-clients.md)  
 [Instrukcje: tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Podstawy programowania przy użyciu programu WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
