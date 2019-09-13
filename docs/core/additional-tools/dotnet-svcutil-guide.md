---
title: Omówienie narzędzia WCF Svcutil
description: Omówienie narzędzia dotnet-Svcutil programu Microsoft WCF, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobnie jak narzędzie WCF Svcutil dla projektów .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 723855401f3a81edbd34c77481e4ff12db7dcdaf
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926451"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="7ebd5-103">WCF dotnet-Svcutil Tool dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="7ebd5-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="7ebd5-104">Windows Communication Foundation (WCF) **dotnet-Svcutil** Tool to narzędzie interfejs wiersza polecenia platformy .NET Core, które pobiera metadane z usługi sieci Web w lokalizacji sieciowej lub z pliku WSDL, i GENERUJE klasę WCF zawierającą metody serwera proxy klienta, które uzyskują dostęp do usługi sieci Web. składowa.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="7ebd5-105">Podobnie jak w przypadku narzędzi [**metadanych Svcutil modelu usług**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dla projektów .NET Framework, **dotnet-Svcutil** to narzędzie wiersza polecenia do generowania odwołania usługi internetowej zgodnej z projektami .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="7ebd5-106">Narzędzie **dotnet-Svcutil** jest alternatywną opcją dla [**usługi sieci Web programu WCF odwołującej**](wcf-web-service-reference-guide.md) się do dostawcy usługi połączonej programu Visual Studio, która jest najpierw dostarczana z programem Visual Studio 2017 v 15.5.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="7ebd5-107">Narzędzie **dotnet-Svcutil** jako narzędzie interfejs wiersza polecenia platformy .NET Core jest dostępne dla wielu platform w systemach Linux, MacOS i Windows.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ebd5-108">Należy tylko odwoływać się do usług z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="7ebd5-109">Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7ebd5-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7ebd5-110">Prerequisites</span></span>

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="7ebd5-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="7ebd5-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

* <span data-ttu-id="7ebd5-112">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowsza wersja</span><span class="sxs-lookup"><span data-stu-id="7ebd5-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="7ebd5-113">Ulubiony Edytor kodu</span><span class="sxs-lookup"><span data-stu-id="7ebd5-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="7ebd5-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="7ebd5-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

* <span data-ttu-id="7ebd5-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) lub jego nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="7ebd5-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="7ebd5-116">Ulubiony Edytor kodu</span><span class="sxs-lookup"><span data-stu-id="7ebd5-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="7ebd5-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="7ebd5-117">Getting started</span></span>

<span data-ttu-id="7ebd5-118">Poniższy przykład przeprowadzi Cię przez kroki wymagane do dodania odwołania usługi sieci Web do projektu sieci Web platformy .NET Core i wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="7ebd5-119">Utworzysz aplikację sieci Web platformy .NET Core o nazwie _HelloSvcutil_ i dodasz odwołanie do usługi sieci Web, która implementuje następujący kontrakt:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-119">You'll create a .NET Core web application named _HelloSvcutil_ and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="7ebd5-120">Na potrzeby tego przykładu Załóżmy, że usługa sieci Web będzie hostowana pod następującym adresem:`http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="7ebd5-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="7ebd5-121">W oknie polecenia systemu Windows, macOS lub Linux wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="7ebd5-122">Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i ustaw go jako bieżący katalog, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="7ebd5-123">Utwórz nowy C# projekt sieci Web w tym katalogu przy użyciu [`dotnet new`](../tools/dotnet-new.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```console
    dotnet new web
    ```

3. <span data-ttu-id="7ebd5-124">Zainstaluj pakiet NuGet jako narzędzie interfejsu wiersza polecenia: [ `dotnet-svcutil` ](https://nuget.org/packages/dotnet-svcutil) </span><span class="sxs-lookup"><span data-stu-id="7ebd5-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="7ebd5-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="7ebd5-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="7ebd5-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="7ebd5-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="7ebd5-127">Otwórz plik [ `dotnet-svcutil` ](https://nuget.org/packages/dotnet-svcutil) projektu w edytorze, `Project` Edytuj element i Dodaj pakiet NuGet jako odwołanie narzędzia interfejsu wiersza polecenia, używając następującego kodu: `HelloSvcutil.csproj`</span><span class="sxs-lookup"><span data-stu-id="7ebd5-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="7ebd5-128">Następnie Przywróć pakiet _dotnet-Svcutil_ za pomocą [`dotnet restore`](../tools/dotnet-restore.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

    ---

4. <span data-ttu-id="7ebd5-129">Uruchom polecenie _dotnet-Svcutil_ , aby wygenerować plik referencyjny usługi sieci Web w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="7ebd5-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="7ebd5-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="7ebd5-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="7ebd5-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```console
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="7ebd5-132">Wygenerowany plik zostanie zapisany jako _HelloSvcutil/ServiceReference/Reference. cs_.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="7ebd5-133">Narzędzie _dotnet-Svcutil_ dodaje również do projektu odpowiednie pakiety WCF wymagane przez kod serwera proxy jako odwołania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="7ebd5-134">Korzystanie z odwołania do usługi</span><span class="sxs-lookup"><span data-stu-id="7ebd5-134">Using the Service Reference</span></span>

1. <span data-ttu-id="7ebd5-135">Przywróć pakiety WCF przy użyciu [`dotnet restore`](../tools/dotnet-restore.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

2. <span data-ttu-id="7ebd5-136">Znajdź nazwę klasy klienta i operację, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="7ebd5-137">`Reference.cs`będzie zawierać klasę, która dziedziczy z `System.ServiceModel.ClientBase`, przy użyciu metod, które mogą być używane do wywoływania operacji w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="7ebd5-138">W tym przykładzie chcesz wywołać operację _Hello_ usługi _sayHello_ .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="7ebd5-139">`ServiceReference.SayHelloClient`jest nazwą klasy klienta i ma metodę o nazwie `HelloAsync` , która może być używana do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="7ebd5-140">`Startup.cs` Otwórz plik w edytorze i Dodaj instrukcję using dla przestrzeni nazw odwołania do usługi u góry:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="7ebd5-141">`Configure` Edytuj metodę, aby wywołać usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="7ebd5-142">Można to zrobić, tworząc wystąpienie klasy, która dziedziczy z `ClientBase` i wywołując metodę na obiekcie klienta:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="7ebd5-143">Uruchom aplikację za pomocą [`dotnet run`](../tools/dotnet-run.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```console
    dotnet run
    ```

6. <span data-ttu-id="7ebd5-144">Przejdź do adresu URL podanego w konsoli programu (na `http://localhost:5000`przykład) w przeglądarce sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="7ebd5-145">Powinny zostać wyświetlone następujące dane wyjściowe: "Hello dotnet-Svcutil!"</span><span class="sxs-lookup"><span data-stu-id="7ebd5-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="7ebd5-146">Aby uzyskać szczegółowy opis `dotnet-svcutil` parametrów narzędzia, wywołaj narzędzie do przekazywania parametru pomocy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ebd5-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="7ebd5-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="7ebd5-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="7ebd5-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="7ebd5-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="7ebd5-149">Opinie & pytania</span><span class="sxs-lookup"><span data-stu-id="7ebd5-149">Feedback & questions</span></span>

<span data-ttu-id="7ebd5-150">Jeśli masz jakieś pytania lub opinie, [Otwórz problem w usłudze GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="7ebd5-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="7ebd5-151">Możesz również zapoznać się z istniejącymi pytaniami i problemami [w REPOZYTORIUM WCF w serwisie GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="7ebd5-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="7ebd5-152">Uwagi do wersji</span><span class="sxs-lookup"><span data-stu-id="7ebd5-152">Release notes</span></span>

* <span data-ttu-id="7ebd5-153">Zapoznaj się z informacjami o [wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) dotyczącymi zaktualizowanych informacji o wersji, w tym znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="7ebd5-154">Informacje</span><span class="sxs-lookup"><span data-stu-id="7ebd5-154">Information</span></span>

* [<span data-ttu-id="7ebd5-155">Pakiet NuGet dotnet-Svcutil</span><span class="sxs-lookup"><span data-stu-id="7ebd5-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
