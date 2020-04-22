---
title: Przegląd narzędzi WCF svcutil
description: Omówienie narzędzia Microsoft WCF dotnet-svcutil, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobne do narzędzia Svcutil WCF dla projektów .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 1f500c9355112183a135c2b639807c7cd62fbbfc
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021253"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="72f6e-103">Narzędzie WCF dotnet-svcutil dla .NET Core</span><span class="sxs-lookup"><span data-stu-id="72f6e-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="72f6e-104">Narzędzie **dotnet-svcutil** programu Windows Communication Foundation (WCF) to narzędzie .NET, które pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL i generuje klasę WCF zawierającą metody proxy klienta, które uzyskują dostęp do operacji usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="72f6e-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="72f6e-105">Podobnie jak w przypadku [**narzędzia Metadane modelu usługi — svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dla projektów .NET Framework, **dotnet-svcutil** jest narzędziem wiersza polecenia do generowania odwołania do usługi sieci web zgodnej z projektami .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="72f6e-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="72f6e-106">Narzędzie **dotnet-svcutil** jest alternatywną opcją dla dostawcy usług połączonych w programie [**Visual Studio,**](wcf-web-service-reference-guide.md) który po raz pierwszy został dostarczony z programem Visual Studio 2017 w wersji 15.5.</span><span class="sxs-lookup"><span data-stu-id="72f6e-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="72f6e-107">Narzędzie **dotnet-svcutil** jako narzędzie .NET jest dostępne na wielu platformach w systemach Linux, macOS i Windows.</span><span class="sxs-lookup"><span data-stu-id="72f6e-107">The **dotnet-svcutil** tool as a .NET tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72f6e-108">Należy odwoływać się tylko do usług z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="72f6e-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="72f6e-109">Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="72f6e-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72f6e-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="72f6e-110">Prerequisites</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="72f6e-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="72f6e-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

