---
title: Tworzenie nowego ASP.NET Core gRPC Project — gRPC dla deweloperów WCF
description: Dowiedz się, jak utworzyć projekt gRPC za pomocą programu Visual Studio lub z wiersza polecenia.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a30d19e1e48692ad68a648406d4bf369937744d7
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846711"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="4f00a-103">Tworzenie nowego projektu usługi gRPC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4f00a-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="4f00a-104">Platforma .NET Core udostępnia zaawansowane narzędzie interfejsu wiersza polecenia, `dotnet`, co umożliwia tworzenie projektów i rozwiązań oraz zarządzanie nimi z poziomu wiersza poleceń.</span><span class="sxs-lookup"><span data-stu-id="4f00a-104">.NET Core comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="4f00a-105">Narzędzie jest ściśle zintegrowane z programem Visual Studio, więc wszystko jest również dostępne za pomocą interfejsu znanego graficznego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4f00a-105">The tool is closely integrated with Visual Studio, so everything is also available through the familiar GUI interface.</span></span> <span data-ttu-id="4f00a-106">W tym rozdziale przedstawiono dwa sposoby tworzenia nowego projektu ASP.NET Core gRPC: najpierw z programem Visual Studio, a następnie z interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4f00a-106">This chapter will show both ways to create a new ASP.NET Core gRPC project: first with Visual Studio, then with the .NET Core CLI.</span></span>

## <a name="create-the-project-using-visual-studio"></a><span data-ttu-id="4f00a-107">Tworzenie projektu przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4f00a-107">Create the project using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f00a-108">Do opracowania dowolnej aplikacji ASP.NET Core 3,0 wymagany jest program Visual Studio 2019,3 lub nowszy z zainstalowanym obciążeniem programu **ASP.NET i sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="4f00a-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019.3 or later with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="4f00a-109">Utwórz puste rozwiązanie o nazwie **TraderSys** z *pustego szablonu rozwiązania* .</span><span class="sxs-lookup"><span data-stu-id="4f00a-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="4f00a-110">Dodaj folder rozwiązania o nazwie `src`, a następnie kliknij prawym przyciskiem myszy folder i wybierz polecenie **dodaj** > **Nowy projekt** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="4f00a-110">Add a Solution Folder called `src`, then right-click on the folder and choose **Add** > **New Project** from the context menu.</span></span> <span data-ttu-id="4f00a-111">Wprowadź `grpc` w polu wyszukiwania szablonu i powinien zostać wyświetlony szablon projektu o nazwie `gRPC Service`.</span><span class="sxs-lookup"><span data-stu-id="4f00a-111">Enter `grpc` in the template search box and you should see a project template called `gRPC Service`.</span></span>

![Okno dialogowe Dodawanie nowego projektu przedstawiające szablon projektu usługi gRPC Service](media/create-project/new-grpc-project.png)

<span data-ttu-id="4f00a-113">Kliknij przycisk **dalej** , aby przejść do okna dialogowego **Konfigurowanie projektu** i nazwij projekt `TraderSys.Portfolios`, a następnie Dodaj `src` podkatalog do **lokalizacji**.</span><span class="sxs-lookup"><span data-stu-id="4f00a-113">Click **Next** to continue to the **Configure project** dialog and name the project `TraderSys.Portfolios`, and add an `src` subdirectory to the **Location**.</span></span>

![Okno dialogowe Konfigurowanie projektu](media/create-project/configure-project.png)

<span data-ttu-id="4f00a-115">Kliknij przycisk **dalej** , aby przejść do okna dialogowego **Nowy projekt gRPC** .</span><span class="sxs-lookup"><span data-stu-id="4f00a-115">Click **Next** to continue to the **New gRPC project** dialog.</span></span>

