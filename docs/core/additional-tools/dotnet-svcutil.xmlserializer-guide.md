# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Za pomocą polecenia dotnet svcutil.xmlserializer na platformie .NET Core

## <a name="prerequisites"></a>Wymagania wstępne

Wymagane jest spełnienie następujących dla platformy dotnet-svcutil.xmlserializer do pracy. 

* [Zestaw SDK programu .NET core 2.1 lub nowszej](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [Środowisko uruchomieniowe programu .NET core 2.1 lub nowszej](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

Możesz użyć polecenia `dotnet --info` do sprawdzenia, które wersje programu .NET Core SDK i środowiska uruchomieniowego została już zainstalowana.

Aby użyć polecenia dotnet svcutil.xmlserializer w aplikacji konsolowej .NET Core:

1. Tworzenie usługi WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "Aplikacja usługi WCF" w programie .NET Framework.  Dodaj ```[XmlSerializerFormat]``` atrybutu metody usługi, jak pokazano poniżej
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. Tworzenie aplikacji konsolowej .NET Core, jako aplikacja klienta WCF, obiekty docelowe na element netcoreapp 2.1, np. Utwórz aplikację przy użyciu polecenia, o nazwie "MyWCFClient"
    ```
    dotnet new console --name MyWCFClient
    ```
    Upewnij się, że Twoje pliku csproj jest przeznaczony dla netcoreapp 2.1. Odbywa się przy użyciu następujących elementów XML w pliku csproj
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. Dodaj odwołania do pakietu do System.ServiceModel.Http, uruchamiając następujące polecenie:
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. Dodaj kod klienta WCF:
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
5. Edytuj plik csproj i Dodaj odwołanie do pakietu dotnet svcutil.xmlserializer. Na przykład:

    i. Uruchom polecenie: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`

    ii. Dodaj następujące wiersze w MyWCFClient.csproj,
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Kompiluj aplikację, uruchamiając `dotnet build`. Jeśli wszystko, co zakończy się powodzeniem, zestaw o nazwie MyWCFClient.XmlSerializers.dll zostanie wygenerowany w folderze wyjściowym. Jeśli narzędzie nie można wygenerować zestawu, zostanie wyświetlone ostrzeżenia w danych wyjściowych kompilacji.

7. Uruchom usługi WCF, np. uruchamiając http://localhost:2561/Service1.svc w przeglądarce. Następnie uruchom aplikację klienta, a także będą automatycznie załadować i użyć wstępnie wygenerowanego serializatory w czasie wykonywania.
