---
title: "Za pomocą generatora serializatora XML programu Microsoft .NET Core"
description: "Przegląd generatora serializatora XML firmy Microsoft."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: b2f52a068d128b2eb978c9e086508bd87e103ebc
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="bd113-103">Za pomocą generatora serializatora XML programu Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd113-103">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="bd113-104">W tym samouczku jest przedstawienie sposobu Generator serializatora XML firmy Microsoft jest używany w aplikacji C# .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd113-104">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="bd113-105">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="bd113-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="bd113-106">Jak utworzyć aplikację .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd113-106">How to create a .NET Core app</span></span>
> * <span data-ttu-id="bd113-107">Jak dodać odwołanie do pakietu Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="bd113-107">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="bd113-108">Jak edytować MyApp.csproj użytkownika można dodać zależności</span><span class="sxs-lookup"><span data-stu-id="bd113-108">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="bd113-109">Jak dodać klasę i XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="bd113-109">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="bd113-110">Jak skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="bd113-110">How to build and run the application</span></span> 

<span data-ttu-id="bd113-111">Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem dla projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="bd113-111">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="bd113-112">Tworzy zestaw serializacji XML dla typów zawartych w zestawie poprawić wydajność uruchamiania serializacji XML podczas serializacji lub do serializacji obiektów typu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="bd113-112">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd113-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bd113-113">Prerequisites</span></span>

<span data-ttu-id="bd113-114">Do ukończenia tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="bd113-114">To complete this tutorial:</span></span>

