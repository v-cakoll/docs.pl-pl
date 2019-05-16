---
title: Za pomocą polecenia dotnet svcutil.xmlserializer na platformie .NET Core
description: Dowiedz się, jak można użyć `dotnet-svcutil.xmlserializer` pakietu NuGet można wstępnie wygenerować zestawu serializacji dla projektów .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 375a5ad5660658431c0d327e55513024823a6eee
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632199"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Za pomocą polecenia dotnet svcutil.xmlserializer na platformie .NET Core

`dotnet-svcutil.xmlserializer` Pakietu NuGet można wstępnie wygenerować zestawu serializacji dla projektów .NET Core. Wstępnie generuje C# kodu serializacji dla typów w aplikacji klienckiej, które są używane przez kontraktu usługi WCF i może być serializowany przez obiekt XmlSerializer. Zwiększa to wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów z tych typów.

## <a name="prerequisites"></a>Wymagania wstępne

* [Zestaw SDK programu .NET core 2.1](https://www.microsoft.com/net/download) lub nowszej
* Wybrany edytor kodu

Możesz użyć polecenia `dotnet --info` do sprawdzenia, które wersje programu .NET Core SDK i środowiska uruchomieniowego została już zainstalowana.

## <a name="getting-started"></a>Wprowadzenie

Aby użyć `dotnet-svcutil.xmlserializer` platformie .NET Core konsoli aplikacji:

1. Tworzenie usługi WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "Aplikacja usługi WCF" w programie .NET Framework. Dodaj `[XmlSerializerFormat]` atrybutu metody usługi, jak pokazano poniżej:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. Tworzenie aplikacji konsolowej .NET Core, jako aplikacja klienta WCF przeznaczonego na platformy .NET Core 2.1 lub nowszej wersji. Na przykład utworzyć aplikację o nazwie "MyWCFClient" za pomocą następującego polecenia:

    ```console
    dotnet new console --name MyWCFClient
    ```

    Aby upewnić się, projekt jest przeznaczony dla platformy .NET Core 2.1 lub nowszej, zbadaj `TargetFramework` — element XML w pliku projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Dodaj odwołanie do pakietu `System.ServiceModel.Http` , uruchamiając następujące polecenie:

    ```console
    dotnet add package System.ServiceModel.Http
    ```

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

5. Dodaj odwołanie do `dotnet-svcutil.xmlserializer` pakietu, uruchamiając następujące polecenie:
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Uruchomienie polecenia należy dodać wpis do pliku projektu podobny do następującego:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Kompiluj aplikację, uruchamiając `dotnet build`. Jeśli wszystko, co zakończy się powodzeniem, zestaw o nazwie *MyWCFClient.XmlSerializers.dll* jest generowany w folderze wyjściowym. Jeśli narzędzie nie można wygenerować zestawu, zostanie wyświetlone ostrzeżenia w danych wyjściowych kompilacji.

7. Uruchom usługę WCF, na przykład `http://localhost:2561/Service1.svc` w przeglądarce. Następnie uruchom aplikację klienta, a także będą automatycznie załadować i użyć wstępnie wygenerowanego serializatory w czasie wykonywania.