- <span data-ttu-id="72f6e-112">[Plik SDK programu .NET Core 2.1](https://dotnet.microsoft.com/download) lub nowszych</span><span class="sxs-lookup"><span data-stu-id="72f6e-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="72f6e-113">Twój ulubiony edytor kodu</span><span class="sxs-lookup"><span data-stu-id="72f6e-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="72f6e-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="72f6e-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

- <span data-ttu-id="72f6e-115">[Plik SDK programu .NET Core 1.0.4](https://dotnet.microsoft.com/download) lub nowszych</span><span class="sxs-lookup"><span data-stu-id="72f6e-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="72f6e-116">Twój ulubiony edytor kodu</span><span class="sxs-lookup"><span data-stu-id="72f6e-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="72f6e-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="72f6e-117">Getting started</span></span>

<span data-ttu-id="72f6e-118">W poniższym przykładzie przedstawiono kroki wymagane do dodania odwołania do usługi sieci web do projektu sieci web .NET Core i wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="72f6e-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="72f6e-119">Utworzysz aplikację sieci web .NET Core o nazwie *HelloSvcutil* i dodasz odwołanie do usługi sieci web, która implementuje następującą umowę:</span><span class="sxs-lookup"><span data-stu-id="72f6e-119">You'll create a .NET Core web application named *HelloSvcutil* and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="72f6e-120">W tym przykładzie załóżmy, że usługa sieci web będzie hostowana pod następującym adresem:`http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="72f6e-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="72f6e-121">Z okna polecenia systemu Windows, macOS lub Linux wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="72f6e-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="72f6e-122">Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i uczynić go bieżącym katalogiem, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="72f6e-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="72f6e-123">Utwórz nowy projekt sieci Web języka [`dotnet new`](../tools/dotnet-new.md) C# w tym katalogu za pomocą polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72f6e-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```dotnetcli
    dotnet new web
    ```

3. <span data-ttu-id="72f6e-124">Zainstaluj [ `dotnet-svcutil` pakiet NuGet](https://nuget.org/packages/dotnet-svcutil) jako narzędzie interfejsu wiersza polecenia: </span><span class="sxs-lookup"><span data-stu-id="72f6e-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="72f6e-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="72f6e-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="72f6e-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="72f6e-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="72f6e-127">Otwórz `HelloSvcutil.csproj` plik projektu w edytorze, edytuj `Project` element i dodaj pakiet [ `dotnet-svcutil` NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie do narzędzia interfejsu wiersza polecenia, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="72f6e-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="72f6e-128">Następnie przywróć pakiet _dotnet-svcutil_ za pomocą polecenia w [`dotnet restore`](../tools/dotnet-restore.md) następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72f6e-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

    ---

4. <span data-ttu-id="72f6e-129">Uruchom polecenie _dotnet-svcutil,_ aby wygenerować plik odwołania do usługi sieci web w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72f6e-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="72f6e-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="72f6e-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="72f6e-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="72f6e-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="72f6e-132">Wygenerowany plik jest zapisywany jako _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="72f6e-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="72f6e-133">Narzędzie _dotnet-svcutil_ dodaje również do projektu odpowiednie pakiety WCF wymagane przez kod serwera proxy jako odwołania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="72f6e-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="72f6e-134">Korzystanie z odwołania do usługi</span><span class="sxs-lookup"><span data-stu-id="72f6e-134">Using the Service Reference</span></span>

1. <span data-ttu-id="72f6e-135">Przywróć pakiety [`dotnet restore`](../tools/dotnet-restore.md) WCF za pomocą polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72f6e-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

2. <span data-ttu-id="72f6e-136">Znajdź nazwę klasy klienta i operacji, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="72f6e-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="72f6e-137">`Reference.cs`będzie zawierać klasę, która `System.ServiceModel.ClientBase`dziedziczy z , z metod, które mogą służyć do wywoływania operacji w usłudze.</span><span class="sxs-lookup"><span data-stu-id="72f6e-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="72f6e-138">W tym przykładzie chcesz wywołać operację _Hello_ usługi _SayHello._</span><span class="sxs-lookup"><span data-stu-id="72f6e-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="72f6e-139">`ServiceReference.SayHelloClient`jest nazwą klasy klienta i ma metodę `HelloAsync` o nazwie, która może służyć do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="72f6e-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="72f6e-140">Otwórz `Startup.cs` plik w edytorze i dodaj instrukcję using dla obszaru nazw odwołania do usługi u góry:</span><span class="sxs-lookup"><span data-stu-id="72f6e-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="72f6e-141">Edytuj `Configure` metodę wywoływania usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="72f6e-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="72f6e-142">Można to zrobić, tworząc wystąpienie klasy, `ClientBase` która dziedziczy i wywołując metodę w obiekcie klienta:</span><span class="sxs-lookup"><span data-stu-id="72f6e-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
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

5. <span data-ttu-id="72f6e-143">Uruchom aplikację za [`dotnet run`](../tools/dotnet-run.md) pomocą polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72f6e-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```dotnetcli
    dotnet run
    ```

6. <span data-ttu-id="72f6e-144">Przejdź do adresu URL wymienionego w `http://localhost:5000`konsoli (na przykład) w przeglądarce internetowej.</span><span class="sxs-lookup"><span data-stu-id="72f6e-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="72f6e-145">Powinieneś zobaczyć następujące dane wyjściowe: "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="72f6e-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="72f6e-146">Aby uzyskać szczegółowy `dotnet-svcutil` opis parametrów narzędzia, wywołać narzędzie przekazując parametr pomocy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72f6e-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="72f6e-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="72f6e-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="72f6e-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="72f6e-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="72f6e-149">Opinie & pytania</span><span class="sxs-lookup"><span data-stu-id="72f6e-149">Feedback & questions</span></span>

<span data-ttu-id="72f6e-150">Jeśli masz jakieś pytania lub opinie, [otwórz problem w usłudze GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="72f6e-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="72f6e-151">Możesz również przejrzeć wszelkie istniejące pytania lub problemy [w repozytorium WCF na GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="72f6e-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="72f6e-152">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="72f6e-152">Release notes</span></span>

- <span data-ttu-id="72f6e-153">Informacje o wersji można znaleźć w [informacjach o](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) wersji, w tym o znanych problemach.</span><span class="sxs-lookup"><span data-stu-id="72f6e-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="72f6e-154">Informacje</span><span class="sxs-lookup"><span data-stu-id="72f6e-154">Information</span></span>

- [<span data-ttu-id="72f6e-155">Pakiet dotnet-svcutil NuGet</span><span class="sxs-lookup"><span data-stu-id="72f6e-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
