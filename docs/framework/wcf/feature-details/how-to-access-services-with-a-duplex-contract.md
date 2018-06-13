---
title: 'Instrukcje: Uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: c0022e6ce3a63c1f497eeee82ca959cec1046cec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490155"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Instrukcje: Uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego
Jedna z funkcji Windows Communication Foundation (WCF) jest możliwość tworzenia usługi, który korzysta ze wzorca komunikacji dupleksowej. Ten wzorzec umożliwia usługi do komunikacji z klientem za pośrednictwem wywołania zwrotnego. W tym temacie przedstawiono kroki, aby utworzyć klienta WCF w klasie klienta, który implementuje interfejs wywołania zwrotnego.  
  
 Dwa powiązania udostępnia adres IP klienta do usługi. Klienta należy użyć zabezpieczeń, aby upewnić się, że go tylko łączy się z usługami go relacji zaufania.  
  
 Samouczek dotyczący tworzenia podstawowej usługi WCF i klienta, zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md).  
  
### <a name="to-access-a-duplex-service"></a>Dostęp do usługi dupleksu  
  
1.  Utwórz usługę, która zawiera dwa interfejsy. Pierwszy interfejs dla usługi, druga jest przeznaczona dla wywołania zwrotnego. Aby uzyskać więcej informacji na temat tworzenia usługi duplex zobacz [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
2.  Uruchom usługę.  
  
3.  Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kontraktów (interfejsy) dla klienta. Aby dowiedzieć się, jak to zrobić, zobacz [porady: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
4.  Zaimplementuj interfejs wywołania zwrotnego w klasie klienta, jak pokazano w poniższym przykładzie.  
  
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
  
5.  Utworzenie wystąpienia <xref:System.ServiceModel.InstanceContext> klasy. Konstruktor wymaga wystąpienia klasy klienta.  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  Utwórz wystąpienie klienta WCF, za pomocą konstruktora, który wymaga <xref:System.ServiceModel.InstanceContext> obiektu. Drugi parametr konstruktora jest nazwa punktu końcowego znalezione w pliku konfiguracji.  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  Wywołanie metody klienta WCF, zgodnie z wymaganiami.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób tworzenia klasy klienta, który uzyskuje dostęp do kontraktu dwukierunkowego.  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Instrukcje: tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Instrukcje: używanie elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