![Nowe okno dialogowe projektu gRPC](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="4f00a-117">Obecnie dostępne są ograniczone opcje tworzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="4f00a-117">At present, there are limited options for the service creation.</span></span> <span data-ttu-id="4f00a-118">Platforma Docker zostanie wprowadzona w dalszej części książki, więc pozostaw pole wyboru niezaznaczone teraz, a po prostu kliknij pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="4f00a-118">Docker will be introduced later in the book, so leave that checkbox unchecked for now and just click **Create**.</span></span> <span data-ttu-id="4f00a-119">Pierwszy ASP.NET Core 3,0 gRPC projektu jest generowany i dodawany do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4f00a-119">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="4f00a-120">Jeśli nie chcesz wiedzieć o pracy z `dotnet CLI`, przejdź do sekcji [czyszczenie przykładowego kodu](#clean-up-the-example-code) .</span><span class="sxs-lookup"><span data-stu-id="4f00a-120">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-using-the-net-core-cli"></a><span data-ttu-id="4f00a-121">Tworzenie projektu przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="4f00a-121">Create the project using the .NET Core CLI</span></span>

<span data-ttu-id="4f00a-122">Ta sekcja obejmuje tworzenie rozwiązań i projektów z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4f00a-122">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="4f00a-123">Utwórz rozwiązanie, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="4f00a-123">Create the solution as shown below.</span></span> <span data-ttu-id="4f00a-124">Flaga `-o` (lub `--output`) określa katalog wyjściowy, który zostanie utworzony w bieżącym katalogu, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="4f00a-124">The `-o` (or `--output`) flag specifies the output directory, which will be created in the current directory if it does not exist.</span></span> <span data-ttu-id="4f00a-125">Rozwiązanie będzie miało taką samą nazwę jak katalog, czyli `TraderSys.sln`. Możesz podać inną nazwę przy użyciu flagi `-n` (lub `--name`).</span><span class="sxs-lookup"><span data-stu-id="4f00a-125">The solution will be given the same name as the directory, i.e. `TraderSys.sln`. You can provide a different name using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="4f00a-126">ASP.NET Core 3,0 jest dostarczany z szablonem interfejsu wiersza polecenia dla usług gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="4f00a-126">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="4f00a-127">Utwórz nowy projekt przy użyciu tego szablonu, umieszczając go w podkatalogu `src` zgodnie z Konwencją dla ASP.NET Core projektów.</span><span class="sxs-lookup"><span data-stu-id="4f00a-127">Create the new project using this template, putting it into an `src` subdirectory as is the convention for ASP.NET Core projects.</span></span> <span data-ttu-id="4f00a-128">Projekt zostanie nazwany po katalogu (tj. `TraderSys.Portfolios.csproj`), chyba że zostanie określona inna nazwa z flagą `-n`.</span><span class="sxs-lookup"><span data-stu-id="4f00a-128">The project will be named after the directory (i.e. `TraderSys.Portfolios.csproj`) unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="4f00a-129">Na koniec Dodaj projekt do rozwiązania przy użyciu polecenia `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="4f00a-129">Finally, add the project to the solution using the `dotnet sln` command.</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="4f00a-130">Ponieważ dany katalog zawiera tylko jeden plik `.csproj`, można w dalszym ciągu określić katalog, który ma zostać zapisany.</span><span class="sxs-lookup"><span data-stu-id="4f00a-130">Since the given directory only contains a single `.csproj` file, you can get away with specifying just the directory to save typing.</span></span>

<span data-ttu-id="4f00a-131">Teraz możesz otworzyć to rozwiązanie w programie Visual Studio 2019, Visual Studio Code lub dowolnym wybranym przez Ciebie edytorze.</span><span class="sxs-lookup"><span data-stu-id="4f00a-131">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="4f00a-132">Czyszczenie przykładowego kodu</span><span class="sxs-lookup"><span data-stu-id="4f00a-132">Clean up the example code</span></span>

<span data-ttu-id="4f00a-133">Przykładowa usługa została utworzona przy użyciu szablonu gRPC, który został wcześniej sprawdzony w książce.</span><span class="sxs-lookup"><span data-stu-id="4f00a-133">You've now created an example service using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="4f00a-134">Nie jest to przydatne w naszym kontekście transakcji giełdowych, dlatego będziemy edytować rzeczy dla pierwszego projektu.</span><span class="sxs-lookup"><span data-stu-id="4f00a-134">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="4f00a-135">Zmiana nazwy i edytowanie pliku proto</span><span class="sxs-lookup"><span data-stu-id="4f00a-135">Rename and edit the proto file</span></span>

<span data-ttu-id="4f00a-136">Przejdź dalej i Zmień nazwę pliku `Protos/greet.proto` na `Protos/portfolios.proto` i otwórz go w edytorze.</span><span class="sxs-lookup"><span data-stu-id="4f00a-136">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto` and open it in your editor.</span></span> <span data-ttu-id="4f00a-137">Usuń wszystko po wierszu `package`, a następnie zmień nazwy `option csharp_namespace`, `package` i `service`, a następnie usuń domyślną usługę `SayHello`, aby kod wyglądał następująco.</span><span class="sxs-lookup"><span data-stu-id="4f00a-137">Delete everything after the `package` line, then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service, so the code looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="4f00a-138">Szablon nie dodaje domyślnie części przestrzeni nazw `Protos`, ale dodanie go ułatwia zachowanie klas generowanych przez gRPC i własnych klas, które są wyraźnie oddzielone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4f00a-138">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="4f00a-139">Jeśli zmienisz nazwę pliku `greet.proto` w zintegrowanym środowisku programistycznym (IDE), takim jak Visual Studio, odwołanie do tego pliku jest automatycznie aktualizowane w pliku `.csproj`.</span><span class="sxs-lookup"><span data-stu-id="4f00a-139">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="4f00a-140">Jednak w innym edytorze, takim jak Visual Studio Code, odwołanie nie jest aktualizowane automatycznie, dlatego należy ręcznie edytować plik projektu.</span><span class="sxs-lookup"><span data-stu-id="4f00a-140">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="4f00a-141">W obiektach docelowych kompilacji gRPC istnieje element `Protobuf` elementu, który pozwala określić, które pliki `.proto` mają być kompilowane, i które formy generowania kodu są wymagane (czyli "serwer" lub "klient").</span><span class="sxs-lookup"><span data-stu-id="4f00a-141">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="4f00a-142">Zmień nazwę klasy GreeterService</span><span class="sxs-lookup"><span data-stu-id="4f00a-142">Rename the GreeterService class</span></span>

<span data-ttu-id="4f00a-143">Klasa `GreeterService` znajduje się w folderze `Services` i dziedziczy po `Greeter.GreeterBase`.</span><span class="sxs-lookup"><span data-stu-id="4f00a-143">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="4f00a-144">Zmień jej nazwę na `PortfolioService` i Zmień klasę bazową, aby `Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="4f00a-144">Rename it to `PortfolioService` and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="4f00a-145">Usuń metody `override`.</span><span class="sxs-lookup"><span data-stu-id="4f00a-145">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="4f00a-146">Istnieje odwołanie do klasy `GreeterService` w metodzie `Configure` w klasie `Startup`.</span><span class="sxs-lookup"><span data-stu-id="4f00a-146">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="4f00a-147">Jeśli użyto refaktoryzacji do zmiany nazwy klasy, to odwołanie powinno zostać zaktualizowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4f00a-147">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="4f00a-148">Niemniej jednak, jeśli nie, musisz edytować ją ręcznie.</span><span class="sxs-lookup"><span data-stu-id="4f00a-148">However, if you didn't, you need to edit it manually.</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="4f00a-149">W następnej sekcji dodamy funkcjonalność do tej nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="4f00a-149">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4f00a-150">[Poprzedni](migrate-wcf-to-grpc.md)
>[Następny](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="4f00a-150">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
