---
title: 'Samouczek: Definiowanie umowy serwisowej programu Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184094"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Samouczek: Definiowanie umowy serwisowej programu Windows Communication Foundation

W tym samouczku opisano pierwsze z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).

Podczas tworzenia usługi WCF, pierwszym zadaniem jest zdefiniowanie umowy serwisowej. Umowa serwisowa określa, jakie operacje obsługuje usługa. Operację można traktować jako metodę usługi sieci Web. Umowy serwisowe można utworzyć, definiując interfejs języka C# lub Visual Basic. Interfejs ma następujące cechy:

- Każda metoda w interfejsie odpowiada określonej operacji usługi.
- Dla każdego interfejsu należy <xref:System.ServiceModel.ServiceContractAttribute> zastosować atrybut.
- Dla każdej operacji/metody należy <xref:System.ServiceModel.OperationContractAttribute> zastosować atrybut.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Utwórz projekt **biblioteki usług WCF.**
> - Zdefiniuj interfejs umowy serwisowej.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Tworzenie projektu biblioteki usług WCF i definiowanie interfejsu umowy serwisowej

1. Otwórz program Visual Studio jako administrator. Aby to zrobić, wybierz program Visual Studio w menu **Start,** a następnie wybierz polecenie **Więcej** > **uruchom jako administrator** z menu skrótów.

2. Utwórz projekt **biblioteki usług WCF.**

   1. Z menu **Plik** wybierz polecenie **Nowy** > **projekt**.

   2. W oknie dialogowym **Nowy projekt** po lewej stronie rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie wybierz kategorię **WCF.** Visual Studio wyświetla listę szablonów projektów w środkowej sekcji okna. Wybierz **bibliotekę usług WCF**.

      > [!NOTE]
      > Jeśli nie widzisz kategorii szablonu projektu **WCF,** może być konieczne zainstalowanie składnika **Programu Windows Communication Foundation** programu Visual Studio. W oknie dialogowym **Nowy projekt** wybierz łącze **Otwórz instalatora programu Visual Studio** po lewej stronie. Wybierz kartę **Poszczególne składniki,** a następnie znajdź i wybierz **pozycję Windows Communication Foundation** w kategorii Działania **deweloperów.** Wybierz **pozycję Modyfikuj,** aby rozpocząć instalację składnika.

   3. W dolnej części okna wprowadź *WprowadzenieStartedLib* dla **nazwy** i *GettingStarted* dla **nazwy rozwiązania**.

   4. Kliknij przycisk **OK**.

      Visual Studio tworzy projekt, który ma trzy pliki: *IService1.cs* (lub *IService1.vb* dla projektu języka Visual Basic), *Service1.cs* (lub *Service1.vb* dla projektu Visual Basic) i *App.config*. Program Visual Studio definiuje te pliki w następujący sposób:
      - Plik *IService1* zawiera domyślną definicję umowy serwisowej.
      - Plik *Service1* zawiera domyślną implementację umowy serwisowej.
      - Plik *App.config* zawiera informacje o konfiguracji potrzebne do załadowania domyślnej usługi za pomocą narzędzia Host usługi WCF programu Visual Studio. Aby uzyskać więcej informacji na temat narzędzia Host usług WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Jeśli program Visual Studio został zainstalowany z ustawieniami środowiska dewelopera języka Visual Basic, rozwiązanie może być ukryte. W takim przypadku wybierz **opcję Opcje** z menu **Narzędzia,** a następnie w oknie **Opcje** wybierz pozycję Projekty **i rozwiązania** > **ogólne.** Wybierz **opcję Zawsze pokazuj rozwiązanie**. Sprawdź też, czy **opcja Zapisz nowe projekty po utworzeniu** jest zaznaczona.

3. W **Eksploratorze rozwiązań**otwórz **plik IService1.cs** lub **IService1.vb** i zastąp jego kod następującym kodem:

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     Niniejsza umowa definiuje kalkulator online. Zwróć `ICalculator` uwagę, że <xref:System.ServiceModel.ServiceContractAttribute> interfejs jest oznaczony `ServiceContract`atrybutem (uproszczonym jako ). Ten atrybut definiuje obszar nazw, aby odróżnić nazwę kontraktu. Kod oznacza każdą operację kalkulatora atrybutem <xref:System.ServiceModel.OperationContractAttribute> (uproszczonym jako `OperationContract`).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Utwórz projekt biblioteki usług WCF.
> - Zdefiniuj interfejs umowy serwisowej.

Przejdź do następnego samouczka, aby dowiedzieć się, jak zaimplementować umowę serwisową WCF.

> [!div class="nextstepaction"]
> [Samouczek: Zaimplementowanie umowy serwisowej WCF](how-to-implement-a-wcf-contract.md)
