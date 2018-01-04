---
title: "Instrukcje: Uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 425d17fa34b61985ad3600f992e028e156f6adb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="b803a-102">Instrukcje: Uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="b803a-102">How to: Access Services with a Duplex Contract</span></span>
<span data-ttu-id="b803a-103">Jedna funkcja [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest możliwość tworzenia usługi, który korzysta ze wzorca komunikacji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="b803a-103">One feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="b803a-104">Ten wzorzec umożliwia usługi do komunikacji z klientem za pośrednictwem wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b803a-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="b803a-105">W tym temacie przedstawiono kroki, aby utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta w klasie klienta, który implementuje interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b803a-105">This topic shows the steps to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client in a client class that implements the callback interface.</span></span>  
  
 <span data-ttu-id="b803a-106">Dwa powiązania udostępnia adres IP klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="b803a-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="b803a-107">Klienta należy użyć zabezpieczeń, aby upewnić się, że go tylko łączy się z usługami go relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="b803a-107">The client should use security to ensure that it connects only to services it trusts.</span></span>  
  
 <span data-ttu-id="b803a-108">Samouczek dotyczący tworzenia podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi i klienta, zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="b803a-108">For a tutorial on creating a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
### <a name="to-access-a-duplex-service"></a><span data-ttu-id="b803a-109">Dostęp do usługi dupleksu</span><span class="sxs-lookup"><span data-stu-id="b803a-109">To access a duplex service</span></span>  
  
1.  <span data-ttu-id="b803a-110">Utwórz usługę, która zawiera dwa interfejsy.</span><span class="sxs-lookup"><span data-stu-id="b803a-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="b803a-111">Pierwszy interfejs dla usługi, druga jest przeznaczona dla wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b803a-111">The first interface is for the service, the second is for the callback.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b803a-112">Tworzenie usługi duplex, zobacz [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b803a-112"> creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
2.  <span data-ttu-id="b803a-113">Uruchom usługę.</span><span class="sxs-lookup"><span data-stu-id="b803a-113">Run the service.</span></span>  
  
3.  <span data-ttu-id="b803a-114">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kontraktów (interfejsy) dla klienta.</span><span class="sxs-lookup"><span data-stu-id="b803a-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="b803a-115">Aby dowiedzieć się, jak to zrobić, zobacz [porady: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="b803a-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
4.  <span data-ttu-id="b803a-116">Zaimplementuj interfejs wywołania zwrotnego w klasie klienta, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b803a-116">Implement the callback interface in the client class, as shown in the following example.</span></span>  
  
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
  
5.  <span data-ttu-id="b803a-117">Utworzenie wystąpienia <xref:System.ServiceModel.InstanceContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="b803a-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="b803a-118">Konstruktor wymaga wystąpienia klasy klienta.</span><span class="sxs-lookup"><span data-stu-id="b803a-118">The constructor requires an instance of the client class.</span></span>  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <span data-ttu-id="b803a-119">Utwórz wystąpienie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta przy użyciu konstruktora, który wymaga <xref:System.ServiceModel.InstanceContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b803a-119">Create an instance of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="b803a-120">Drugi parametr konstruktora jest nazwa punktu końcowego znalezione w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b803a-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  <span data-ttu-id="b803a-121">Wywołanie metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="b803a-121">Call the methods of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b803a-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="b803a-122">Example</span></span>  
 <span data-ttu-id="b803a-123">Poniższy przykładowy kod przedstawia sposób tworzenia klasy klienta, który uzyskuje dostęp do kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="b803a-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="b803a-124">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b803a-124">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b803a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b803a-125">See Also</span></span>  
 [<span data-ttu-id="b803a-126">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="b803a-126">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="b803a-127">Instrukcje: tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="b803a-127">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="b803a-128">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="b803a-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="b803a-129">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="b803a-129">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="b803a-130">Instrukcje: używanie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="b803a-130">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
