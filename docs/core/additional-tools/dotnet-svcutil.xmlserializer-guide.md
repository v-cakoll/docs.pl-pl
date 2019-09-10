---
title: Używanie programu dotnet-Svcutil. XmlSerializer w programie .NET Core
description: Dowiedz się, `dotnet-svcutil.xmlserializer` jak za pomocą pakietu NuGet wstępnie wygenerować zestaw serializacji dla projektów .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: a98f8d30f2e37b722a3bf1f93be8fe9df540a468
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848970"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Używanie programu dotnet-Svcutil. XmlSerializer w programie .NET Core

Pakiet `dotnet-svcutil.xmlserializer` NuGet może wstępnie wygenerować zestaw serializacji dla projektów .NET Core. Wstępnie generuje C# kod serializacji dla typów w aplikacji klienckiej, które są używane przez kontrakt usługi WCF i który może zostać Zserializowany przez element XmlSerializer. Poprawia to wydajność uruchomienia serializacji XML podczas serializacji lub deserializacji obiektów tych typów.

## <a name="prerequisites"></a>Wymagania wstępne

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowszy
* Ulubiony Edytor kodu

Możesz użyć polecenia `dotnet --info` , aby sprawdzić, które wersje zestaw .NET Core SDK i środowiska uruchomieniowego zostały już zainstalowane.

## <a name="getting-started"></a>Wprowadzenie

Aby użyć `dotnet-svcutil.xmlserializer` w aplikacji konsolowej programu .NET Core:

1. Utwórz usługę WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "aplikacja usługi WCF" w .NET Framework. Dodaj `[XmlSerializerFormat]` atrybut do metody usługi w następujący sposób:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. Utwórz aplikację konsolową .NET Core jako aplikację kliencką WCF, która jest przeznaczona dla programu .NET Core 2,1 lub jego nowszych wersji. Na przykład Utwórz aplikację o nazwie "MyWCFClient" za pomocą następującego polecenia:

    ```console
    dotnet new console --name MyWCFClient
    ```

    Aby upewnić się, że projekt jest przeznaczony dla platformy .NET Core 2,1 `TargetFramework` lub nowszej, zbadaj element XML w pliku projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Dodaj odwołanie do pakietu do `System.ServiceModel.Http` programu, uruchamiając następujące polecenie:

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

    Uruchomienie polecenia powinno spowodować dodanie wpisu do pliku projektu podobnego do tego:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Skompiluj aplikację, uruchamiając `dotnet build`. Jeśli wszystko powiedzie się, zestaw o nazwie *MyWCFClient. XmlSerializers. dll* jest generowany w folderze wyjściowym. Jeśli narzędzie nie wygenerowało zestawu, zobaczysz ostrzeżenia w danych wyjściowych kompilacji.

7. Uruchom usługę WCF, na przykład działającej `http://localhost:2561/Service1.svc` w przeglądarce. Następnie uruchom aplikację kliencką, która będzie automatycznie ładować i korzystać z wstępnie wygenerowanych serializatorów w czasie wykonywania.
