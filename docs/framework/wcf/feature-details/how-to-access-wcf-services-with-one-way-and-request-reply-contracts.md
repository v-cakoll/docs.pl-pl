---
title: 'Instrukcje: Uzyskiwanie dostępu do usług WCF za pomocą kontraktów jednokierunkowych i kontraktów „żądanie-odpowiedź”'
ms.date: 03/30/2017
ms.assetid: 7e10d3a5-fcf4-4a4b-a8d6-92ee2c988b3b
ms.openlocfilehash: 533b97892b15c9034679efba6e4da5e72b56099b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185140"
---
# <a name="how-to-access-wcf-services-with-one-way-and-request-reply-contracts"></a><span data-ttu-id="fa2b9-102">Instrukcje: Uzyskiwanie dostępu do usług WCF za pomocą kontraktów jednokierunkowych i kontraktów „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="fa2b9-102">How to: Access WCF Services with One-Way and Request-Reply Contracts</span></span>
<span data-ttu-id="fa2b9-103">W poniższych procedurach opisano sposób uzyskiwania dostępu do usługi Windows Communication Foundation (WCF), która definiuje umowę jednokierunkową i kontrakt żądanie-odpowiedź i która nie używa wzorca komunikacji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-103">The following procedures describe how to access a Windows Communication Foundation (WCF) service that defines a one-way contract and a request-reply contract and that does not use the duplex communication pattern.</span></span>  
  
### <a name="to-define-the-service"></a><span data-ttu-id="fa2b9-104">Aby zdefiniować usługę</span><span class="sxs-lookup"><span data-stu-id="fa2b9-104">To define the service</span></span>  
  
