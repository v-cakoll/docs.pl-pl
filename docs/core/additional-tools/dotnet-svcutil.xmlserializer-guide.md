---
title: Korzystanie z dotnet-Svcutil. XmlSerializer
description: Dowiedz się, jak za pomocą pakietu NuGet `dotnet-svcutil.xmlserializer` wstępnie wygenerować zestaw serializacji dla projektów .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 4811647c294118cb160d25805e7d3ada97f071f9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344903"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Używanie programu dotnet-Svcutil. XmlSerializer w programie .NET Core

Pakiet NuGet `dotnet-svcutil.xmlserializer` może wstępnie wygenerować zestaw serializacji dla projektów .NET Core. Wstępnie generuje C# kod serializacji dla typów w aplikacji klienckiej, które są używane przez kontrakt usługi WCF i który może zostać Zserializowany przez element XmlSerializer. Poprawia to wydajność uruchomienia serializacji XML podczas serializacji lub deserializacji obiektów tych typów.

## <a name="prerequisites"></a>Wymagania wstępne

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowszy
* Ulubiony Edytor kodu

Możesz użyć `dotnet --info` polecenia, aby sprawdzić, które wersje zestaw .NET Core SDK i środowiska uruchomieniowego zostały już zainstalowane.

## <a name="getting-started"></a>Wprowadzenie

Aby użyć `dotnet-svcutil.xmlserializer` w aplikacji konsolowej programu .NET Core:

1. Utwórz usługę WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "aplikacja usługi WCF" w .NET Framework. Dodaj atrybut `[XmlSerializerFormat]` w metodzie usługi podobny do następującego:

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

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    Aby upewnić się, że projekt jest przeznaczony dla platformy .NET Core 2,1 lub nowszej, sprawdź `TargetFramework` element XML w pliku projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Dodaj odwołanie do pakietu do `System.ServiceModel.Http`, uruchamiając następujące polecenie:

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

5. Dodaj odwołanie do pakietu `dotnet-svcutil.xmlserializer`, uruchamiając następujące polecenie:
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Uruchomienie polecenia powinno spowodować dodanie wpisu do pliku projektu podobnego do tego:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Kompilowanie aplikacji przez uruchomienie `dotnet build`. Jeśli wszystko powiedzie się, zestaw o nazwie *MyWCFClient. XmlSerializers. dll* jest generowany w folderze wyjściowym. Jeśli narzędzie nie wygenerowało zestawu, zobaczysz ostrzeżenia w danych wyjściowych kompilacji.

7. Uruchom usługę WCF, wykonując na przykład `http://localhost:2561/Service1.svc` w przeglądarce. Następnie uruchom aplikację kliencką, która będzie automatycznie ładować i korzystać z wstępnie wygenerowanych serializatorów w czasie wykonywania.
