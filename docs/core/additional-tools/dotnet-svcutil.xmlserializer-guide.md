---
title: Korzystanie z dotnet-svcutil.xmlserializer
description: Dowiedz się, jak `dotnet-svcutil.xmlserializer` użyć pakietu NuGet do wstępnego generowania zestawu serializacji dla projektów .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 4811647c294118cb160d25805e7d3ada97f071f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344903"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Korzystanie z dotnet-svcutil.xmlserializer w ustonach .NET Core

Pakiet `dotnet-svcutil.xmlserializer` NuGet można wstępnie wygenerować zestaw serializacji dla projektów .NET Core. Wstępnie generuje kod serializacji C# dla typów w aplikacji klienckiej, które są używane przez Kontrakt serwisowy WCF i które mogą być serializowane przez XmlSerializer. Zwiększa to wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów.

## <a name="prerequisites"></a>Wymagania wstępne

* [Sdk .NET Core 2.1](https://dotnet.microsoft.com/download) lub nowszy
* Twój ulubiony edytor kodu

Za pomocą polecenia `dotnet --info` można sprawdzić, które wersje programu .NET Core SDK i czas uruchomieniowy zostały już zainstalowane.

## <a name="getting-started"></a>Wprowadzenie

Aby `dotnet-svcutil.xmlserializer` użyć w aplikacji konsoli .NET Core:

1. Utwórz usługę WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "WCF Service Application" w .NET Framework. Dodaj `[XmlSerializerFormat]` atrybut do metody usługi, takie jak następujące:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. Utwórz aplikację konsoli .NET Core jako aplikację kliencką WCF, która jest przeznaczona dla wersji .NET Core 2.1 lub nowszych. Na przykład utwórz aplikację o nazwie "MyWCFClient" za pomocą następującego polecenia:

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    Aby upewnić się, że projekt jest przeznaczony dla `TargetFramework` programu .NET Core 2.1 lub nowszego, sprawdź element XML w pliku projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Dodaj odwołanie do `System.ServiceModel.Http` pakietu, uruchamiając następujące polecenie:

    ```dotnetcli
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
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Uruchomienie polecenia powinno dodać wpis do pliku projektu podobny do następującego:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Tworzenie aplikacji przez `dotnet build`uruchomienie . Jeśli wszystko się powiedzie, w folderze wyjściowym generowany jest zestaw o nazwie *MyWCFClient.XmlSerializers.dll.* Jeśli narzędzie nie może wygenerować zestawu, zobaczysz ostrzeżenia w danych wyjściowych kompilacji.

7. Uruchom usługę WCF, na przykład `http://localhost:2561/Service1.svc` działając w przeglądarce. Następnie uruchom aplikację kliencką i automatycznie załaduje i użyje wstępnie wygenerowanych serializatorów w czasie wykonywania.