1. <span data-ttu-id="fa2b9-105">Zadeklaruj umowę serwisową.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-105">Declare the service contract.</span></span> <span data-ttu-id="fa2b9-106">Operacje, które mają być jednokierunkowe, `true` muszą <xref:System.ServiceModel.OperationContractAttribute>być `IsOneWay` ustawione w obrębie .</span><span class="sxs-lookup"><span data-stu-id="fa2b9-106">The operations that are to be one-way must have `IsOneWay` set to `true` within the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="fa2b9-107">Poniższy kod deklaruje `IOneWayCalculator` kontrakt, który ma `Add`operacje `Subtract` `Multiply`jednokierunkowe dla , , i `Divide`.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-107">The following code declares the `IOneWayCalculator` contract that has one-way operations for `Add`, `Subtract`, `Multiply`, and `Divide`.</span></span> <span data-ttu-id="fa2b9-108">Definiuje również operację odpowiedzi żądania `SayHello`o nazwie .</span><span class="sxs-lookup"><span data-stu-id="fa2b9-108">It also defines a request response operation called `SayHello`.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface IOneWayCalculator  
    {  
        [OperationContract(IsOneWay = true)]  
        void Add(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Subtract(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Multiply(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Divide(double n1, double n2);  
        [OperationContract]  
        string SayHello(string name);  
    }  
    ```  
  
2. <span data-ttu-id="fa2b9-109">Zaimplementuj umowę serwisową.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-109">Implement the service contract.</span></span> <span data-ttu-id="fa2b9-110">Poniższy kod implementuje `IOnewayCalculator` interfejs.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-110">The following code implements the `IOnewayCalculator` interface.</span></span>  
  
    ```csharp  
    [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.PerCall)]  
    public class CalculatorService : IOneWayCalculator  
    {  
        public void Add(double n1, double n2)  
        {  
           double result = n1 + n2;  
           Console.WriteLine("Add({0},{1}) = {2} ", n1, n2, result);  
        }  
  
        public void Subtract(double n1, double n2)  
        {  
           double result = n1 - n2;  
           Console.WriteLine("Subtract({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public void Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Multiply({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public void Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Divide({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public string SayHello(string name)  
        {  
            Console.WriteLine("SayHello({0})", name);  
            return "Hello " + name;  
        }  
    }  
    ```  
  
3. <span data-ttu-id="fa2b9-111">Hostuj usługę w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-111">Host the service in a console application.</span></span> <span data-ttu-id="fa2b9-112">Poniższy kod pokazuje, jak hostować usługę.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-112">The following code shows how to host the service.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
       // Define the base address for the service.  
       Uri baseAddress = new Uri("http://localhost:8000/servicemodelsamples/service");  
  
       // Create a ServiceHost for the CalculatorService type and provide the base address.  
       using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
       {  
            // Add an endpoint using the IOneWayCalculator contract and the WSHttpBinding  
            serviceHost.AddServiceEndpoint(typeof(IOneWayCalculator), new WSHttpBinding(), "");  
  
          // Turn on the metadata behavior, this allows svcutil to get metadata for the service.  
          ServiceMetadataBehavior smb = (ServiceMetadataBehavior) serviceHost.Description.Behaviors.Find<ServiceMetadataBehavior>();  
          if (smb == null)  
          {  
                smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                serviceHost.Description.Behaviors.Add(smb);  
          }  
  
          // Open the ServiceHostBase to create listeners and start listening for messages.  
          serviceHost.Open();  
  
          // The service can now be accessed.  
          Console.WriteLine("The service is ready.");  
          Console.WriteLine("Press <ENTER> to terminate service.");  
          Console.WriteLine();  
          Console.ReadLine();  
        }  
    }  
    ```  
  
### <a name="to-access-the-service"></a><span data-ttu-id="fa2b9-113">Aby uzyskać dostęp do usługi</span><span class="sxs-lookup"><span data-stu-id="fa2b9-113">To access the service</span></span>  
  
1. <span data-ttu-id="fa2b9-114">Uruchom [narzędzie servicemodel metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) przy użyciu adresu końcowego punktu końcowego wymiany `Svcutil http://localhost:8000/Service` metadanych w celu utworzenia klasy klienta dla usługi przy użyciu następującego wiersza polecenia: [Narzędzie narzędziowe metadata ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje zestaw interfejsów i klas, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-114">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) using the metadata exchange endpoint address to create the client class for the service using the following command line: `Svcutil http://localhost:8000/Service` The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generates a set of interfaces and classes, as shown in the following sample code.</span></span>  
  
    ```csharp  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    [System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="IOneWayCalculator")]  
    public interface IOneWayCalculator  
    {  
  
        [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/Add")]  
        void Add(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/Subtract")]  
        void Subtract(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/Multiply")]  
        void Multiply(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/Divide")]  
        void Divide(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/SayHello", ReplyAction="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/SayHelloResponse")]  
        string SayHello(string name);  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    public interface IOneWayCalculatorChannel : IOneWayCalculator, System.ServiceModel.IClientChannel  
    {  
    }  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    public partial class OneWayCalculatorClient : System.ServiceModel.ClientBase<IOneWayCalculator>, IOneWayCalculator  
    {  
  
        public OneWayCalculatorClient()  
        {  
        }  
  
        public OneWayCalculatorClient(string endpointConfigurationName) :
                base(endpointConfigurationName)  
        {  
        }  
  
        public OneWayCalculatorClient(string endpointConfigurationName, string remoteAddress) :
                base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public OneWayCalculatorClient(string endpointConfigurationName, System.ServiceModel.EndpointAddress remoteAddress) :
                base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public OneWayCalculatorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress remoteAddress) :
                base(binding, remoteAddress)  
        {  
        }  
  
        public void Add(double n1, double n2)  
        {  
            base.Channel.Add(n1, n2);  
        }  
  
        public void Subtract(double n1, double n2)  
        {  
            base.Channel.Subtract(n1, n2);  
        }  
  
        public void Multiply(double n1, double n2)  
        {  
            base.Channel.Multiply(n1, n2);  
        }  
  
        public void Divide(double n1, double n2)  
        {  
            base.Channel.Divide(n1, n2);  
        }  
  
        public string SayHello(string name)  
        {  
            return base.Channel.SayHello(name);  
        }  
    }  
    ```  
  
     <span data-ttu-id="fa2b9-115">Uwaga w `IOneWayCalculator` interfejsie, że jednokierunkowe <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> operacje usługi `true` mają atrybut ustawiony na i operacja usługi żądanie `false`odpowiedź ma atrybut ustawiony na wartość domyślną, .</span><span class="sxs-lookup"><span data-stu-id="fa2b9-115">Notice in the `IOneWayCalculator` interface that the one-way service operations have the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> attribute set to `true` and the request-reply service operation has the attribute set to the default value, `false`.</span></span> <span data-ttu-id="fa2b9-116">Zwróć również `OneWayCalculatorClient` uwagę na klasę.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-116">Also notice the `OneWayCalculatorClient` class.</span></span> <span data-ttu-id="fa2b9-117">Jest to klasa, która będzie używana do wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-117">This is the class that you will use to call the service.</span></span>  
  
2. <span data-ttu-id="fa2b9-118">Utwórz obiekt klienta.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-118">Create the client object.</span></span>  
  
    ```csharp  
    // Create a client  
    WSHttpBinding binding = new WSHttpBinding();  
    EndpointAddress epAddress = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
    OneWayCalculatorClient client = new OneWayCalculatorClient(binding, epAddress);  
    ```  
  
3. <span data-ttu-id="fa2b9-119">Wywołaj operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-119">Call service operations.</span></span>  
  
    ```csharp  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1})", value1, value2);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1})", value1, value2);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1})", value1, value2);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1})", value1, value2);  
  
    // Call the SayHello service operation  
    string name = "World";  
    string response = client.SayHello(name);  
    Console.WriteLine("SayHello([0])", name);  
    Console.WriteLine("SayHello() returned: " + response);  
    ```  
  
4. <span data-ttu-id="fa2b9-120">Zamknij klienta, aby zamknąć połączenia i oczyścić zasoby.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-120">Close the client to close connections and clean up resources.</span></span>  
  
    ```csharp  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="fa2b9-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa2b9-121">Example</span></span>  
 <span data-ttu-id="fa2b9-122">Poniżej znajduje się pełna lista kodu używanego w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="fa2b9-122">The following is a complete listing of the code used  in this topic.</span></span>  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface IOneWayCalculator  
    {  
        [OperationContract(IsOneWay = true)]  
        void Add(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Subtract(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Multiply(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Divide(double n1, double n2);  
        [OperationContract]  
        string SayHello(string name);  
    }  
  
    // Service class which implements the service contract.  
    // Added code to write output to the console window  
    [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.PerCall)]  
    public class CalculatorService : IOneWayCalculator  
    {  
        public void Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Add({0},{1}) = {2} ", n1, n2, result);  
        }  
  
        public void Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Subtract({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public void Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Multiply({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public void Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Divide({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public string SayHello(string name)  
        {  
            Console.WriteLine("SayHello({0})", name);  
            return "Hello " + name;  
        }  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Define the base address for the service.  
            Uri baseAddress = new Uri("http://localhost:8000/servicemodelsamples/service");  
  
            // Create a ServiceHost for the CalculatorService type and provide the base address.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
            {  
                // Add an endpoint using the IOneWayCalculator contract and the WSHttpBinding  
                serviceHost.AddServiceEndpoint(typeof(IOneWayCalculator), new WSHttpBinding(), "");  
  
                // Turn on the metadata behavior, this allows svcutil to get metadata for the service.  
                ServiceMetadataBehavior smb = (ServiceMetadataBehavior) serviceHost.Description.Behaviors.Find<ServiceMetadataBehavior>();  
                if (smb == null)  
                {  
                    smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    serviceHost.Description.Behaviors.Add(smb);  
                }  
  
                // Open the ServiceHostBase to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}
```

```csharp
// client.cs  
using System;  
using System.ServiceModel;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            // Create a client  
            WSHttpBinding binding = new WSHttpBinding();  
            EndpointAddress epAddress = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
            OneWayCalculatorClient client = new OneWayCalculatorClient(binding, epAddress);  
  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1})", value1, value2);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1})", value1, value2);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1})", value1, value2);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1})", value1, value2);  
  
            // Call the SayHello service operation  
            string name = "World";  
            string response = client.SayHello(name);  
            Console.WriteLine("SayHello([0])", name);  
            Console.WriteLine("SayHello() returned: " + response);  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa2b9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa2b9-123">See also</span></span>

- [<span data-ttu-id="fa2b9-124">Usługi jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="fa2b9-124">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
