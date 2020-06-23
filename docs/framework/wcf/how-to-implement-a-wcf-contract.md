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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Samouczek: Implementowanie kontraktu usługi Windows Communication Foundation

W tym samouczku opisano dwa z pięciu zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).

Następnym krokiem tworzenia aplikacji WCF jest dodanie kodu w celu zaimplementowania interfejsu usługi WCF, który został utworzony w poprzednim kroku. W tym kroku utworzysz klasę o nazwie `CalculatorService` implementującej interfejs zdefiniowany przez użytkownika `ICalculator` . Każda metoda w poniższym kodzie wywołuje operację kalkulatora i zapisuje tekst w konsoli programu w celu jej przetestowania.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
> [!div class="checklist"]
>
> - Dodaj kod, aby zaimplementować kontrakt usługi WCF.
> - Skompiluj rozwiązanie.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Dodawanie kodu w celu zaimplementowania kontraktu usługi WCF

W **GettingStartedLib**otwórz plik **Service1.cs** lub **Service1. vb** i Zastąp jego kod następującym kodem:

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

## <a name="edit-appconfig"></a>Edytuj App.config

Edytuj **App.config** w **GettingStartedLib** , aby odzwierciedlić zmiany wprowadzone w kodzie.

- W przypadku projektów Visual C#:
  - Zmień wiersz 14 na`<service name="GettingStartedLib.CalculatorService">`
  - Zmień wiersz 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Zmień wiersz 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Projekty Visual Basic:
  - Zmień wiersz 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Zmień wiersz 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Zmień wiersz 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Kompiluj kod

Skompiluj rozwiązanie, aby upewnić się, że nie występują żadne błędy kompilacji. Jeśli używasz programu Visual Studio, w menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie** (lub naciśnij **klawisze CTRL** + **SHIFT** + **B**).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Dodaj kod, aby zaimplementować kontrakt usługi WCF.
> - Skompiluj rozwiązanie.

Przejdź do następnego samouczka, aby dowiedzieć się, jak uruchomić usługę WCF.

> [!div class="nextstepaction"]
> [Samouczek: Hostowanie i uruchamianie podstawowej usługi WCF](how-to-host-and-run-a-basic-wcf-service.md)
