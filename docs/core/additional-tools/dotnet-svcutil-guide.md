---
title: Narzędzia dotnet svcutil Microsoft WCF
description: Omówienie narzędzia dotnet svcutil Microsoft WCF, który dodaje funkcje platformy .NET Core i ASP.NET Core projektów, podobnie jak narzędzia svcutil WCF dla projektów .NET Framework.
author: mlacouture
ms.author: jralexander
ms.date: 05/31/2018
ms.openlocfilehash: 1ef428059ff5d02ecf88d6c56875b712e3707caa
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728761"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a><span data-ttu-id="cecae-103">Narzędzia dotnet svcutil Microsoft WCF</span><span class="sxs-lookup"><span data-stu-id="cecae-103">Microsoft WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="cecae-104">Windows Communication Foundation (WCF) **dotnet svcutil** narzędzie to narzędzie .NET Core interfejsu wiersza polecenia, które pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, a następnie generuje WCF klasy zawierające metody serwera proxy klienta który dostęp do operacji usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="cecae-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="cecae-105">Podobnie jak [ **metadanych modelu usługi - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe) narzędzi dla projektów .NET Framework **dotnet svcutil** to narzędzie wiersza polecenia do generowania odwołania do usługi sieci web zgodny z projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cecae-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="cecae-106">**Dotnet svcutil** narzędzie jest dostępna opcja alternatywnych [ **odwołania do usługi sieci Web WCF** ](wcf-web-service-reference-guide) programu Visual Studio połączenia usługodawcy, najpierw dostarczonej z programem Visual Studio v15.5 2017 r.</span><span class="sxs-lookup"><span data-stu-id="cecae-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="cecae-107">**Dotnet svcutil** narzędzie jako narzędzie .NET Core interfejsu wiersza polecenia, jest dostępny i platform w systemie Linux, macOS i systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cecae-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cecae-108">Użytkownik powinien odwoływać się tylko usługi z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="cecae-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="cecae-109">Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="cecae-109">Adding references from an untrusted source may compromise security.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="cecae-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="cecae-110">Prerequisites</span></span>

