---
title: 'Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 2f83b8ac71bfc53791f7de42d127badbda0d3881
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610317"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego

Jedna z funkcji Windows Communication Foundation (WCF) jest możliwość tworzenia to usługa, która używa dwukierunkowego wzorzec przesyłania komunikatów dotyczących. Ten wzorzec umożliwia użycie usługi do komunikacji z klientem za pośrednictwem wywołania zwrotnego. W tym temacie przedstawiono kroki umożliwiające utworzenie klienta WCF w klasie klienta, który implementuje interfejs wywołania zwrotnego.

Podwójna powiązania udostępnia adres IP klienta do usługi. Klienta należy użyć zabezpieczeń, aby upewnić się, że nawiąże połączenie tylko z usługami jej relacji zaufania.

Aby uzyskać samouczek dotyczący tworzenia podstawowe usługi i klienta WCF, zobacz [Samouczek wprowadzający](../../../../docs/framework/wcf/getting-started-tutorial.md).

## <a name="to-access-a-duplex-service"></a>Dostęp do usługi dwukierunkowe

1. Utwórz usługę, która zawiera dwa interfejsy. Pierwszy interfejs dla usługi, druga jest przeznaczona dla wywołania zwrotnego. Aby uzyskać więcej informacji na temat tworzenia usługi duplex, zobacz [jak: Tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).

2. Uruchom usługę.

3. Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania zamówień (interfejsy) dla klienta. Aby dowiedzieć się, jak to zrobić, zobacz [jak: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).

4. Implementuje interfejs wywołania zwrotnego w klasie klienta, jak pokazano w poniższym przykładzie.

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
            Console.Writeline("Equation({0})", equation)
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

6. Utwórz wystąpienie obiektu klienta WCF, za pomocą konstruktora, który wymaga <xref:System.ServiceModel.InstanceContext> obiektu. Drugi parametr konstruktora jest nazwa punktu końcowego w pliku konfiguracji.

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. Wywołanie metody klienta WCF, zgodnie z potrzebami.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak utworzyć klasę klienta, który uzyskuje dostęp do kontraktu dwukierunkowego.

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Instrukcje: Tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Instrukcje: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Instrukcje: Używanie elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
