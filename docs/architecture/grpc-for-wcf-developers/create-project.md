---
title: Tworzenie nowego ASP.NET Core gRPC Project — gRPC dla deweloperów WCF
description: Dowiedz się, jak utworzyć projekt gRPC za pomocą programu Visual Studio lub wiersza polecenia.
ms.date: 09/02/2019
ms.openlocfilehash: ea6d7658404f61fedb25d7de7ddedb7c51437383
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711447"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="67ac6-103">Tworzenie nowego projektu usługi gRPC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67ac6-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="67ac6-104">Zestaw .NET Core SDK udostępnia zaawansowane narzędzie interfejsu wiersza polecenia, `dotnet`, które umożliwia tworzenie projektów i rozwiązań oraz zarządzanie nimi z poziomu wiersza poleceń.</span><span class="sxs-lookup"><span data-stu-id="67ac6-104">The .NET Core SDK comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="67ac6-105">Zestaw SDK jest ściśle zintegrowany z programem Visual Studio, więc wszystko jest również dostępne za pomocą znanego graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="67ac6-105">The SDK is closely integrated with Visual Studio, so everything is also available through the familiar graphical user interface.</span></span> <span data-ttu-id="67ac6-106">W tym rozdziale przedstawiono obie metody tworzenia nowego projektu ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="67ac6-106">This chapter shows both ways to create a new ASP.NET Core gRPC project.</span></span>

## <a name="create-the-project-by-using-visual-studio"></a><span data-ttu-id="67ac6-107">Tworzenie projektu przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67ac6-107">Create the project by using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67ac6-108">Do opracowania dowolnej aplikacji ASP.NET Core 3,0 wymagany jest program Visual Studio 2019 16,3 lub nowszy z zainstalowanym obciążeniem **programowanie ASP.NET i sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="67ac6-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019 16.3 or later, with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="67ac6-109">Utwórz puste rozwiązanie o nazwie **TraderSys** z *pustego szablonu rozwiązania* .</span><span class="sxs-lookup"><span data-stu-id="67ac6-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="67ac6-110">Dodaj folder rozwiązania o nazwie `src`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-110">Add a solution folder called `src`.</span></span> <span data-ttu-id="67ac6-111">Następnie kliknij prawym przyciskiem myszy folder, a następnie wybierz polecenie **dodaj** > **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="67ac6-111">Then, right-click on the folder and choose **Add** > **New Project**.</span></span> <span data-ttu-id="67ac6-112">Wprowadź `grpc` w polu wyszukiwania szablonu i powinien zostać wyświetlony szablon projektu o nazwie `gRPC Service`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-112">Enter `grpc` in the template search box, and you should see a project template called `gRPC Service`.</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie nowego projektu](media/create-project/new-grpc-project.png)

<span data-ttu-id="67ac6-114">Wybierz pozycję **dalej** , aby przejść do okna dialogowego **Konfigurowanie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="67ac6-114">Select **Next** to continue to the **Configure your new project** dialog box.</span></span> <span data-ttu-id="67ac6-115">Nadaj projektowi nazwę `TraderSys.Portfolios`i Dodaj `src` podkatalogu do **lokalizacji**.</span><span class="sxs-lookup"><span data-stu-id="67ac6-115">Name the project `TraderSys.Portfolios`, and add an `src` subdirectory to the **Location**.</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Konfigurowanie nowego projektu](media/create-project/configure-project.png)

