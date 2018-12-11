# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="7e8ea-101">Za pomocą polecenia dotnet svcutil.xmlserializer na platformie .NET Core</span><span class="sxs-lookup"><span data-stu-id="7e8ea-101">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7e8ea-102">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7e8ea-102">Prerequisites</span></span>

<span data-ttu-id="7e8ea-103">Wymagane jest spełnienie następujących dla platformy dotnet-svcutil.xmlserializer do pracy.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-103">The following is required for dotnet-svcutil.xmlserializer to work.</span></span> 

* [<span data-ttu-id="7e8ea-104">Zestaw SDK programu .NET core 2.1 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="7e8ea-104">.NET Core 2.1 SDK or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [<span data-ttu-id="7e8ea-105">Środowisko uruchomieniowe programu .NET core 2.1 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="7e8ea-105">.NET Core Runtime 2.1 or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

<span data-ttu-id="7e8ea-106">Możesz użyć polecenia `dotnet --info` do sprawdzenia, które wersje programu .NET Core SDK i środowiska uruchomieniowego została już zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-106">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

<span data-ttu-id="7e8ea-107">Aby użyć polecenia dotnet svcutil.xmlserializer w aplikacji konsolowej .NET Core:</span><span class="sxs-lookup"><span data-stu-id="7e8ea-107">To use dotnet-svcutil.xmlserializer in a .NET Core console application:</span></span>

1. <span data-ttu-id="7e8ea-108">Tworzenie usługi WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "Aplikacja usługi WCF" w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-108">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span>  <span data-ttu-id="7e8ea-109">Dodaj ```[XmlSerializerFormat]``` atrybutu metody usługi, jak pokazano poniżej</span><span class="sxs-lookup"><span data-stu-id="7e8ea-109">Add ```[XmlSerializerFormat]``` attribute on the service method like the following</span></span>
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. <span data-ttu-id="7e8ea-110">Tworzenie aplikacji konsolowej .NET Core, jako aplikacja klienta WCF, obiekty docelowe na element netcoreapp 2.1, np. Utwórz aplikację przy użyciu polecenia, o nazwie "MyWCFClient"</span><span class="sxs-lookup"><span data-stu-id="7e8ea-110">Create a .NET Core console application as WCF client application that targets at netcoreapp 2.1, e.g. create an app named 'MyWCFClient' with the command,</span></span>
    ```
    dotnet new console --name MyWCFClient
    ```
    <span data-ttu-id="7e8ea-111">Upewnij się, że Twoje pliku csproj jest przeznaczony dla netcoreapp 2.1.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-111">Make sure your csproj targets a netcoreapp 2.1.</span></span> <span data-ttu-id="7e8ea-112">Odbywa się przy użyciu następujących elementów XML w pliku csproj</span><span class="sxs-lookup"><span data-stu-id="7e8ea-112">This is done using the following XML element in your .csproj file</span></span>
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. <span data-ttu-id="7e8ea-113">Dodaj odwołania do pakietu do System.ServiceModel.Http, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7e8ea-113">Add a package reference to System.ServiceModel.Http by running the following command:</span></span>
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. <span data-ttu-id="7e8ea-114">Dodaj kod klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="7e8ea-114">Add the WCF Client code:</span></span>
    ```csharp
    using System.ServiceModel;
    
    class Program
    {
        static void Main(string[] args)
        {
            var myBinding = new BasicHttpBinding();
            var myEndpoint = new EndpointAddress("http://localhost:2561/Service1.svc"); //Fill your service url here
            var myChannelFactory = new ChannelFactory<IService1>(myBinding, myEndpoint);
            IService1 client = myChannelFactory.CreateChannel();
            string s = client.GetData(1);
            ((ICommunicationObject)client).Close();
        }
    }

    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
5. <span data-ttu-id="7e8ea-115">Edytuj plik csproj i Dodaj odwołanie do pakietu dotnet svcutil.xmlserializer.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-115">Edit the .csproj file and add a reference to the dotnet-svcutil.xmlserializer package.</span></span> <span data-ttu-id="7e8ea-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7e8ea-116">For example:</span></span>

    <span data-ttu-id="7e8ea-117">i.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-117">i.</span></span> <span data-ttu-id="7e8ea-118">Uruchom polecenie: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span><span class="sxs-lookup"><span data-stu-id="7e8ea-118">Run command: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span></span>

    <span data-ttu-id="7e8ea-119">ii.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-119">ii.</span></span> <span data-ttu-id="7e8ea-120">Dodaj następujące wiersze w MyWCFClient.csproj,</span><span class="sxs-lookup"><span data-stu-id="7e8ea-120">Add the following lines in MyWCFClient.csproj,</span></span>
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="7e8ea-121">Kompiluj aplikację, uruchamiając `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-121">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="7e8ea-122">Jeśli wszystko, co zakończy się powodzeniem, zestaw o nazwie MyWCFClient.XmlSerializers.dll zostanie wygenerowany w folderze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-122">If everything succeeds, an assembly named MyWCFClient.XmlSerializers.dll will be generated in the output folder.</span></span> <span data-ttu-id="7e8ea-123">Jeśli narzędzie nie można wygenerować zestawu, zostanie wyświetlone ostrzeżenia w danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-123">You will see warnings in the build output if the tool failed to generate the assembly.</span></span>

7. <span data-ttu-id="7e8ea-124">Uruchom usługi WCF, np. uruchamiając http://localhost:2561/Service1.svc w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-124">Start the WCF service e.g. by running http://localhost:2561/Service1.svc in the browser.</span></span> <span data-ttu-id="7e8ea-125">Następnie uruchom aplikację klienta, a także będą automatycznie załadować i użyć wstępnie wygenerowanego serializatory w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-125">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
