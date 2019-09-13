---
title: 'Samouczek: Zdefiniuj kontrakt usługi Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: ba88fc6ba4cba8d46ed1b43080d471b1b7c4bd75
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928877"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Samouczek: Zdefiniuj kontrakt usługi Windows Communication Foundation

W tym samouczku opisano pierwsze pięć zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, [zobacz Samouczek: Rozpocznij pracę z aplikacjami](getting-started-tutorial.md)Windows Communication Foundation.

Podczas tworzenia usługi WCF pierwsze zadanie polega na zdefiniowaniu kontraktu usługi. Kontrakt usługi określa operacje obsługiwane przez usługę. Operację można traktować jako metodę usługi sieci Web. Kontrakty usługi można tworzyć przez zdefiniowanie C# interfejsu wizualizacji lub Visual Basic (VB). Interfejs ma następującą charakterystykę:

- Każda metoda w interfejsie odpowiada określonej operacji usługi. 
- Dla każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> atrybut.
- Dla każdej operacji/metody należy zastosować <xref:System.ServiceModel.OperationContractAttribute> atrybut. 

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Utwórz projekt **biblioteki usługi WCF** .
> - Zdefiniuj interfejs kontraktu usługi.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Utwórz projekt biblioteki usługi WCF i zdefiniuj interfejs kontraktu usługi

1. Otwórz program Visual Studio jako administrator. W tym celu wybierz program Visual Studio w menu **Start** , a następnie wybierz polecenie **więcej** > **Uruchom jako administrator** z menu skrótów.

2. Utwórz projekt **biblioteki usługi WCF** .

   1. Z **pliku** menu, wybierz opcję **New** > **projektu**.

   2. W oknie dialogowym **Nowy projekt** po lewej stronie rozwiń pozycję  **C# Wizualizacja** lub **Visual Basic**, a następnie wybierz kategorię **WCF** . Program Visual Studio Wyświetla listę szablonów projektu w środkowej sekcji okna. Wybierz pozycję **Biblioteka usług WCF**.

      > [!NOTE]
      > Jeśli nie widzisz kategorii szablonu projektu **WCF** , może być konieczne zainstalowanie składnika **Windows Communication Foundation** programu Visual Studio. W oknie dialogowym **Nowy projekt** wybierz łącze **Otwórz Instalator programu Visual Studio** po lewej stronie. Wybierz kartę **poszczególne składniki** , a następnie Znajdź i wybierz **Windows Communication Foundation** w kategorii **działania rozwojowe** . Wybierz pozycję **Modyfikuj** , aby rozpocząć instalowanie składnika.

   3. W dolnej części okna wprowadź *GettingStartedLib* dla **nazwy** i *GettingStarted* **nazwy rozwiązania**. 

   4. Kliknij przycisk **OK**.

      Program Visual Studio tworzy projekt, który ma trzy pliki: *IService1.cs* (lub *IService1. vb* dla projektu Visual Basic), *Service1.cs* (lub *Service1. vb* dla projektu Visual Basic) i *App. config*. Program Visual Studio definiuje te pliki w następujący sposób: 
      - Plik *IService1* zawiera definicję domyślną kontraktu usługi. 
      - Plik *Service1* zawiera domyślną implementację kontraktu usługi. 
      - Plik *App. config* zawiera informacje o konfiguracji, które są konieczne do załadowania usługi domyślnej za pomocą narzędzia hosta usługi WCF programu Visual Studio. Aby uzyskać więcej informacji na temat narzędzia hosta usługi WCF, zobacz [host usługi WCF (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Jeśli zainstalowano program Visual Studio z Visual Basic ustawieniach środowiska deweloperskiego, rozwiązanie może być ukryte. W takim przypadku wybierz pozycję **Opcje** z menu **Narzędzia** , a następnie wybierz pozycję **projekty i rozwiązania** > **Ogólne** w oknie **Opcje** . Wybierz pozycję **Zawsze pokazuj rozwiązanie**. Sprawdź również, czy wybrano opcję **Zapisz nowe projekty po utworzeniu** .

3. W **Eksplorator rozwiązań**otwórz plik **IService1.cs** lub **IService1. vb** i Zastąp jego kod następującym kodem:

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

     Ten kontrakt definiuje Kalkulator online. Zauważ, `ICalculator` że interfejs jest oznaczony <xref:System.ServiceModel.ServiceContractAttribute> atrybutem (uproszczony `ServiceContract`jako). Ten atrybut definiuje przestrzeń nazw, aby odróżnić nazwę kontraktu. Kod oznacza każdą operację kalkulatora z <xref:System.ServiceModel.OperationContractAttribute> atrybutem (uproszczony jako `OperationContract`).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Utwórz projekt biblioteki usługi WCF.
> - Zdefiniuj interfejs kontraktu usługi.

Przejdź do następnego samouczka, aby dowiedzieć się, jak zaimplementować kontrakt usługi WCF.

> [!div class="nextstepaction"]
> [Samouczek: Implementowanie kontraktu usługi WCF](how-to-implement-a-wcf-contract.md)
