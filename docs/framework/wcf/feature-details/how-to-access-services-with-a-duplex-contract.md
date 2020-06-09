---
title: 'Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dupleksowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597218"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dupleksowego

Jedną z funkcji programu Windows Communication Foundation (WCF) jest możliwość tworzenia usługi korzystającej ze wzorca obsługi komunikatów dupleksowych. Ten wzorzec umożliwia usłudze komunikowanie się z klientem za pomocą wywołania zwrotnego. W tym temacie przedstawiono procedurę tworzenia klienta WCF w klasie klienta implementującej interfejs wywołania zwrotnego.

Podwójne powiązanie uwidacznia adres IP klienta w usłudze. Klient powinien używać zabezpieczeń, aby upewnić się, że nawiązuje połączenie tylko z usługami, które ufają.

Aby zapoznać się z samouczkiem dotyczącym tworzenia podstawowej usługi i klienta WCF, zobacz [samouczek wprowadzenie](../getting-started-tutorial.md).

## <a name="to-access-a-duplex-service"></a>Aby uzyskać dostęp do usługi dupleksowej

1. Utwórz usługę, która zawiera dwa interfejsy. Pierwszy interfejs dotyczy usługi, a drugi jest dla wywołania zwrotnego. Aby uzyskać więcej informacji na temat tworzenia usługi dupleksowej, zobacz [How to: Create a Duplex kontraktu](how-to-create-a-duplex-contract.md).

2. Uruchom usługę.

3. Użyj [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania kontraktów (interfejsów) dla klienta. Aby uzyskać informacje o tym, jak to zrobić, zobacz [How to: Create a Client](../how-to-create-a-wcf-client.md).

4. Zaimplementuj interfejs wywołania zwrotnego w klasie Client, jak pokazano w poniższym przykładzie.

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. Utworzenie wystąpienia <xref:System.ServiceModel.InstanceContext> klasy. Konstruktor wymaga wystąpienia klasy klienta.

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. Utwórz wystąpienie klienta WCF przy użyciu konstruktora wymagającego <xref:System.ServiceModel.InstanceContext> obiektu. Drugim parametrem konstruktora jest nazwa punktu końcowego znajdującego się w pliku konfiguracji.

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. Wywołaj metody klienta WCF zgodnie z wymaganiami.

## <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje sposób tworzenia klasy klienta, która uzyskuje dostęp do kontraktu dupleksowego.

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie — samouczek](../getting-started-tutorial.md)
- [Instrukcje: tworzenie kontraktu dwukierunkowego](how-to-create-a-duplex-contract.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Instrukcje: tworzenie klienta](../how-to-create-a-wcf-client.md)
- [Instrukcje: używanie elementu ChannelFactory](how-to-use-the-channelfactory.md)
