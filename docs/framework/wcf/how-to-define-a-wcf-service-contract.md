---
title: 'Samouczek: Definiowanie kontraktu usługi Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228396"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Samouczek: Definiowanie kontraktu usługi Windows Communication Foundation

W tym samouczku opisano pierwszy pięć zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).

Podczas tworzenia usługi WCF, pierwsze zadanie jest definiowanie kontraktu usługi. Kontrakt usługi określa, jakie operacje obsługuje usługi. Operacja można traktować jako metoda usługi sieci Web. Tworzenie kontraktów usług, definiując wizualizacji C# lub interfejs Visual Basic (VB). Interfejs ma następującą charakterystykę:

- Każda metoda w interfejsie odpowiada określonej operacji usługi. 
- Dla każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.
- Dla każdej operacji/metody, należy najpierw zastosować <xref:System.ServiceModel.OperationContractAttribute> atrybutu. 

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Tworzenie **biblioteki usługi WCF** projektu.
> - Zdefiniuj interfejs kontraktu usługi.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Utwórz projekt biblioteki usługi WCF i definiowanie interfejsu kontraktu usługi

1. Otwórz program Visual Studio jako administrator. Aby to zrobić, wybierz program Visual Studio w **Start** menu, a następnie wybierz pozycję **więcej** > **Uruchom jako administrator** z menu skrótów.

2. Tworzenie **biblioteki usługi WCF** projektu.

   1. Z **pliku** menu, wybierz opcję **New** > **projektu**.

   2. W **nowy projekt** okna dialogowego po lewej stronie rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **WCF** kategorii. Visual Studio Wyświetla listy szablonów projektu w w górnej części okna. Wybierz **biblioteki usługi WCF**.

      > [!NOTE]
      > Jeśli nie widzisz **WCF** kategorii szablonu projektu, użytkownik może być konieczne zainstalowanie **Windows Communication Foundation** składnika programu Visual Studio. W **nowy projekt** okno dialogowe, wybierz opcję **Otwórz Instalator programu Visual Studio** link po lewej stronie. Wybierz **poszczególne składniki** kartę, a następnie znajdź i zaznacz **Windows Communication Foundation** w obszarze **działań programistycznych** kategorii. Wybierz **Modyfikuj** do rozpoczęcia instalacji tego składnika.

   3. W dolnej części okna wprowadź *GettingStartedLib* dla **nazwa** i *GettingStarted* dla **Nazwa rozwiązania**. 

   4. Kliknij przycisk **OK**.

      Program Visual Studio tworzy projekt, który ma trzy pliki: *IService1.cs* (lub *IService1.vb* dla projektów języka Visual Basic), *Service1.cs* (lub *Service1.vb* dla projektów języka Visual Basic), a  *App.config*. Program Visual Studio definiuje te pliki w następujący sposób: 
      - *IService1* plik zawiera definicję domyślną kontraktu usługi. 
      - *Service1* plik zawiera domyślną implementację elementu kontraktu usługi. 
      - *App.config* plik zawiera informacje o konfiguracji potrzebne do załadowania domyślnej usługi za pomocą narzędzia Host usługi WCF w usłudze Visual Studio. Aby uzyskać więcej informacji o narzędziu Host usługi WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Po zainstalowaniu programu Visual Studio z ustawieniami środowiska dewelopera języka Visual Basic, rozwiązanie może być ukryta. Jeśli jest to możliwe, wybierz opcję **opcje** z **narzędzia** menu, następnie wybierz pozycję **projekty i rozwiązania** > **ogólne** w **opcje** okna. Wybierz **zawsze pokazuj rozwiązanie**. Ponadto upewnij się, że **Zapisz nowe projekty po utworzeniu** jest zaznaczone.

3. Z **Eksploratora rozwiązań**, otwórz **IService1.cs** lub **IService1.vb** pliku i zastąp jego kod poniższym kodem:

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

     Ten kontrakt definiuje kalkulatora online. Zwróć uwagę `ICalculator` interfejs z oznaczeniem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu (uproszczone jako `ServiceContract`). Ten atrybut definiuje przestrzeni nazw, aby odróżnić nazwy kontraktu. Ten kod oznacza każda operacja Kalkulator, za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu (uproszczone jako `OperationContract`).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Utwórz projekt biblioteki usługi WCF.
> - Zdefiniuj interfejs kontraktu usługi.

Przejdź do następnego samouczka, aby dowiedzieć się, jak: Implementowanie kontraktu usługi WCF.

> [!div class="nextstepaction"]
> [Samouczek: Implementowanie kontraktu usługi WCF](how-to-implement-a-wcf-contract.md)
