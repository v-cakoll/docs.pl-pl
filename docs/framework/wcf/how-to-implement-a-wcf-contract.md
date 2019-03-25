---
title: 'Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fcf96af11bae701585acd92001c8000125858449
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410085"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation

W tym samouczku opisano drugi pięć zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).

Następnym krokiem do tworzenia aplikacji WCF jest Dodaj kod do implementacji interfejsu usługi WCF, który został utworzony w poprzednim kroku. W tym kroku opisano tworzenie klasę o nazwie `CalculatorService` implementującej zdefiniowany przez użytkownika `ICalculator` interfejsu. Każda metoda w poniższym kodzie wywołuje działania kalkulatora i zapisuje tekst w konsoli, aby ją przetestować. 

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Dodaj kod implementacji kontraktu usługi WCF.
> - Skompiluj rozwiązanie.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Dodaj kod implementacji kontraktu usługi WCF

W **GettingStartedLib**, otwórz **Service1.cs** lub **Service1.vb** i zastąp jego kod poniższym kodem:

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

## <a name="edit-appconfig"></a>Edytowanie pliku App.config

Edytuj **App.config** w **GettingStartedLib** aby odzwierciedlić zmiany wprowadzone do kodu.
   - Dla elementu wizualnego C# projektów:
       - Zmień wiersz 14 `<service name="GettingStartedLib.CalculatorService">`
       - Zmień wiersz 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
       - Zmień wiersz 22 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

   - Dla projektów języka Visual Basic:
       - Zmień wiersz 14 `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
       - Zmień wiersz 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
       - Zmień wiersz 22 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`


## <a name="compile-the-code"></a>Skompilować kod

Kompiluj rozwiązanie, aby sprawdzić, czy nie ma żadnych błędów kompilacji. Jeśli używasz programu Visual Studio na **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie** (lub naciśnij **Ctrl**+**Shift** + **B**).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Dodaj kod implementacji kontraktu usługi WCF.
> - Skompiluj rozwiązanie.

Przejdź do następnego samouczka, aby dowiedzieć się, jak uruchomić usługi WCF.

> [!div class="nextstepaction"]
> [Samouczek: Hostowanie i uruchamianie podstawowej usługi WCF](how-to-host-and-run-a-basic-wcf-service.md)
