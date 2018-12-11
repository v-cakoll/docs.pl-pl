---
title: Generator serializatora XML firmy Microsoft
description: Przegląd Generator serializatora XML firmy Microsoft. Użyj Generator serializatora XML, aby wygenerować zestawu serializacji XML dla typów zawartych w projekcie.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: fad0bbe098718ba91765c24678b2cb099aa7bbb2
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168861"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="e0327-104">Za pomocą Generator serializatora XML firmy Microsoft na platformie .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0327-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="e0327-105">W tym samouczku pokazano sposób użycia Generator serializatora XML firmy Microsoft w C# aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0327-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="e0327-106">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="e0327-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="e0327-107">Jak utworzyć aplikację platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0327-107">How to create a .NET Core app</span></span>
> * <span data-ttu-id="e0327-108">Jak dodać odwołanie do pakietu Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="e0327-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="e0327-109">Jak edytować swoje MyApp.csproj, aby dodać zależności</span><span class="sxs-lookup"><span data-stu-id="e0327-109">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="e0327-110">Jak dodać klasę i element XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="e0327-110">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="e0327-111">Jak utworzyć i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="e0327-111">How to build and run the application</span></span> 

<span data-ttu-id="e0327-112">Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem dla projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e0327-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="e0327-113">Tworzy zestaw serializacji XML dla typów, które są zawarte w zestawie, aby zwiększyć wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiekty, które z tych typów, przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e0327-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e0327-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e0327-114">Prerequisites</span></span>

<span data-ttu-id="e0327-115">Do ukończenia tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="e0327-115">To complete this tutorial:</span></span>

