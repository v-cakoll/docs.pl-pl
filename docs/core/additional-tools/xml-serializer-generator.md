---
title: Generator serializatorów XML firmy Microsoft
description: Omówienie generatora serializatorów XML firmy Microsoft. Użyj generatora serializatorów XML, aby wygenerować zestaw serializacji XML dla typów zawartych w projekcie.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c3f1fcda8a8a6abc58d35bf37e51485bb3590fa3
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794640"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="ace41-104">Używanie generatora serializatorów Microsoft XML na platformie .NET Core</span><span class="sxs-lookup"><span data-stu-id="ace41-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="ace41-105">W tym samouczku przedstawiono sposób użycia generatora serializatorów XML firmy Microsoft w aplikacji .NET Core w języku C#.</span><span class="sxs-lookup"><span data-stu-id="ace41-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="ace41-106">W ramach tego samouczka nauczysz się:</span><span class="sxs-lookup"><span data-stu-id="ace41-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ace41-107">Jak utworzyć aplikację .NET Core</span><span class="sxs-lookup"><span data-stu-id="ace41-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="ace41-108">Jak dodać odwołanie do pakietu Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="ace41-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="ace41-109">Jak edytować plik MyApp.csproj, aby dodać zależności</span><span class="sxs-lookup"><span data-stu-id="ace41-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="ace41-110">Jak dodać klasę i obiekt XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="ace41-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="ace41-111">Jak skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="ace41-111">How to build and run the application</span></span>

<span data-ttu-id="ace41-112">Podobnie jak w przypadku .NET Framework [Generator serializatorów XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) , [pakiet NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ace41-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="ace41-113">Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność podczas uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ace41-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ace41-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ace41-114">Prerequisites</span></span>

<span data-ttu-id="ace41-115">W celu ukończenia tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="ace41-115">To complete this tutorial:</span></span>

- <span data-ttu-id="ace41-116">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ace41-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="ace41-117">Twój ulubiony Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="ace41-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="ace41-118">Musisz zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="ace41-118">Need to install a code editor?</span></span> <span data-ttu-id="ace41-119">Wypróbuj [program Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="ace41-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="ace41-120">Używanie generatora serializatorów Microsoft XML w aplikacji konsolowej platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ace41-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="ace41-121">Poniższe instrukcje pokazują, jak używać generatora serializatorów XML w aplikacji konsolowej programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ace41-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="ace41-122">Tworzenie aplikacji konsolowej platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ace41-122">Create a .NET Core console application</span></span>

<span data-ttu-id="ace41-123">Otwórz wiersz polecenia i Utwórz folder o nazwie *MojaApl*.</span><span class="sxs-lookup"><span data-stu-id="ace41-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="ace41-124">Przejdź do utworzonego folderu i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ace41-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="ace41-125">Dodawanie odwołania do pakietu Microsoft. XmlSerializer. Generator w projekcie MojaApl</span><span class="sxs-lookup"><span data-stu-id="ace41-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="ace41-126">Użyj polecenia [`dotnet add package`](../tools/dotnet-add-package.md) , aby dodać odwołanie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ace41-126">Use the [`dotnet add package`](../tools/dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="ace41-127">Wpisz:</span><span class="sxs-lookup"><span data-stu-id="ace41-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="ace41-128">Sprawdź zmiany w programie MojaApl. csproj po dodaniu pakietu</span><span class="sxs-lookup"><span data-stu-id="ace41-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="ace41-129">Otwórz Edytor kodu i zacznijmy pracę!</span><span class="sxs-lookup"><span data-stu-id="ace41-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="ace41-130">Nadal pracujemy nad katalogiem *MojaApl* , w którym została skompilowana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="ace41-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="ace41-131">Otwórz w edytorze tekstów *MojaApl. csproj* .</span><span class="sxs-lookup"><span data-stu-id="ace41-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="ace41-132">Po uruchomieniu [`dotnet add package`](../tools/dotnet-add-package.md) polecenia do pliku projektu *MojaApl. csproj* są dodawane następujące wiersze:</span><span class="sxs-lookup"><span data-stu-id="ace41-132">After running the [`dotnet add package`](../tools/dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="ace41-133">Dodaj kolejną sekcję elementu Item dla interfejs wiersza polecenia platformy .NET Core pomocy technicznej narzędzi</span><span class="sxs-lookup"><span data-stu-id="ace41-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="ace41-134">Dodaj następujące wiersze po `ItemGroup` sekcji, którą sprawdzisz:</span><span class="sxs-lookup"><span data-stu-id="ace41-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="ace41-135">Dodawanie klasy w aplikacji</span><span class="sxs-lookup"><span data-stu-id="ace41-135">Add a class in the application</span></span>

<span data-ttu-id="ace41-136">Otwórz *program.cs* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="ace41-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="ace41-137">Dodaj klasę o nazwie *MyClass* w *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="ace41-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="ace41-138">Utwórz dla `XmlSerializer` elementu MyClass</span><span class="sxs-lookup"><span data-stu-id="ace41-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="ace41-139">Dodaj następujący wiersz w obszarze *głównym* , aby utworzyć `XmlSerializer` for MyClass:</span><span class="sxs-lookup"><span data-stu-id="ace41-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="ace41-140">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="ace41-140">Build and run the application</span></span>

<span data-ttu-id="ace41-141">Nadal w folderze *MojaApl* Uruchom aplikację za pośrednictwem [`dotnet run`](../tools/dotnet-run.md) programu, która automatycznie ładuje i używa wstępnie wygenerowanych serializatorów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ace41-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="ace41-142">W oknie konsoli wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ace41-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="ace41-143">[`dotnet run`](../tools/dotnet-run.md)wywołuje [`dotnet build`](../tools/dotnet-build.md) się, by upewnić się, że cele kompilacji zostały skompilowane `dotnet <assembly.dll>` , a następnie wywołuje, aby uruchomić aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="ace41-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ace41-144">Polecenia i kroki przedstawione w tym samouczku do uruchamiania aplikacji są używane tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="ace41-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="ace41-145">Gdy wszystko będzie gotowe do wdrożenia aplikacji, zapoznaj się z różnymi [strategiami wdrażania](../deploying/index.md) aplikacji .NET Core i [`dotnet publish`](../tools/dotnet-publish.md) poleceniem.</span><span class="sxs-lookup"><span data-stu-id="ace41-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="ace41-146">Jeśli wszystko powiedzie się, zestaw o nazwie *MojaApl. XmlSerializers. dll* jest generowany w folderze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="ace41-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="ace41-147">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="ace41-147">Congratulations!</span></span> <span data-ttu-id="ace41-148">Masz właśnie:</span><span class="sxs-lookup"><span data-stu-id="ace41-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ace41-149">Utworzono aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ace41-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="ace41-150">Dodano odwołanie do pakietu Microsoft. XmlSerializer. Generator.</span><span class="sxs-lookup"><span data-stu-id="ace41-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="ace41-151">Edycja programu MojaApl. csproj w celu dodania zależności.</span><span class="sxs-lookup"><span data-stu-id="ace41-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="ace41-152">Dodano klasę i element XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="ace41-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="ace41-153">Aplikacja została skompilowana i uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ace41-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="ace41-154">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="ace41-154">Related resources</span></span>

- [<span data-ttu-id="ace41-155">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="ace41-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="ace41-156">Jak serializować przy użyciu elementu XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="ace41-156">How to serialize using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [<span data-ttu-id="ace41-157">Instrukcje: Serializowanie przy użyciu elementu XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace41-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
