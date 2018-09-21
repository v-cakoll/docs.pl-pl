---
title: 'Instrukcje: Definiowanie kontraktu usługi Windows Communication Foundation'
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 4f85a51c47eb045d1d2f0111cb217199c9acf0d7
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537881"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Instrukcje: Definiowanie kontraktu usługi Windows Communication Foundation

Jest to pierwszy z sześciu zadań podrzędnych, wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.

 Podczas tworzenia usługi WCF, pierwsze zadanie jest definiowanie kontraktu usługi. Kontrakt usługi określa, jakie operacje obsługuje usługi. Operacja można traktować jako metoda usługi sieci Web. Kontrakty są tworzone przez definiowanie interfejsu C++, C# lub Visual Basic (VB). Każda metoda w interfejsie odpowiada określonej operacji usługi. Każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> zastosowano i każdej operacji musi być <xref:System.ServiceModel.OperationContractAttribute> zastosowany do niego. Jeśli metoda w interfejsie z atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybut nie ma <xref:System.ServiceModel.OperationContractAttribute> atrybutu, że metoda nie są udostępniane przez usługę.

 Kod używany dla tego zadania znajduje się w przykładzie zamieszczonym po procedurze.

## <a name="define-a-service-contract"></a>Definiowanie kontraktu usługi

1. Otwórz program Visual Studio jako administrator, klikając prawym przyciskiem myszy program w **Start** menu i wybierając polecenie **więcej** > **Uruchom jako administrator**.

2. Utwórz projekt biblioteki usługi WCF.

   1. Z **pliku** menu, wybierz opcję **New** > **projektu**.

   2. W **nowy projekt** okna dialogowego po lewej stronie rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **WCF** kategorii. Listy szablonów projektu jest wyświetlany w w górnej części okna dialogowego. Wybierz **biblioteki usługi WCF**.

   3. Wprowadź `GettingStartedLib` w **nazwa** pole tekstowe i `GettingStarted` w **Nazwa rozwiązania** pole tekstowe w dolnej części okna dialogowego.

   > [!NOTE]
   > Jeśli nie widzisz **WCF** kategorii szablonu projektu, użytkownik może być konieczne zainstalowanie **Windows Communication Foundation** składnika programu Visual Studio. W **nowy projekt** okna dialogowego kliknij łącze, które mówi **Otwórz Instalator programu Visual Studio**. Wybierz **poszczególne składniki** kartę, a następnie znajdź i zaznacz **Windows Communication Foundation** w obszarze **działań programistycznych** kategorii. Wybierz **Modyfikuj** do rozpoczęcia instalacji tego składnika.

   Program Visual Studio tworzy projekt, który zawiera pliki 3: IService1.cs (lub IService1.vb) Service1.cs (lub Service1.vb) i pliku App.config. Plik IService1 zawiera domyślny kontrakt usługi. Plik Service1 zawiera domyślną implementację kontraktu usługi. Plik App.config zawiera konfiguracji potrzebne do załadowania domyślnej usługi za pomocą programu Visual Studio Host usługi WCF. Aby uzyskać więcej informacji o narzędziu Host usługi WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)

3. Otwórz plik IService1.cs lub IService1.vb i Usuń kod w deklaracji przestrzeni nazw, pozostawiając deklarację przestrzeni nazw. W obszarze nazw deklaracji Zdefiniuj nowy interfejs o nazwie `ICalculator` jak pokazano w poniższym kodzie.

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

     Ten kontrakt definiuje kalkulatora online. Zwróć uwagę `ICalculator` interfejs z oznaczeniem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Ten atrybut definiuje obszar nazw, który służy do odróżniania nazw kontraktu. Każda operacja Kalkulator jest oznaczona za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Porady: Implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Instrukcje: implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)