* <span data-ttu-id="bd113-115">Zainstaluj [.NET Core SDK 2.1.3 lub nowszy](https://www.microsoft.com/net/download)</span><span class="sxs-lookup"><span data-stu-id="bd113-115">Install [.NET Core SDK 2.1.3 or later](https://www.microsoft.com/net/download)</span></span>
* <span data-ttu-id="bd113-116">Jeśli nie jest jeszcze, należy zainstalować w edytorze kodu ulubionych.</span><span class="sxs-lookup"><span data-stu-id="bd113-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="bd113-117">Należy zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="bd113-117">Need to install a code editor?</span></span> <span data-ttu-id="bd113-118">Spróbuj [programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="bd113-118">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="bd113-119">Użyj generatora serializatora XML firmy Microsoft w aplikacji konsoli .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd113-119">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span> 

<span data-ttu-id="bd113-120">Poniższe instrukcje pokazują, jak użyć generatora serializatora XML w aplikacji konsoli .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd113-120">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="bd113-121">Tworzenie aplikacji konsoli .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd113-121">Create a .NET Core console application</span></span>

<span data-ttu-id="bd113-122">Otwórz wiersz polecenia i Utwórz folder o nazwie *moja_aplikacja*.</span><span class="sxs-lookup"><span data-stu-id="bd113-122">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="bd113-123">Przejdź do folderu, który został utworzony i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="bd113-123">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="bd113-124">Dodaj odwołanie do pakietu Microsoft.XmlSerializer.Generator w projekcie moja_aplikacja</span><span class="sxs-lookup"><span data-stu-id="bd113-124">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="bd113-125">Użyj [ `dotnet add package` ](../tools//dotnet-add-package.md) polecenie, aby dodać odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="bd113-125">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span> 

<span data-ttu-id="bd113-126">Wpisz:</span><span class="sxs-lookup"><span data-stu-id="bd113-126">Type:</span></span>
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="bd113-127">Sprawdzenie zmian MyApp.csproj po dodaniu pakietu</span><span class="sxs-lookup"><span data-stu-id="bd113-127">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="bd113-128">Otwórz w edytorze kodu i do dzieła!</span><span class="sxs-lookup"><span data-stu-id="bd113-128">Open your code editor and let's get started!</span></span> <span data-ttu-id="bd113-129">Naszym celem jest nadal z *moja_aplikacja* budujemy aplikację w katalogu.</span><span class="sxs-lookup"><span data-stu-id="bd113-129">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="bd113-130">Otwórz *MyApp.csproj* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="bd113-130">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="bd113-131">Po uruchomieniu [ `dotnet add package` ](../tools//dotnet-add-package.md) następujących wierszy polecenia, są dodawane do Twojej *MyApp.csproj* pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="bd113-131">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="bd113-132">Dodaj innej sekcji ItemGroup .NET Core interfejsu wiersza polecenia narzędzia pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="bd113-132">Add another ItemGroup section for .NET Core CLI Tool support</span></span>
 
 <span data-ttu-id="bd113-133">Dodaj następujące wiersze po `ItemGroup` sekcji możemy inspekcji:</span><span class="sxs-lookup"><span data-stu-id="bd113-133">Add the following lines after the `ItemGroup` section that we inspected:</span></span>
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a><span data-ttu-id="bd113-134">Dodaj klasę w aplikacji</span><span class="sxs-lookup"><span data-stu-id="bd113-134">Add a class in the application</span></span>

<span data-ttu-id="bd113-135">Otwórz *Program.cs* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="bd113-135">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="bd113-136">Dodaj klasę o nazwie *MyClass* w *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="bd113-136">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="bd113-137">Utwórz `XmlSerializer` dla MyClass</span><span class="sxs-lookup"><span data-stu-id="bd113-137">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="bd113-138">Dodaj następujący wiersz wewnątrz *Main* utworzyć `XmlSerializer` dla MyClass:</span><span class="sxs-lookup"><span data-stu-id="bd113-138">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="bd113-139">Tworzenie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="bd113-139">Build and run the application</span></span>

<span data-ttu-id="bd113-140">Nadal w ramach *moja_aplikacja* folderu, uruchom aplikację za pośrednictwem [ `dotnet run` ](../tools/dotnet-run.md) i automatycznie ładuje i używa serializatorów wstępnie wygenerowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bd113-140">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="bd113-141">Wpisz następujące polecenie w oknie konsoli:</span><span class="sxs-lookup"><span data-stu-id="bd113-141">Type the following command in your console window:</span></span>

 ```console
 $ dotnet run
 ```
> [!NOTE]
> <span data-ttu-id="bd113-142">[`dotnet run`](../tools/dotnet-run.md)wywołania [ `dotnet build` ](../tools/dotnet-build.md) do upewnij się, że kompilacji są wbudowane elementy docelowe, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="bd113-142">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd113-143">Polecenia i kroki opisane w tym samouczku do uruchamiania aplikacji są używane tylko w czasie tworzenia.</span><span class="sxs-lookup"><span data-stu-id="bd113-143">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="bd113-144">Gdy wszystko jest gotowe do wdrożenia aplikacji, zapoznaj się z różnych [strategii wdrażania](../deploying/index.md) dla aplikacji .NET Core i [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd113-144">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="bd113-145">Jeśli wszystko, co zakończy się powodzeniem, zestaw o nazwie *MyApp.XmlSerializers.dll* jest generowana w folderze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="bd113-145">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span> 



<span data-ttu-id="bd113-146">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="bd113-146">Congratulations!</span></span> <span data-ttu-id="bd113-147">masz tylko:</span><span class="sxs-lookup"><span data-stu-id="bd113-147">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bd113-148">Utworzony .NET Core aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd113-148">Created a .NET Core app.</span></span>
> * <span data-ttu-id="bd113-149">Dodano odwołanie do pakietu Microsoft.XmlSerializer.Generator.</span><span class="sxs-lookup"><span data-stu-id="bd113-149">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="bd113-150">Edytować MyApp.csproj użytkownika można dodać zależności.</span><span class="sxs-lookup"><span data-stu-id="bd113-150">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="bd113-151">Dodaje klasę i XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="bd113-151">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="bd113-152">Wbudowane i uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd113-152">Built and ran the application.</span></span> 

## <a name="related-resources"></a><span data-ttu-id="bd113-153">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="bd113-153">Related Resources</span></span>

* [<span data-ttu-id="bd113-154">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="bd113-154">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="bd113-155">Porady: serializacji przy użyciu elementu XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="bd113-155">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [<span data-ttu-id="bd113-156">Porady: serializacji przy użyciu elementu XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd113-156">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