* <span data-ttu-id="cecae-111">[Zestaw SDK programu .NET core](https://www.microsoft.com/net/download) v1.0.4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="cecae-111">[.NET Core SDK](https://www.microsoft.com/net/download) v1.0.4 or later versions</span></span>
* <span data-ttu-id="cecae-112">Edytor kodu ulubionych</span><span class="sxs-lookup"><span data-stu-id="cecae-112">Your favorite code editor</span></span>

## <a name="getting-started"></a><span data-ttu-id="cecae-113">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="cecae-113">Getting started</span></span>

<span data-ttu-id="cecae-114">Poniższy przykład przeprowadzi Cię przez kroki wymagane do dodawania odwołania do usługi sieci web do projektu konsoli .NET Core i wywoływanie usługi.</span><span class="sxs-lookup"><span data-stu-id="cecae-114">The following example walks you through the steps required to add a web service reference to a .NET Core console project and invoke the service.</span></span> <span data-ttu-id="cecae-115">Spowoduje utworzenie aplikacji konsoli .NET Core o nazwie _HelloSvcutil_ oraz zostanie dodane odwołanie do usługi sieci web implementujący kontrakt następujące:</span><span class="sxs-lookup"><span data-stu-id="cecae-115">You will create a .NET Core console application named _HelloSvcutil_ and will add a reference to a web service that implements the following contract:</span></span>
```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```
<span data-ttu-id="cecae-116">Na przykład usługi sieci web będzie traktowane jako hostowany pod następującym adresem: _http://myhost/SayHello.svc_</span><span class="sxs-lookup"><span data-stu-id="cecae-116">For this example, the web service will be assumed to be hosted at the following address: _http://myhost/SayHello.svc_</span></span>

<span data-ttu-id="cecae-117">Z `Windows`, `macOS`, lub `Linux` polecenia okna, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cecae-117">From a `Windows`, `macOS`, or `Linux` command window perform the following steps:</span></span>

1. <span data-ttu-id="cecae-118">Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i przekształcenie go w bieżącym katalogu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cecae-118">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="cecae-119">Utwórz nowy projekt console C# w tym katalogu przy użyciu [ `dotnet new` ](../tools/dotnet-new.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cecae-119">Create a new C# console project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new console
```

3. <span data-ttu-id="cecae-120">Otwórz `HelloSvcutil.csproj` projekt plik w edytorze, Edytuj `Project` element i Dodaj [ `dotnet-svcutil` pakietu NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie narzędzia interfejsu wiersza polecenia, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="cecae-120">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.0" />
</ItemGroup>
```

4. <span data-ttu-id="cecae-121">Przywróć _dotnet svcutil_ pakietu przy użyciu [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cecae-121">Restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

5. <span data-ttu-id="cecae-122">Uruchom _dotnet_ z _svcutil_ polecenie w celu wygenerowania pliku odwołań do usługi sieci web w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cecae-122">Run _dotnet_ with the _svcutil_ command to generate the web service reference file as follows:</span></span>

```console
dotnet svcutil http://myhost/SayHello.svc
```
<span data-ttu-id="cecae-123">Wygenerowany plik zostanie zapisany jako _HelloSvcutil/ServiceReference1/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="cecae-123">The generated file is saved as _HelloSvcutil/ServiceReference1/Reference.cs_.</span></span> <span data-ttu-id="cecae-124">_Dotnet_svcutil_ narzędzie również dodaje do projektu odpowiednich pakietów WCF wymagane przez kod serwera proxy jako odwołania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="cecae-124">The _dotnet_svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

6. <span data-ttu-id="cecae-125">Przywracanie pakietów WCF za pomocą [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cecae-125">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

7. <span data-ttu-id="cecae-126">Otwórz `Program.cs` plik w edytorze, Edytuj `Main()` metodę i Zastąp automatycznego generowania kodu przy użyciu następujący kod, aby wywołać usługę sieci web:</span><span class="sxs-lookup"><span data-stu-id="cecae-126">Open the `Program.cs` file in your editor, edit the `Main()` method, and replace the auto-generated code with the following code to invoke the web service:</span></span>

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. <span data-ttu-id="cecae-127">Uruchamianie aplikacji przy użyciu [ `dotnet run` ](../tools/dotnet-run.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cecae-127">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```
<span data-ttu-id="cecae-128">Powinny pojawić się następujące dane wyjściowe: "tekst Hello dotnet svcutil!"</span><span class="sxs-lookup"><span data-stu-id="cecae-128">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="cecae-129">Aby uzyskać szczegółowy opis `dotnet-svcutil` narzędzie parametrów, wywołania narzędzia przekazywanie parametru pomocy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cecae-129">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

```console
dotnet svcutil --help
```

## <a name="next-steps"></a><span data-ttu-id="cecae-130">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="cecae-130">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="cecae-131">Opinie i pytania</span><span class="sxs-lookup"><span data-stu-id="cecae-131">Feedback & questions</span></span>
<span data-ttu-id="cecae-132">Jeśli masz pytania lub opinie, [Otwórz problemu w serwisie GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="cecae-132">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="cecae-133">Można także przejrzeć wszystkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="cecae-133">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="cecae-134">Uwagi do wersji</span><span class="sxs-lookup"><span data-stu-id="cecae-134">Release notes</span></span>
* <span data-ttu-id="cecae-135">Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="cecae-135">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span> 

### <a name="information"></a><span data-ttu-id="cecae-136">Informacje</span><span class="sxs-lookup"><span data-stu-id="cecae-136">Information</span></span>
* [<span data-ttu-id="cecae-137">Pakiet NuGet DotNet svcutil</span><span class="sxs-lookup"><span data-stu-id="cecae-137">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
