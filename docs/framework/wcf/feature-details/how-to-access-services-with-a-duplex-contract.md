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
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="19178-102">Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dupleksowego</span><span class="sxs-lookup"><span data-stu-id="19178-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="19178-103">Jedną z funkcji programu Windows Communication Foundation (WCF) jest możliwość tworzenia usługi korzystającej ze wzorca obsługi komunikatów dupleksowych.</span><span class="sxs-lookup"><span data-stu-id="19178-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="19178-104">Ten wzorzec umożliwia usłudze komunikowanie się z klientem za pomocą wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="19178-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="19178-105">W tym temacie przedstawiono procedurę tworzenia klienta WCF w klasie klienta implementującej interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="19178-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="19178-106">Podwójne powiązanie uwidacznia adres IP klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="19178-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="19178-107">Klient powinien używać zabezpieczeń, aby upewnić się, że nawiązuje połączenie tylko z usługami, które ufają.</span><span class="sxs-lookup"><span data-stu-id="19178-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="19178-108">Aby zapoznać się z samouczkiem dotyczącym tworzenia podstawowej usługi i klienta WCF, zobacz [samouczek wprowadzenie](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="19178-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="19178-109">Aby uzyskać dostęp do usługi dupleksowej</span><span class="sxs-lookup"><span data-stu-id="19178-109">To access a duplex service</span></span>

1. <span data-ttu-id="19178-110">Utwórz usługę, która zawiera dwa interfejsy.</span><span class="sxs-lookup"><span data-stu-id="19178-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="19178-111">Pierwszy interfejs dotyczy usługi, a drugi jest dla wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="19178-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="19178-112">Aby uzyskać więcej informacji na temat tworzenia usługi dupleksowej, zobacz [How to: Create a Duplex kontraktu](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="19178-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="19178-113">Uruchom usługę.</span><span class="sxs-lookup"><span data-stu-id="19178-113">Run the service.</span></span>

3. <span data-ttu-id="19178-114">Użyj [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania kontraktów (interfejsów) dla klienta.</span><span class="sxs-lookup"><span data-stu-id="19178-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="19178-115">Aby uzyskać informacje o tym, jak to zrobić, zobacz [How to: Create a Client](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="19178-115">For information about how to do this, see  [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="19178-116">Zaimplementuj interfejs wywołania zwrotnego w klasie Client, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="19178-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

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

5. <span data-ttu-id="19178-117">Utworzenie wystąpienia <xref:System.ServiceModel.InstanceContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="19178-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="19178-118">Konstruktor wymaga wystąpienia klasy klienta.</span><span class="sxs-lookup"><span data-stu-id="19178-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="19178-119">Utwórz wystąpienie klienta WCF przy użyciu konstruktora wymagającego <xref:System.ServiceModel.InstanceContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="19178-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="19178-120">Drugim parametrem konstruktora jest nazwa punktu końcowego znajdującego się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="19178-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="19178-121">Wywołaj metody klienta WCF zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="19178-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="19178-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="19178-122">Example</span></span>

<span data-ttu-id="19178-123">Poniższy przykład kodu demonstruje sposób tworzenia klasy klienta, która uzyskuje dostęp do kontraktu dupleksowego.</span><span class="sxs-lookup"><span data-stu-id="19178-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="19178-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19178-124">See also</span></span>

- [<span data-ttu-id="19178-125">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="19178-125">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="19178-126">Instrukcje: tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="19178-126">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="19178-127">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="19178-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="19178-128">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="19178-128">How to: Create a Client</span></span>](../how-to-create-a-wcf-client.md)
- [<span data-ttu-id="19178-129">Instrukcje: używanie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="19178-129">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
