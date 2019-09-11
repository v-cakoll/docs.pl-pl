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
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="729eb-103">Używanie programu dotnet-Svcutil. XmlSerializer w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="729eb-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="729eb-104">Pakiet `dotnet-svcutil.xmlserializer` NuGet może wstępnie wygenerować zestaw serializacji dla projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="729eb-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="729eb-105">Wstępnie generuje C# kod serializacji dla typów w aplikacji klienckiej, które są używane przez kontrakt usługi WCF i który może zostać Zserializowany przez element XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="729eb-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="729eb-106">Poprawia to wydajność uruchomienia serializacji XML podczas serializacji lub deserializacji obiektów tych typów.</span><span class="sxs-lookup"><span data-stu-id="729eb-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="729eb-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="729eb-107">Prerequisites</span></span>

* <span data-ttu-id="729eb-108">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="729eb-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="729eb-109">Ulubiony Edytor kodu</span><span class="sxs-lookup"><span data-stu-id="729eb-109">Your favorite code editor</span></span>

<span data-ttu-id="729eb-110">Możesz użyć polecenia `dotnet --info` , aby sprawdzić, które wersje zestaw .NET Core SDK i środowiska uruchomieniowego zostały już zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="729eb-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="729eb-111">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="729eb-111">Getting started</span></span>

<span data-ttu-id="729eb-112">Aby użyć `dotnet-svcutil.xmlserializer` w aplikacji konsolowej programu .NET Core:</span><span class="sxs-lookup"><span data-stu-id="729eb-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="729eb-113">Utwórz usługę WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "aplikacja usługi WCF" w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="729eb-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="729eb-114">Dodaj `[XmlSerializerFormat]` atrybut do metody usługi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="729eb-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="729eb-115">Utwórz aplikację konsolową .NET Core jako aplikację kliencką WCF, która jest przeznaczona dla programu .NET Core 2,1 lub jego nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="729eb-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="729eb-116">Na przykład Utwórz aplikację o nazwie "MyWCFClient" za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="729eb-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```console
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="729eb-117">Aby upewnić się, że projekt jest przeznaczony dla platformy .NET Core 2,1 `TargetFramework` lub nowszej, zbadaj element XML w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="729eb-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="729eb-118">Dodaj odwołanie do pakietu do `System.ServiceModel.Http` programu, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="729eb-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```console
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="729eb-119">Dodaj kod klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="729eb-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="729eb-120">Dodaj odwołanie do `dotnet-svcutil.xmlserializer` pakietu, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="729eb-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="729eb-121">Uruchomienie polecenia powinno spowodować dodanie wpisu do pliku projektu podobnego do tego:</span><span class="sxs-lookup"><span data-stu-id="729eb-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="729eb-122">Skompiluj aplikację, uruchamiając `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="729eb-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="729eb-123">Jeśli wszystko powiedzie się, zestaw o nazwie *MyWCFClient. XmlSerializers. dll* jest generowany w folderze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="729eb-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="729eb-124">Jeśli narzędzie nie wygenerowało zestawu, zobaczysz ostrzeżenia w danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="729eb-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="729eb-125">Uruchom usługę WCF, na przykład działającej `http://localhost:2561/Service1.svc` w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="729eb-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="729eb-126">Następnie uruchom aplikację kliencką, która będzie automatycznie ładować i korzystać z wstępnie wygenerowanych serializatorów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="729eb-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
