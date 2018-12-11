---
title: Omówienie narzędzia svcutil WCF
description: Omówienie narzędzia dotnet svcutil Microsoft WCF, który dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobny do narzędzia svcutil WCF dla projektów programu .NET Framework.
author: mlacouture
ms.date: 08/20/2018
ms.custom: seodec18
ms.openlocfilehash: e42ec0d4072c56456c824a814f1b383ea70a9307
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237262"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="76bcf-103">Narzędzia dotnet svcutil WCF dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="76bcf-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="76bcf-104">Windows Communication Foundation (WCF) **narzędzia svcutil dotnet** narzędzie to narzędzie wiersza polecenia platformy .NET Core, pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, która generuje klasę usługi WCF, zawierająca metody serwera proxy klienta, dostęp do operacji usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="76bcf-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="76bcf-105">Podobnie jak [ **metadanych modelu usługi - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia dla projektów programu .NET Framework **narzędzia svcutil dotnet** jest narzędziem wiersza polecenia do generowania odwołanie do usługi sieci web zgodne z projektami .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="76bcf-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="76bcf-106">**Narzędzia svcutil dotnet** narzędzie jest alternatywnych opcji [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) dostawcy usług, które po raz pierwszy wysłane połączona programu Visual Studio z programem Visual Studio v15.5 2017 r.</span><span class="sxs-lookup"><span data-stu-id="76bcf-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="76bcf-107">**Narzędzia svcutil dotnet** narzędzia jako narzędzie wiersza polecenia platformy .NET Core, są dostępne dla wielu platform w systemie Linux, macOS i Windows.</span><span class="sxs-lookup"><span data-stu-id="76bcf-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="76bcf-108">Użytkownik powinien odwoływać się tylko do usług z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="76bcf-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="76bcf-109">Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="76bcf-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="76bcf-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="76bcf-110">Prerequisites</span></span>

* <span data-ttu-id="76bcf-111">[Zestaw .NET core SDK](https://dotnet.microsoft.com/download) v1.0.4 lub nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="76bcf-111">[.NET Core SDK](https://dotnet.microsoft.com/download) v1.0.4 or later versions</span></span>
* <span data-ttu-id="76bcf-112">Wybrany edytor kodu</span><span class="sxs-lookup"><span data-stu-id="76bcf-112">Your favorite code editor</span></span>

## <a name="getting-started"></a><span data-ttu-id="76bcf-113">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="76bcf-113">Getting started</span></span>

<span data-ttu-id="76bcf-114">Poniższy przykład przeprowadzi Cię przez kroki wymagane do Dodaj odwołanie do usługi sieci web, aby projekt konsoli .NET Core i wywołać usługę.</span><span class="sxs-lookup"><span data-stu-id="76bcf-114">The following example walks you through the steps required to add a web service reference to a .NET Core console project and invoke the service.</span></span> <span data-ttu-id="76bcf-115">Utworzysz aplikację konsolową .NET Core, o nazwie _HelloSvcutil_ i doda odwołanie do usługi sieci web, który implementuje ten kontrakt następujące:</span><span class="sxs-lookup"><span data-stu-id="76bcf-115">You will create a .NET Core console application named _HelloSvcutil_ and will add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="76bcf-116">W tym przykładzie Usługa sieci web zostanie przyjęta wartość będzie hostowana pod następującym adresem: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="76bcf-116">For this example, the web service will be assumed to be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="76bcf-117">Z poziomu okna polecenia Windows, macOS lub Linux, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="76bcf-117">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="76bcf-118">Utwórz katalog o nazwie _HelloSvcutil_ dla projektu i udostępnić go w bieżącym katalogu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="76bcf-118">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="76bcf-119">Utwórz nowy projekt konsoli języka C#, w tym katalogu przy użyciu [ `dotnet new` ](../tools/dotnet-new.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76bcf-119">Create a new C# console project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new console
```

3. <span data-ttu-id="76bcf-120">Otwórz `HelloSvcutil.csproj` projektu plik w edytorze, Edytuj `Project` element i Dodaj [ `dotnet-svcutil` pakietu NuGet](https://nuget.org/packages/dotnet-svcutil) jako odwołanie narzędzie interfejsu wiersza polecenia, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="76bcf-120">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. <span data-ttu-id="76bcf-121">Przywróć _narzędzia svcutil dotnet_ pakietu przy użyciu [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76bcf-121">Restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

5. <span data-ttu-id="76bcf-122">Uruchom _dotnet_ z _svcutil_ polecenie, aby wygenerować plik odwołanie do usługi sieci web w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76bcf-122">Run _dotnet_ with the _svcutil_ command to generate the web service reference file as follows:</span></span>

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
<span data-ttu-id="76bcf-123">Wygenerowany plik jest zapisywany jako _HelloSvcutil/ServiceReference1/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="76bcf-123">The generated file is saved as _HelloSvcutil/ServiceReference1/Reference.cs_.</span></span> <span data-ttu-id="76bcf-124">_Dotnet_svcutil_ narzędzie automatycznie dodaje również do projektu odpowiednich pakietów WCF wymagane przez kod serwera proxy jako odwołania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="76bcf-124">The _dotnet_svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

6. <span data-ttu-id="76bcf-125">Przywróć pakiety programu WCF za pomocą [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76bcf-125">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

7. <span data-ttu-id="76bcf-126">Otwórz `Program.cs` plik w edytorze, Edytuj `Main()` metodę i Zastąp automatycznego generowania kodu za pomocą następującego kodu, aby wywołać usługę sieci web:</span><span class="sxs-lookup"><span data-stu-id="76bcf-126">Open the `Program.cs` file in your editor, edit the `Main()` method, and replace the auto-generated code with the following code to invoke the web service:</span></span>

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. <span data-ttu-id="76bcf-127">Uruchamianie aplikacji przy użyciu [ `dotnet run` ](../tools/dotnet-run.md) polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76bcf-127">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```
<span data-ttu-id="76bcf-128">Powinny zostać wyświetlone następujące dane wyjściowe: "Hello dotnet-svcutil /!"</span><span class="sxs-lookup"><span data-stu-id="76bcf-128">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="76bcf-129">Aby uzyskać szczegółowy opis `dotnet-svcutil` narzędzia parametrów, wywołaj narzędzie przekazywania parametru pomocy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76bcf-129">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

```console
dotnet svcutil --help
```

## <a name="next-steps"></a><span data-ttu-id="76bcf-130">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="76bcf-130">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="76bcf-131">Opinie i pytania</span><span class="sxs-lookup"><span data-stu-id="76bcf-131">Feedback & questions</span></span>

<span data-ttu-id="76bcf-132">Jeśli masz pytania lub opinie, [Otwórz problem w serwisie GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="76bcf-132">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="76bcf-133">Możesz również sprawdzić wszelkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="76bcf-133">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="76bcf-134">Uwagi do wersji</span><span class="sxs-lookup"><span data-stu-id="76bcf-134">Release notes</span></span>

* <span data-ttu-id="76bcf-135">Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="76bcf-135">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

### <a name="information"></a><span data-ttu-id="76bcf-136">Informacje</span><span class="sxs-lookup"><span data-stu-id="76bcf-136">Information</span></span>

* [<span data-ttu-id="76bcf-137">Pakiet NuGet narzędzia svcutil DotNet</span><span class="sxs-lookup"><span data-stu-id="76bcf-137">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