<span data-ttu-id="67ac6-117">Wybierz pozycję **dalej** , aby przejść do okna dialogowego **Tworzenie nowej usługi gRPC** .</span><span class="sxs-lookup"><span data-stu-id="67ac6-117">Select **Next** to continue to the **Create a new gRPC service** dialog box.</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie nowej usługi gRPC](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="67ac6-119">W tej chwili masz ograniczoną liczbę opcji tworzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="67ac6-119">At present, you have limited options for the service creation.</span></span> <span data-ttu-id="67ac6-120">Platforma Docker zostanie wprowadzona później, dlatego nie należy zaznaczać tej opcji.</span><span class="sxs-lookup"><span data-stu-id="67ac6-120">Docker will be introduced later, so for now, leave that option unselected.</span></span> <span data-ttu-id="67ac6-121">Po prostu wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="67ac6-121">Just select **Create**.</span></span> <span data-ttu-id="67ac6-122">Pierwszy ASP.NET Core 3,0 gRPC projektu jest generowany i dodawany do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="67ac6-122">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="67ac6-123">Jeśli nie chcesz wiedzieć o pracy z `dotnet CLI`, przejdź do sekcji [czyszczenie przykładowego kodu](#clean-up-the-example-code) .</span><span class="sxs-lookup"><span data-stu-id="67ac6-123">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-by-using-the-net-core-cli"></a><span data-ttu-id="67ac6-124">Tworzenie projektu przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="67ac6-124">Create the project by using the .NET Core CLI</span></span>

<span data-ttu-id="67ac6-125">Ta sekcja obejmuje tworzenie rozwiązań i projektów z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="67ac6-125">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="67ac6-126">Utwórz rozwiązanie, jak pokazano w poniższym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="67ac6-126">Create the solution as shown in the following command.</span></span> <span data-ttu-id="67ac6-127">Flaga `-o` (lub `--output`) określa katalog wyjściowy, który jest tworzony w bieżącym katalogu, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="67ac6-127">The `-o` (or `--output`) flag specifies the output directory, which is created in the current directory if it doesn't already exist.</span></span> <span data-ttu-id="67ac6-128">Rozwiązanie ma taką samą nazwę jak katalog: `TraderSys.sln`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-128">The solution has the same name as the directory: `TraderSys.sln`.</span></span> <span data-ttu-id="67ac6-129">Można podać inną nazwę przy użyciu flagi `-n` (lub `--name`).</span><span class="sxs-lookup"><span data-stu-id="67ac6-129">You can provide a different name by using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="67ac6-130">ASP.NET Core 3,0 jest dostarczany z szablonem interfejsu wiersza polecenia dla usług gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="67ac6-130">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="67ac6-131">Utwórz nowy projekt przy użyciu tego szablonu, umieszczając go w podkatalogu `src`, co jest konwencjonalne dla ASP.NET Core projektów.</span><span class="sxs-lookup"><span data-stu-id="67ac6-131">Create the new project by using this template, putting it into an `src` subdirectory as is conventional for ASP.NET Core projects.</span></span> <span data-ttu-id="67ac6-132">Projekt nosi nazwę po katalogu (`TraderSys.Portfolios.csproj`), chyba że zostanie określona inna nazwa z flagą `-n`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-132">The project is named after the directory (`TraderSys.Portfolios.csproj`), unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="67ac6-133">Na koniec Dodaj projekt do rozwiązania przy użyciu polecenia `dotnet sln`:</span><span class="sxs-lookup"><span data-stu-id="67ac6-133">Finally, add the project to the solution by using the `dotnet sln` command:</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="67ac6-134">Ponieważ konkretny katalog zawiera tylko jeden plik `.csproj`, można określić tylko katalog, aby zapisać tekst.</span><span class="sxs-lookup"><span data-stu-id="67ac6-134">Because the particular directory only contains a single `.csproj` file, you can specify just the directory, to save typing.</span></span>

<span data-ttu-id="67ac6-135">Teraz możesz otworzyć to rozwiązanie w programie Visual Studio 2019, Visual Studio Code lub dowolnym wybranym przez Ciebie edytorze.</span><span class="sxs-lookup"><span data-stu-id="67ac6-135">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="67ac6-136">Czyszczenie przykładowego kodu</span><span class="sxs-lookup"><span data-stu-id="67ac6-136">Clean up the example code</span></span>

<span data-ttu-id="67ac6-137">Przykładowa usługa została utworzona przy użyciu szablonu gRPC, który został wcześniej sprawdzony w książce.</span><span class="sxs-lookup"><span data-stu-id="67ac6-137">You've now created an example service by using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="67ac6-138">Nie jest to przydatne w naszym kontekście transakcji giełdowych, dlatego będziemy edytować rzeczy dla pierwszego projektu.</span><span class="sxs-lookup"><span data-stu-id="67ac6-138">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="67ac6-139">Zmiana nazwy i edytowanie pliku proto</span><span class="sxs-lookup"><span data-stu-id="67ac6-139">Rename and edit the proto file</span></span>

<span data-ttu-id="67ac6-140">Przejdź dalej i Zmień nazwę pliku `Protos/greet.proto` na `Protos/portfolios.proto`i otwórz go w edytorze.</span><span class="sxs-lookup"><span data-stu-id="67ac6-140">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto`, and open it in your editor.</span></span> <span data-ttu-id="67ac6-141">Usuń wszystko po wierszu `package`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-141">Delete everything after the `package` line.</span></span> <span data-ttu-id="67ac6-142">Następnie zmień nazwy `option csharp_namespace`, `package` i `service` i usuń domyślną usługę `SayHello`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-142">Then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service.</span></span> <span data-ttu-id="67ac6-143">Kod wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="67ac6-143">The code now looks like the following:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="67ac6-144">Szablon nie dodaje domyślnie części przestrzeni nazw `Protos`, ale dodanie go ułatwia zachowanie klas generowanych przez gRPC i własnych klas, które są wyraźnie oddzielone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="67ac6-144">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="67ac6-145">Jeśli zmienisz nazwę pliku `greet.proto` w zintegrowanym środowisku programistycznym (IDE), takim jak Visual Studio, odwołanie do tego pliku jest automatycznie aktualizowane w pliku `.csproj`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-145">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="67ac6-146">Jednak w innym edytorze, takim jak Visual Studio Code, odwołanie nie jest aktualizowane automatycznie, dlatego należy ręcznie edytować plik projektu.</span><span class="sxs-lookup"><span data-stu-id="67ac6-146">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="67ac6-147">W obiektach docelowych kompilacji gRPC istnieje element elementu `Protobuf`, który pozwala określić, które pliki `.proto` mają być kompilowane, i które formy generowania kodu są wymagane (czyli "serwer" lub "klient").</span><span class="sxs-lookup"><span data-stu-id="67ac6-147">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled, and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="67ac6-148">Zmień nazwę klasy `GreeterService`</span><span class="sxs-lookup"><span data-stu-id="67ac6-148">Rename the `GreeterService` class</span></span>

<span data-ttu-id="67ac6-149">Klasa `GreeterService` znajduje się w folderze `Services` i dziedziczy po `Greeter.GreeterBase`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-149">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="67ac6-150">Zmień nazwę na `PortfolioService`i Zmień klasę bazową, aby `Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-150">Rename it to `PortfolioService`, and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="67ac6-151">Usuń metody `override`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-151">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="67ac6-152">Istnieje odwołanie do klasy `GreeterService` w metodzie `Configure` w klasie `Startup`.</span><span class="sxs-lookup"><span data-stu-id="67ac6-152">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="67ac6-153">Jeśli użyto refaktoryzacji do zmiany nazwy klasy, to odwołanie powinno zostać zaktualizowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="67ac6-153">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="67ac6-154">Niemniej jednak, jeśli nie, musisz edytować ją ręcznie.</span><span class="sxs-lookup"><span data-stu-id="67ac6-154">However, if you didn't, you need to edit it manually.</span></span>

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

<span data-ttu-id="67ac6-155">W następnej sekcji dodamy funkcjonalność do tej nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="67ac6-155">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="67ac6-156">[Poprzednie](migrate-wcf-to-grpc.md)
>[dalej](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="67ac6-156">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
