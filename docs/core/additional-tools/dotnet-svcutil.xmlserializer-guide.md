---
title: Za pomocą polecenia dotnet svcutil.xmlserializer na platformie .NET Core
description: Dowiedz się, jak można użyć `dotnet-svcutil.xmlserializer` pakietu NuGet można wstępnie wygenerować zestawu serializacji dla projektów .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: f5ffed47079a3ee122c7784d0c61c4d40461ba26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638986"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="8e76c-103">Za pomocą polecenia dotnet svcutil.xmlserializer na platformie .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e76c-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="8e76c-104">`dotnet-svcutil.xmlserializer` Pakietu NuGet można wstępnie wygenerować zestawu serializacji dla projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e76c-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="8e76c-105">Wstępnie generuje C# kodu serializacji dla typów w aplikacji klienckiej, które są używane przez kontraktu usługi WCF i może być serializowany przez obiekt XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="8e76c-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="8e76c-106">Zwiększa to wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów z tych typów.</span><span class="sxs-lookup"><span data-stu-id="8e76c-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8e76c-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8e76c-107">Prerequisites</span></span>

* <span data-ttu-id="8e76c-108">[Zestaw SDK programu .NET core 2.1](https://www.microsoft.com/net/download) lub nowszej</span><span class="sxs-lookup"><span data-stu-id="8e76c-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later</span></span>
* <span data-ttu-id="8e76c-109">Wybrany edytor kodu</span><span class="sxs-lookup"><span data-stu-id="8e76c-109">Your favorite code editor</span></span>

<span data-ttu-id="8e76c-110">Możesz użyć polecenia `dotnet --info` do sprawdzenia, które wersje programu .NET Core SDK i środowiska uruchomieniowego została już zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="8e76c-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="8e76c-111">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8e76c-111">Getting started</span></span>

<span data-ttu-id="8e76c-112">Aby użyć `dotnet-svcutil.xmlserializer` platformie .NET Core konsoli aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8e76c-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="8e76c-113">Tworzenie usługi WCF o nazwie "MyWCFService" przy użyciu domyślnego szablonu "Aplikacja usługi WCF" w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e76c-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="8e76c-114">Dodaj `[XmlSerializerFormat]` atrybutu metody usługi, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="8e76c-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="8e76c-115">Tworzenie aplikacji konsolowej .NET Core, jako aplikacja klienta WCF przeznaczonego na platformy .NET Core 2.1 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="8e76c-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="8e76c-116">Na przykład utworzyć aplikację o nazwie "MyWCFClient" za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="8e76c-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```console
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="8e76c-117">Aby upewnić się, projekt jest przeznaczony dla platformy .NET Core 2.1 lub nowszej, zbadaj `TargetFramework` — element XML w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="8e76c-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="8e76c-118">Dodaj odwołanie do pakietu `System.ServiceModel.Http` , uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="8e76c-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```console
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="8e76c-119">Dodaj kod klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="8e76c-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="8e76c-120">Dodaj odwołanie do `dotnet-svcutil.xmlserializer` pakietu, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="8e76c-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="8e76c-121">Uruchomienie polecenia należy dodać wpis do pliku projektu podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="8e76c-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="8e76c-122">Kompiluj aplikację, uruchamiając `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="8e76c-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="8e76c-123">Jeśli wszystko, co zakończy się powodzeniem, zestaw o nazwie *MyWCFClient.XmlSerializers.dll* jest generowany w folderze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="8e76c-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="8e76c-124">Jeśli narzędzie nie można wygenerować zestawu, zostanie wyświetlone ostrzeżenia w danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8e76c-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="8e76c-125">Uruchom usługę WCF, na przykład `http://localhost:2561/Service1.svc` w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="8e76c-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="8e76c-126">Następnie uruchom aplikację klienta, a także będą automatycznie załadować i użyć wstępnie wygenerowanego serializatory w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8e76c-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>