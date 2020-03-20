---
title: 'Samouczek: Zaimplementowanie umowy serwisowej programu Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184067"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Samouczek: Zaimplementowanie umowy serwisowej programu Windows Communication Foundation

W tym samouczku opisano drugie z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).

Następnym krokiem do tworzenia aplikacji WCF jest dodanie kodu do zaimplementowania interfejsu usługi WCF, który został utworzony w poprzednim kroku. W tym kroku należy utworzyć `CalculatorService` klasę o nazwie, `ICalculator` która implementuje interfejs zdefiniowany przez użytkownika. Każda metoda w poniższym kodzie wywołuje operację kalkulatora i zapisuje tekst w konsoli, aby ją przetestować.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Dodaj kod, aby zaimplementować kontrakt serwisowy WCF.
> - Skompiluj rozwiązanie.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Dodaj kod do zaimplementowania umowy serwisowej WCF

W **gettingstartedlib**otwórz plik **Service1.cs** lub **Service1.vb** i zastąp jego kod następującym kodem:

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

## <a name="edit-appconfig"></a>Edytuj plik App.config

Edytuj **app.config** w **GettingStartedLib,** aby odzwierciedlić zmiany wprowadzone w kodzie.

- W przypadku projektów visual c#:
  - Zmień linię 14 na`<service name="GettingStartedLib.CalculatorService">`
  - Zmień linię 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Zmień linię 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- W przypadku projektów visual basic:
  - Zmień linię 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Zmień linię 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Zmień linię 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Skompiluj kod

Skompiluj rozwiązanie, aby sprawdzić, czy nie ma żadnych błędów kompilacji. Jeśli używasz programu Visual Studio, w menu **Kompilacja** wybierz opcję **Kompilacja rozwiązania** (lub naciśnij klawisz **Ctrl**+**Shift**+**B**).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Dodaj kod, aby zaimplementować kontrakt serwisowy WCF.
> - Skompiluj rozwiązanie.

Przejdź do następnego samouczka, aby dowiedzieć się, jak uruchomić usługę WCF.

> [!div class="nextstepaction"]
> [Samouczek: Host i uruchom podstawową usługę WCF](how-to-host-and-run-a-basic-wcf-service.md)
