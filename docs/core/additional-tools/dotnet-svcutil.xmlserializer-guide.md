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
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="22669-103">Korzystanie z dotnet-svcutil.xmlserializer w ustonach .NET Core</span><span class="sxs-lookup"><span data-stu-id="22669-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="22669-104">Pakiet `dotnet-svcutil.xmlserializer` NuGet można wstępnie wygenerować zestaw serializacji dla projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22669-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="22669-105">Wstępnie generuje kod serializacji C# dla typów w aplikacji klienckiej, które są używane przez Kontrakt serwisowy WCF i które mogą być serializowane przez XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="22669-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="22669-106">Zwiększa to wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów.</span><span class="sxs-lookup"><span data-stu-id="22669-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22669-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="22669-107">Prerequisites</span></span>

* <span data-ttu-id="22669-108">[Sdk .NET Core 2.1](https://dotnet.microsoft.com/download) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="22669-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="22669-109">Twój ulubiony edytor kodu</span><span class="sxs-lookup"><span data-stu-id="22669-109">Your favorite code editor</span></span>

<span data-ttu-id="22669-110">Za pomocą polecenia `dotnet --info` można sprawdzić, które wersje programu .NET Core SDK i czas uruchomieniowy zostały już zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="22669-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="22669-111">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="22669-111">Getting started</span></span>

<span data-ttu-id="22669-112">Aby `dotnet-svcutil.xmlserializer` użyć w aplikacji konsoli .NET Core:</span><span class="sxs-lookup"><span data-stu-id="22669-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="22669-113">Utwórz usługę WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "WCF Service Application" w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22669-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="22669-114">Dodaj `[XmlSerializerFormat]` atrybut do metody usługi, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="22669-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="22669-115">Utwórz aplikację konsoli .NET Core jako aplikację kliencką WCF, która jest przeznaczona dla wersji .NET Core 2.1 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="22669-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="22669-116">Na przykład utwórz aplikację o nazwie "MyWCFClient" za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="22669-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="22669-117">Aby upewnić się, że projekt jest przeznaczony dla `TargetFramework` programu .NET Core 2.1 lub nowszego, sprawdź element XML w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="22669-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="22669-118">Dodaj odwołanie do `System.ServiceModel.Http` pakietu, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="22669-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="22669-119">Dodaj kod klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="22669-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="22669-120">Dodaj odwołanie do `dotnet-svcutil.xmlserializer` pakietu, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="22669-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="22669-121">Uruchomienie polecenia powinno dodać wpis do pliku projektu podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="22669-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="22669-122">Tworzenie aplikacji przez `dotnet build`uruchomienie .</span><span class="sxs-lookup"><span data-stu-id="22669-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="22669-123">Jeśli wszystko się powiedzie, w folderze wyjściowym generowany jest zestaw o nazwie *MyWCFClient.XmlSerializers.dll.*</span><span class="sxs-lookup"><span data-stu-id="22669-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="22669-124">Jeśli narzędzie nie może wygenerować zestawu, zobaczysz ostrzeżenia w danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="22669-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="22669-125">Uruchom usługę WCF, na przykład `http://localhost:2561/Service1.svc` działając w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="22669-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="22669-126">Następnie uruchom aplikację kliencką i automatycznie załaduje i użyje wstępnie wygenerowanych serializatorów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="22669-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
