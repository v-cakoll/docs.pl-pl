---
title: Udostępnianie składników .NET Core do modelu COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 8d9b8eb274777a0ed019a207c6e8610cc73ec390
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973313"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="d6e74-102">Udostępnianie składników .NET Core do modelu COM</span><span class="sxs-lookup"><span data-stu-id="d6e74-102">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="d6e74-103">W programie .NET Core proces uwidaczniania obiektów .NET do modelu COM został znacznie ulepszony w porównaniu do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6e74-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="d6e74-104">Poniższy proces przeprowadzi Cię przez sposób udostępnienia klasy modelowi COM.</span><span class="sxs-lookup"><span data-stu-id="d6e74-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="d6e74-105">W tym samouczku pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="d6e74-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="d6e74-106">Uwidocznij klasę modelu COM z platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e74-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="d6e74-107">Wygeneruj serwer COM w ramach tworzenia biblioteki .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e74-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="d6e74-108">Automatycznie Generuj manifest serwera Side-by-Side dla modelu COM bez rejestracji.</span><span class="sxs-lookup"><span data-stu-id="d6e74-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d6e74-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d6e74-109">Prerequisites</span></span>

- <span data-ttu-id="d6e74-110">Zainstaluj program [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download) lub nowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="d6e74-110">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="d6e74-111">Utwórz bibliotekę</span><span class="sxs-lookup"><span data-stu-id="d6e74-111">Create the library</span></span>

<span data-ttu-id="d6e74-112">Pierwszym krokiem jest utworzenie biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d6e74-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="d6e74-113">Utwórz nowy folder, a w tym folderze Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d6e74-113">Create a new folder, and in that folder run the following command:</span></span>
    
    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="d6e74-114">Otwórz `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="d6e74-115">Dodaj `using System.Runtime.InteropServices;` na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="d6e74-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="d6e74-116">Utwórz interfejs o nazwie `IServer`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="d6e74-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d6e74-117">For example:</span></span>

   [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]

5. <span data-ttu-id="d6e74-118">Dodaj atrybut `[Guid("<IID>")]` do interfejsu przy użyciu identyfikatora GUID interfejsu dla implementowanego interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="d6e74-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="d6e74-119">Na przykład `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="d6e74-120">Należy zauważyć, że ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d6e74-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="d6e74-121">W programie Visual Studio można wygenerować identyfikator GUID, przechodząc do menu Narzędzia > Utwórz GUID, aby otworzyć narzędzie Tworzenie identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="d6e74-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="d6e74-122">Dodaj atrybut `[InterfaceType]` do interfejsu i określ podstawowe interfejsy COM, które ma zaimplementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="d6e74-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="d6e74-123">Utwórz klasę o nazwie `Server` implementującej `IServer`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="d6e74-124">Dodaj atrybut `[Guid("<CLSID>")]` do klasy z identyfikatorem GUID klasy dla implementującej klasy COM.</span><span class="sxs-lookup"><span data-stu-id="d6e74-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="d6e74-125">Na przykład `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="d6e74-126">Podobnie jak w przypadku identyfikatora GUID interfejsu, ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d6e74-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="d6e74-127">Dodaj atrybut `[ComVisible(true)]` do interfejsu i klasy.</span><span class="sxs-lookup"><span data-stu-id="d6e74-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6e74-128">W przeciwieństwie do .NET Framework platforma .NET Core wymaga określenia identyfikatora CLSID każdej klasy, która ma być aktywowalnej za pośrednictwem modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d6e74-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="d6e74-129">Generowanie hosta COM</span><span class="sxs-lookup"><span data-stu-id="d6e74-129">Generate the COM host</span></span>

1. <span data-ttu-id="d6e74-130">Otwórz plik projektu `.csproj` i Dodaj `<EnableComHosting>true</EnableComHosting>` wewnątrz tagu `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="d6e74-131">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="d6e74-131">Build the project.</span></span>

<span data-ttu-id="d6e74-132">Wynikowe dane wyjściowe będą mieć `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` i `ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="d6e74-133">Rejestrowanie hosta COM dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="d6e74-133">Register the COM host for COM</span></span>

<span data-ttu-id="d6e74-134">Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom `regsvr32 ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="d6e74-135">Spowoduje to zarejestrowanie wszystkich uwidocznionych obiektów .NET w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d6e74-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="d6e74-136">Włączanie nierejestrowanego COM</span><span class="sxs-lookup"><span data-stu-id="d6e74-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="d6e74-137">Otwórz plik projektu `.csproj` i Dodaj `<EnableRegFreeCom>true</EnableRegFreeCom>` wewnątrz tagu `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="d6e74-138">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="d6e74-138">Build the project.</span></span>

<span data-ttu-id="d6e74-139">Wynikowe dane wyjściowe będą teraz również mieć plik `ProjectName.X.manifest`.</span><span class="sxs-lookup"><span data-stu-id="d6e74-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="d6e74-140">Ten plik jest manifestem równoległym do użycia z modelem COM bez rejestru.</span><span class="sxs-lookup"><span data-stu-id="d6e74-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="d6e74-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6e74-141">Sample</span></span>

<span data-ttu-id="d6e74-142">Istnieje w pełni funkcjonalny [przykład serwera com](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) w repozytorium dotnet/Samples w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="d6e74-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="d6e74-143">Dodatkowe uwagi</span><span class="sxs-lookup"><span data-stu-id="d6e74-143">Additional notes</span></span>

<span data-ttu-id="d6e74-144">W przeciwieństwie do .NET Framework, nie ma obsługi w programie .NET Core do generowania biblioteki typów modelu COM (TLB) z zestawu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e74-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="d6e74-145">Wskazówki dotyczą ręcznego zapisywania pliku IDL lub C/C++ nagłówka dla natywnych deklaracji interfejsów com.</span><span class="sxs-lookup"><span data-stu-id="d6e74-145">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="d6e74-146">Ponadto ładowanie obu .NET Framework i .NET Core do tego samego procesu ma ograniczenia diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="d6e74-146">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="d6e74-147">Głównym ograniczeniem jest debugowanie składników zarządzanych, ponieważ nie jest możliwe debugowanie jednocześnie .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e74-147">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="d6e74-148">Ponadto dwa wystąpienia środowiska uruchomieniowego nie współdzielą zestawów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d6e74-148">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="d6e74-149">Oznacza to, że nie jest możliwe udostępnianie rzeczywistych typów .NET między dwoma środowiskami uruchomieniowymi, a w zamian wszystkie interakcje muszą być ograniczone do umów dotyczących interfejsów COM.</span><span class="sxs-lookup"><span data-stu-id="d6e74-149">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
