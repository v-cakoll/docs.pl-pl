---
title: 'Instrukcje: rejestrowanie i Konfigurowanie monikera usługi'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: fc0b2d00bcc8e3b14c491446f16297c1036b783b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747089"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Instrukcje: rejestrowanie i Konfigurowanie monikera usługi

Przed użyciem monikera usługi Windows Communication Foundation (WCF) w ramach aplikacji COM z umową z określonym typem, należy zarejestrować wymagane typy z atrybutami COM i skonfigurować aplikację COM oraz moniker z wymaganym powiązaniem skonfigurować.

## <a name="register-the-required-attributed-types-with-com"></a>Rejestrowanie wymaganych typów atrybutów z modelem COM

1. Użyj narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , aby pobrać kontrakt metadanych z usługi WCF. Spowoduje to wygenerowanie kodu źródłowego dla zestawu klienta WCF i pliku konfiguracji aplikacji klienckiej.

2. Upewnij się, że typy w zestawie są oznaczone jako `ComVisible`. Aby to zrobić, Dodaj następujący atrybut do pliku *AssemblyInfo.cs* w projekcie programu Visual Studio.

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. Kompiluj zarządzany klient WCF jako zestaw o silnej nazwie. Wymaga to podpisania za pomocą pary kluczy kryptograficznych. Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../../standard/assembly/sign-strong-name.md).

4. Użyj narzędzia rejestracji zestawu (Regasm. exe) z opcją `-tlb`, aby zarejestrować typy w zestawie przy użyciu modelu COM.

5. Użyj narzędzia globalnej pamięci podręcznej zestawów (Gacutil. exe), aby dodać zestaw do globalnej pamięci podręcznej zestawów.

    > [!NOTE]
    > Podpisywanie zestawu i dodawanie go do globalnej pamięci podręcznej zestawów to kroki opcjonalne, ale mogą uprościć proces ładowania zestawu z właściwej lokalizacji w czasie wykonywania.

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>Skonfiguruj aplikację COM i moniker z wymaganą konfiguracją powiązania

- Umieść definicje powiązań (wygenerowane przez [Narzędzie do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w pliku konfiguracyjnym wygenerowanej aplikacji klienta) w pliku konfiguracyjnym aplikacji klienta. Na przykład w przypadku pliku wykonywalnego Visual Basic 6,0 o nazwie CallCenterClient. exe Konfiguracja powinna zostać umieszczona w pliku o nazwie CallCenterConfig. exe. config w tym samym katalogu, w którym znajduje się plik wykonywalny. Aplikacja kliencka może teraz używać monikera. Należy pamiętać, że konfiguracja powiązania nie jest wymagana, jeśli używany jest jeden ze standardowych typów powiązań dostarczonych przez program WCF.

     Następujący typ jest zarejestrowany.

    ```csharp
    using System.ServiceModel;

    [ServiceContract]
    public interface IMathService
    {
        [OperationContract]
        public int Add(int x, int y);
        [OperationContract]
        public int Subtract(int x, int y);
    }
    ```

     Aplikacja zostanie udostępniona przy użyciu powiązania `wsHttpBinding`. W przypadku danego typu i konfiguracji aplikacji używane są następujące przykładowe ciągi monikera.

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     lub

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     Można użyć dowolnego z tych ciągów monikera z poziomu aplikacji Visual Basic 6,0, po dodaniu odwołania do zestawu zawierającego typy `IMathService`, jak pokazano w poniższym przykładowym kodzie.

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     W tym przykładzie definicja `Binding1` konfiguracji powiązania jest przechowywana w pliku konfiguracyjnym o odpowiednich nazwach dla aplikacji klienckiej, takiej jak *vb6appname. exe. config*.

    > [!NOTE]
    > Możesz użyć podobnego kodu w C#, a C++lub dowolnej innej aplikacji języka .NET.

    > [!NOTE]
    > Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie do `GetObject` zwraca błąd "Nieprawidłowa składnia". Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.

     Chociaż ten temat koncentruje się na używaniu monikera usługi w Visual Basic kodzie 6,0, można użyć monikera usługi z innych języków. W przypadku używania monikera C++ z kodu, zestaw wygenerowany przez Svcutil. exe powinien zostać zaimportowany z "no_namespace named_guids raw_interfaces_only", jak pokazano w poniższym kodzie.

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     Powoduje to modyfikację zaimportowanych definicji interfejsu, tak aby wszystkie metody zwracały `HResult`. Wszystkie inne zwracane wartości są konwertowane na parametry out. Ogólne wykonywanie metod pozostaje bez zmian. Pozwala to określić przyczynę wyjątku podczas wywoływania metody na serwerze proxy. Ta funkcja jest dostępna tylko w C++ kodzie.

## <a name="see-also"></a>Zobacz także

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
