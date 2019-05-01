---
title: Omówienie narzędzia svcutil WCF
description: Omówienie narzędzia dotnet svcutil Microsoft WCF, który dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobny do narzędzia svcutil WCF dla projektów programu .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 665958bf4b36154f05d9f35f235b45c62f07973c
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63773940"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="5e8f2-103">Narzędzia dotnet svcutil WCF dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e8f2-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="5e8f2-104">Windows Communication Foundation (WCF) **narzędzia svcutil dotnet** narzędzie to narzędzie wiersza polecenia platformy .NET Core, pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, która generuje klasę usługi WCF, zawierająca metody serwera proxy klienta, dostęp do operacji usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="5e8f2-105">Podobnie jak [ **metadanych modelu usługi - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia dla projektów programu .NET Framework **narzędzia svcutil dotnet** jest narzędziem wiersza polecenia do generowania odwołanie do usługi sieci web zgodne z projektami .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="5e8f2-106">**Narzędzia svcutil dotnet** narzędzie jest alternatywnych opcji [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) dostawcy usług, które po raz pierwszy wysłane połączona programu Visual Studio z programem Visual Studio v15.5 2017 r.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="5e8f2-107">**Narzędzia svcutil dotnet** narzędzia jako narzędzie wiersza polecenia platformy .NET Core, są dostępne dla wielu platform w systemie Linux, macOS i Windows.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e8f2-108">Użytkownik powinien odwoływać się tylko do usług z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="5e8f2-109">Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e8f2-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5e8f2-110">Prerequisites</span></span>

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="5e8f2-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="5e8f2-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)
* <span data-ttu-id="5e8f2-112">[Zestaw SDK programu .NET core 2.1](https://dotnet.microsoft.com/download) lub nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="5e8f2-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="5e8f2-113">Wybrany edytor kodu</span><span class="sxs-lookup"><span data-stu-id="5e8f2-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="5e8f2-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="5e8f2-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
* <span data-ttu-id="5e8f2-115">[.NET core 1.0.4 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="5e8f2-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="5e8f2-116">Wybrany edytor kodu</span><span class="sxs-lookup"><span data-stu-id="5e8f2-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="5e8f2-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="5e8f2-117">Getting started</span></span>

<span data-ttu-id="5e8f2-118">Poniższy przykład przeprowadzi Cię przez kroki wymagane do Dodaj odwołanie do usługi sieci web do projektu sieci web platformy .NET Core i wywołać usługę.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="5e8f2-119">Utworzysz aplikację sieci web platformy .NET Core, o nazwie _HelloSvcutil_ i Dodaj odwołanie do usługi sieci web, który implementuje ten kontrakt następujące:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-119">You'll create a .NET Core web application named _HelloSvcutil_ and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="5e8f2-120">W tym przykładzie załóżmy, że będzie hostowana usługa sieci web, korzystając z następującego adresu: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="5e8f2-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="5e8f2-121">Z poziomu okna polecenia Windows, macOS lub Linux, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="5e8f2-122">Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i udostępnić go w bieżącym katalogu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="5e8f2-123">Utwórz nową C# projektu sieci web w tym katalogu przy użyciu [ `dotnet new` ](../tools/dotnet-new.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```console
    dotnet new web
    ```

3. <span data-ttu-id="5e8f2-124">Zainstaluj [ `dotnet-svcutil` pakietu NuGet](https://nuget.org/packages/dotnet-svcutil) jako narzędzie interfejsu wiersza polecenia:  </span><span class="sxs-lookup"><span data-stu-id="5e8f2-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="5e8f2-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="5e8f2-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

        ```console
        dotnet tool install --global dotnet-svcutil
        ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="5e8f2-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="5e8f2-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="5e8f2-127">Otwórz `HelloSvcutil.csproj` projektu plik w edytorze, Edytuj `Project` element i Dodaj [ `dotnet-svcutil` pakietu NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie narzędzie interfejsu wiersza polecenia, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="5e8f2-128">Następnie Przywróć _narzędzia svcutil dotnet_ pakietu przy użyciu [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

    ---

4. <span data-ttu-id="5e8f2-129">Uruchom _narzędzia svcutil dotnet_ polecenie, aby wygenerować plik odwołanie do usługi sieci web w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="5e8f2-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="5e8f2-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="5e8f2-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="5e8f2-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```console
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="5e8f2-132">Wygenerowany plik jest zapisywany jako _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="5e8f2-133">_Narzędzia svcutil dotnet_ narzędzie automatycznie dodaje również do projektu odpowiednich pakietów WCF wymagane przez kod serwera proxy jako odwołania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="5e8f2-134">Za pomocą odwołania do usługi</span><span class="sxs-lookup"><span data-stu-id="5e8f2-134">Using the Service Reference</span></span>

1. <span data-ttu-id="5e8f2-135">Przywróć pakiety programu WCF za pomocą [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

2. <span data-ttu-id="5e8f2-136">Znajdź nazwę klienta, klasy i operacji, które chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="5e8f2-137">`Reference.cs` zawiera klasy, która dziedziczy `System.ServiceModel.ClientBase`, za pomocą metod, które mogą służyć do wywoływania operacji w usłudze.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="5e8f2-138">W tym przykładzie, który chcesz wybrać _SayHello_ usługi _Hello_ operacji.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="5e8f2-139">`ServiceReference.SayHelloClient` jest nazwą Klasa klienta i metody o nazwie `HelloAsync` można wywołać operację.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="5e8f2-140">Otwórz `Startup.cs` plik w edytorze i Dodaj instrukcję using instrukcji dla przestrzeni nazw odwołań usługi u góry:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="5e8f2-141">Edytuj `Configure` metody do wywołania usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="5e8f2-142">Możesz to zrobić przez utworzenie wystąpienia klasy, która dziedziczy `ClientBase` i wywołanie metody w obiekcie klienta:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IHostingEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. <span data-ttu-id="5e8f2-143">Uruchamianie aplikacji przy użyciu [ `dotnet run` ](../tools/dotnet-run.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```console
    dotnet run
    ```

6. <span data-ttu-id="5e8f2-144">Przejdź do adresu URL podanego w konsoli (na przykład `http://localhost:5000`) w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="5e8f2-145">Powinny zostać wyświetlone następujące dane wyjściowe: "Hello dotnet-svcutil /!"</span><span class="sxs-lookup"><span data-stu-id="5e8f2-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="5e8f2-146">Aby uzyskać szczegółowy opis `dotnet-svcutil` narzędzia parametrów, wywołaj narzędzie przekazywania parametru pomocy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e8f2-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="5e8f2-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="5e8f2-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="5e8f2-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="5e8f2-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="5e8f2-149">Opinie i pytania</span><span class="sxs-lookup"><span data-stu-id="5e8f2-149">Feedback & questions</span></span>

<span data-ttu-id="5e8f2-150">Jeśli masz pytania lub opinie, [Otwórz problem w serwisie GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="5e8f2-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="5e8f2-151">Możesz również sprawdzić wszelkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="5e8f2-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="5e8f2-152">Uwagi do wersji</span><span class="sxs-lookup"><span data-stu-id="5e8f2-152">Release notes</span></span>

* <span data-ttu-id="5e8f2-153">Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="5e8f2-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="5e8f2-154">Informacje</span><span class="sxs-lookup"><span data-stu-id="5e8f2-154">Information</span></span>

* [<span data-ttu-id="5e8f2-155">Pakiet NuGet narzędzia svcutil DotNet</span><span class="sxs-lookup"><span data-stu-id="5e8f2-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