* <span data-ttu-id="e0327-116">Zainstaluj [zestawu SDK programu .NET Core 2.1 lub nowszej](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="e0327-116">Install [.NET Core 2.1 SDK or later](https://www.microsoft.com/net/download).</span></span>
* <span data-ttu-id="e0327-117">Wybrany edytor kodu, należy zainstalować, jeśli jeszcze go.</span><span class="sxs-lookup"><span data-stu-id="e0327-117">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="e0327-118">Należy zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="e0327-118">Need to install a code editor?</span></span> <span data-ttu-id="e0327-119">Spróbuj [programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="e0327-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="e0327-120">Generator serializatora XML firmy Microsoft jest używany w aplikacji konsoli .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0327-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span> 

<span data-ttu-id="e0327-121">Następujące instrukcje pokazują, jak użyć Generator serializatora XML w aplikacji konsolowej .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0327-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="e0327-122">Tworzenie aplikacji konsolowej .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0327-122">Create a .NET Core console application</span></span>

<span data-ttu-id="e0327-123">Otwórz wiersz polecenia i Utwórz folder o nazwie *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="e0327-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="e0327-124">Przejdź do folderu, który został utworzony, a następnie wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e0327-124">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="e0327-125">Dodaj odwołanie do pakietu Microsoft.XmlSerializer.Generator w projekcie moja_aplikacja</span><span class="sxs-lookup"><span data-stu-id="e0327-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="e0327-126">Użyj [ `dotnet add package` ](../tools//dotnet-add-package.md) polecenie, aby dodać odwołanie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="e0327-126">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span> 

<span data-ttu-id="e0327-127">Wpisz:</span><span class="sxs-lookup"><span data-stu-id="e0327-127">Type:</span></span>
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="e0327-128">Sprawdź zmiany MyApp.csproj po dodaniu pakietu</span><span class="sxs-lookup"><span data-stu-id="e0327-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="e0327-129">Otwieranie Edytora kodu i zaczynajmy!</span><span class="sxs-lookup"><span data-stu-id="e0327-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="e0327-130">Wciąż pracujemy z *MyApp* utworzyliśmy aplikację w katalogu.</span><span class="sxs-lookup"><span data-stu-id="e0327-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="e0327-131">Otwórz *MyApp.csproj* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="e0327-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="e0327-132">Po uruchomieniu [ `dotnet add package` ](../tools//dotnet-add-package.md) polecenia, następujące wiersze są dodawane do Twojego *MyApp.csproj* pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="e0327-132">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="e0327-133">Dodawanie innej sekcji ItemGroup obsługę narzędzia interfejsu wiersza polecenia programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0327-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>
 
 <span data-ttu-id="e0327-134">Dodaj następujące wiersze po `ItemGroup` sekcji, którą firma Microsoft inspekcji:</span><span class="sxs-lookup"><span data-stu-id="e0327-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a><span data-ttu-id="e0327-135">Dodaj klasę w aplikacji</span><span class="sxs-lookup"><span data-stu-id="e0327-135">Add a class in the application</span></span>

<span data-ttu-id="e0327-136">Otwórz *Program.cs* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="e0327-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="e0327-137">Dodaj klasę o nazwie *MyClass* w *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="e0327-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="e0327-138">Utwórz `XmlSerializer` dla MyClass</span><span class="sxs-lookup"><span data-stu-id="e0327-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="e0327-139">Dodaj następujący wiersz *Main* utworzyć `XmlSerializer` dla MyClass:</span><span class="sxs-lookup"><span data-stu-id="e0327-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="e0327-140">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e0327-140">Build and run the application</span></span>

<span data-ttu-id="e0327-141">Nadal w elemencie *MyApp* folder, uruchom aplikację za pośrednictwem [ `dotnet run` ](../tools/dotnet-run.md) i automatycznie ładuje i używa wstępnie wygenerowanego serializatory w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="e0327-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="e0327-142">W oknie konsoli, należy wpisać następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e0327-142">Type the following command in your console window:</span></span>

 ```console
 $ dotnet run
 ```
> [!NOTE]
> <span data-ttu-id="e0327-143">[`dotnet run`](../tools/dotnet-run.md) wywołania [ `dotnet build` ](../tools/dotnet-build.md) do upewnij się, że kompilacji, utworzone elementy docelowe, a następnie wywołania `dotnet <assembly.dll>` do uruchamiania aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="e0327-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0327-144">Polecenia i kroki opisane w tym samouczku do uruchamiania aplikacji są używane tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="e0327-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="e0327-145">Gdy wszystko będzie gotowe do wdrożenia aplikacji, zapoznaj się z różnych [strategie wdrażania](../deploying/index.md) dla aplikacji platformy .NET Core i [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="e0327-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="e0327-146">Jeśli wszystko, co zakończy się powodzeniem, zestaw o nazwie *MyApp.XmlSerializers.dll* jest generowany w folderze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="e0327-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span> 



<span data-ttu-id="e0327-147">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="e0327-147">Congratulations!</span></span> <span data-ttu-id="e0327-148">masz tylko:</span><span class="sxs-lookup"><span data-stu-id="e0327-148">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="e0327-149">Utworzone .NET Core aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e0327-149">Created a .NET Core app.</span></span>
> * <span data-ttu-id="e0327-150">Dodano odwołanie do pakietu Microsoft.XmlSerializer.Generator.</span><span class="sxs-lookup"><span data-stu-id="e0327-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="e0327-151">Edytować swoje MyApp.csproj, aby dodać zależności.</span><span class="sxs-lookup"><span data-stu-id="e0327-151">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="e0327-152">Dodaje klasę i element XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="e0327-152">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="e0327-153">Wbudowane i uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e0327-153">Built and ran the application.</span></span> 

## <a name="related-resources"></a><span data-ttu-id="e0327-154">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="e0327-154">Related Resources</span></span>

* [<span data-ttu-id="e0327-155">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="e0327-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="e0327-156">Jak: Serializowanie przy użyciu elementu XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="e0327-156">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [<span data-ttu-id="e0327-157">Jak: Serializowanie przy użyciu elementu XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0327-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
