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
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="0eb4e-102">Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="0eb4e-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="0eb4e-103">Jedna z funkcji Windows Communication Foundation (WCF) jest możliwość tworzenia to usługa, która używa dwukierunkowego wzorzec przesyłania komunikatów dotyczących.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="0eb4e-104">Ten wzorzec umożliwia użycie usługi do komunikacji z klientem za pośrednictwem wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="0eb4e-105">W tym temacie przedstawiono kroki umożliwiające utworzenie klienta WCF w klasie klienta, który implementuje interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="0eb4e-106">Podwójna powiązania udostępnia adres IP klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="0eb4e-107">Klienta należy użyć zabezpieczeń, aby upewnić się, że nawiąże połączenie tylko z usługami jej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="0eb4e-108">Aby uzyskać samouczek dotyczący tworzenia podstawowe usługi i klienta WCF, zobacz [Samouczek wprowadzający](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="0eb4e-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="0eb4e-109">Dostęp do usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="0eb4e-109">To access a duplex service</span></span>

1. <span data-ttu-id="0eb4e-110">Utwórz usługę, która zawiera dwa interfejsy.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="0eb4e-111">Pierwszy interfejs dla usługi, druga jest przeznaczona dla wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="0eb4e-112">Aby uzyskać więcej informacji na temat tworzenia usługi duplex, zobacz [jak: Tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="0eb4e-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="0eb4e-113">Uruchom usługę.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-113">Run the service.</span></span>

3. <span data-ttu-id="0eb4e-114">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania zamówień (interfejsy) dla klienta.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="0eb4e-115">Aby dowiedzieć się, jak to zrobić, zobacz [jak: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="0eb4e-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="0eb4e-116">Implementuje interfejs wywołania zwrotnego w klasie klienta, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

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

5. <span data-ttu-id="0eb4e-117">Utworzenie wystąpienia <xref:System.ServiceModel.InstanceContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="0eb4e-118">Konstruktor wymaga wystąpienia klasy klienta.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="0eb4e-119">Utwórz wystąpienie obiektu klienta WCF, za pomocą konstruktora, który wymaga <xref:System.ServiceModel.InstanceContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="0eb4e-120">Drugi parametr konstruktora jest nazwa punktu końcowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="0eb4e-121">Wywołanie metody klienta WCF, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="0eb4e-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="0eb4e-122">Example</span></span>

<span data-ttu-id="0eb4e-123">Poniższy przykład kodu pokazuje, jak utworzyć klasę klienta, który uzyskuje dostęp do kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="0eb4e-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="0eb4e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0eb4e-124">See also</span></span>

- [<span data-ttu-id="0eb4e-125">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="0eb4e-125">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="0eb4e-126">Instrukcje: Tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="0eb4e-126">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="0eb4e-127">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="0eb4e-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="0eb4e-128">Instrukcje: Tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="0eb4e-128">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="0eb4e-129">Instrukcje: Używanie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="0eb4e-129">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
