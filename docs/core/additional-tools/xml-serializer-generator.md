---
title: Generator serializatora XML firmy Microsoft
description: Omówienie generatora serializatora Microsoft XML. Użyj Generatora serializatora XML, aby wygenerować zestaw serializacji XML dla typów zawartych w projekcie.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714528"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="4011a-104">Używanie generatora serializatora Microsoft XML w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="4011a-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="4011a-105">W tym samouczku nauczy cię, jak używać generatora serializatora Microsoft XML w aplikacji C# .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4011a-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="4011a-106">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="4011a-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4011a-107">Jak utworzyć aplikację .NET Core</span><span class="sxs-lookup"><span data-stu-id="4011a-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="4011a-108">Jak dodać odwołanie do pakietu Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="4011a-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="4011a-109">Jak edytować plik MyApp.csproj, aby dodać zależności</span><span class="sxs-lookup"><span data-stu-id="4011a-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="4011a-110">Jak dodać klasę i obiekt XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="4011a-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="4011a-111">Jak skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="4011a-111">How to build and run the application</span></span>

<span data-ttu-id="4011a-112">Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework, [pakiet Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4011a-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="4011a-113">Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność uruchamiania serializacji XML podczas <xref:System.Xml.Serialization.XmlSerializer>serializacji lub deserializacji obiektów tych typów przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="4011a-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4011a-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4011a-114">Prerequisites</span></span>

<span data-ttu-id="4011a-115">W celu ukończenia tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="4011a-115">To complete this tutorial:</span></span>

- <span data-ttu-id="4011a-116">[SDK .NET Core 2.1](https://dotnet.microsoft.com/download) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="4011a-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="4011a-117">Twój ulubiony edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="4011a-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="4011a-118">Chcesz zainstalować edytor kodów?</span><span class="sxs-lookup"><span data-stu-id="4011a-118">Need to install a code editor?</span></span> <span data-ttu-id="4011a-119">[Wypróbuj program Visual Studio!](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="4011a-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="4011a-120">Używanie generatora serializatora Microsoft XML w aplikacji konsoli .NET Core</span><span class="sxs-lookup"><span data-stu-id="4011a-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="4011a-121">W poniższych instrukcjach przedstawiono sposób używania generatora serializatora XML w aplikacji konsoli .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4011a-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="4011a-122">Tworzenie aplikacji konsolowej platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="4011a-122">Create a .NET Core console application</span></span>

<span data-ttu-id="4011a-123">Otwórz wiersz polecenia i utwórz folder o nazwie *Mojaaplikacja*.</span><span class="sxs-lookup"><span data-stu-id="4011a-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="4011a-124">Przejdź do utworzonego folderu i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4011a-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="4011a-125">Dodawanie odwołania do pakietu Microsoft.XmlSerializer.Generator w projekcie MyApp</span><span class="sxs-lookup"><span data-stu-id="4011a-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="4011a-126">Użyj [`dotnet add package`](../tools//dotnet-add-package.md) polecenia, aby dodać odwołanie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4011a-126">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="4011a-127">Wpisz:</span><span class="sxs-lookup"><span data-stu-id="4011a-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="4011a-128">Sprawdź zmiany w myapp.csproj po dodaniu pakietu</span><span class="sxs-lookup"><span data-stu-id="4011a-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="4011a-129">Otwórz edytor kodu i zacznijmy!</span><span class="sxs-lookup"><span data-stu-id="4011a-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="4011a-130">Nadal pracujemy z katalogu *MyApp,* w który stworzyliśmy aplikację.</span><span class="sxs-lookup"><span data-stu-id="4011a-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="4011a-131">Otwórz *MyApp.csproj* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="4011a-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="4011a-132">Po uruchomieniu [`dotnet add package`](../tools//dotnet-add-package.md) polecenia do pliku projektu *MyApp.csproj* są dodawane następujące wiersze:</span><span class="sxs-lookup"><span data-stu-id="4011a-132">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="4011a-133">Dodawanie innej sekcji ItemGroup dla obsługi narzędzia CLI platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="4011a-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="4011a-134">Dodaj następujące wiersze `ItemGroup` po sekcji, którą sprawdziliśmy:</span><span class="sxs-lookup"><span data-stu-id="4011a-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="4011a-135">Dodawanie klasy w aplikacji</span><span class="sxs-lookup"><span data-stu-id="4011a-135">Add a class in the application</span></span>

<span data-ttu-id="4011a-136">Otwórz *Program.cs* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="4011a-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="4011a-137">Dodaj klasę o nazwie *MyClass* w *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="4011a-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="4011a-138">Tworzenie `XmlSerializer` dla MyClass</span><span class="sxs-lookup"><span data-stu-id="4011a-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="4011a-139">Dodaj następujący wiersz wewnątrz *Main,* aby utworzyć `XmlSerializer` for MyClass:</span><span class="sxs-lookup"><span data-stu-id="4011a-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="4011a-140">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4011a-140">Build and run the application</span></span>

<span data-ttu-id="4011a-141">Nadal w folderze *MyApp* uruchom [`dotnet run`](../tools/dotnet-run.md) aplikację za pośrednictwem i automatycznie ładuje i używa wstępnie wygenerowanych serializatorów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4011a-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="4011a-142">Wpisz następujące polecenie w oknie konsoli:</span><span class="sxs-lookup"><span data-stu-id="4011a-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="4011a-143">[`dotnet run`](../tools/dotnet-run.md)wywołania, [`dotnet build`](../tools/dotnet-build.md) aby upewnić się, że obiekty `dotnet <assembly.dll>` docelowe kompilacji zostały utworzone, a następnie wywołuje do uruchomienia aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="4011a-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4011a-144">Polecenia i kroki przedstawione w tym samouczku do uruchamiania aplikacji są używane tylko w czasie programowania.</span><span class="sxs-lookup"><span data-stu-id="4011a-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="4011a-145">Gdy wszystko będzie gotowe do wdrożenia aplikacji, zapoznaj się z [różnymi strategiami wdrażania](../deploying/index.md) aplikacji .NET Core i [`dotnet publish`](../tools/dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="4011a-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="4011a-146">Jeśli wszystko się powiedzie, w folderze wyjściowym jest generowany zestaw o nazwie *MyApp.XmlSerializers.dll.*</span><span class="sxs-lookup"><span data-stu-id="4011a-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="4011a-147">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="4011a-147">Congratulations!</span></span> <span data-ttu-id="4011a-148">Masz tylko:</span><span class="sxs-lookup"><span data-stu-id="4011a-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4011a-149">Utworzono aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4011a-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="4011a-150">Dodano odwołanie do pakietu Microsoft.XmlSerializer.Generator.</span><span class="sxs-lookup"><span data-stu-id="4011a-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="4011a-151">Edytowałem urządzenie MyApp.csproj, aby dodać zależności.</span><span class="sxs-lookup"><span data-stu-id="4011a-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="4011a-152">Dodano klasę i XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="4011a-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="4011a-153">Zbudowano i uruchomiono aplikację.</span><span class="sxs-lookup"><span data-stu-id="4011a-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="4011a-154">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="4011a-154">Related resources</span></span>

- [<span data-ttu-id="4011a-155">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="4011a-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="4011a-156">Jak serializować za pomocą XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="4011a-156">How to serialize using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [<span data-ttu-id="4011a-157">Jak: Serializuj przy użyciu XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4011a-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
