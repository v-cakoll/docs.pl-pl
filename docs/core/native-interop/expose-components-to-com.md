---
title: Udostępnianie składników .NET Core w ucho.
description: W tym samouczku pokazano, jak udostępnić klasę com z platformy .NET Core. Wygenerujesz serwer COM i manifest serwera side-by-side dla com bez rejestru.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 17d85b9e9734fae0bb69f94da8c08669216ab0ae
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242871"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="1387c-104">Udostępnianie składników .NET Core w ucho.</span><span class="sxs-lookup"><span data-stu-id="1387c-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="1387c-105">W .NET Core proces wystawiania obiektów platformy .NET na urządzenie .NET został znacznie usprawniony w porównaniu z programem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1387c-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="1387c-106">Poniższy proces poprowadzi Cię przez jak udostępnić klasę do COM.</span><span class="sxs-lookup"><span data-stu-id="1387c-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="1387c-107">Ten samouczek przedstawia sposób wykonania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1387c-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="1387c-108">Uwidacznianie klasy do com z .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1387c-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="1387c-109">Generowanie serwera COM w ramach tworzenia biblioteki .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1387c-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="1387c-110">Automatycznie wygeneruj manifest serwera obok siebie dla com bez rejestru.</span><span class="sxs-lookup"><span data-stu-id="1387c-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1387c-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1387c-111">Prerequisites</span></span>

- <span data-ttu-id="1387c-112">Zainstaluj [pakiet .NET Core 3.0 SDK](https://dotnet.microsoft.com/download) lub nowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="1387c-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="1387c-113">Tworzenie biblioteki</span><span class="sxs-lookup"><span data-stu-id="1387c-113">Create the library</span></span>

<span data-ttu-id="1387c-114">Pierwszym krokiem jest utworzenie biblioteki.</span><span class="sxs-lookup"><span data-stu-id="1387c-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="1387c-115">Utwórz nowy folder, a w tym folderze uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="1387c-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="1387c-116">Otwórz plik `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="1387c-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="1387c-117">Dodaj `using System.Runtime.InteropServices;` do górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="1387c-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="1387c-118">Tworzenie interfejsu `IServer`o nazwie .</span><span class="sxs-lookup"><span data-stu-id="1387c-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="1387c-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1387c-119">For example:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. <span data-ttu-id="1387c-120">Dodaj `[Guid("<IID>")]` atrybut do interfejsu z identyfikatorem GUID interfejsu interfejsu com, który implementujesz.</span><span class="sxs-lookup"><span data-stu-id="1387c-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="1387c-121">Na przykład `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="1387c-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="1387c-122">Należy zauważyć, że ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu dla com.</span><span class="sxs-lookup"><span data-stu-id="1387c-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="1387c-123">W programie Visual Studio można wygenerować identyfikator GUID, przechodząc do narzędzia > tworzenie identyfikatora GUID, aby otworzyć narzędzie Tworzenie identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="1387c-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="1387c-124">Dodaj `[InterfaceType]` atrybut do interfejsu i określ, jakie podstawowe interfejsy COM interfejs powinien zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="1387c-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="1387c-125">Utwórz klasę `Server` o `IServer`nazwie, która implementuje .</span><span class="sxs-lookup"><span data-stu-id="1387c-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="1387c-126">Dodaj `[Guid("<CLSID>")]` atrybut do klasy z identyfikatorem klasy guiD dla klasy COM, którą implementujesz.</span><span class="sxs-lookup"><span data-stu-id="1387c-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="1387c-127">Na przykład `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="1387c-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="1387c-128">Podobnie jak w interfejsie GUID interfejsu, ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu do com.</span><span class="sxs-lookup"><span data-stu-id="1387c-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="1387c-129">Dodaj `[ComVisible(true)]` atrybut do interfejsu i klasy.</span><span class="sxs-lookup"><span data-stu-id="1387c-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1387c-130">W przeciwieństwie do programu .NET Framework program .NET Core wymaga określenia clsid dowolnej klasy, którą chcesz aktywować za pośrednictwem programu COM.</span><span class="sxs-lookup"><span data-stu-id="1387c-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="1387c-131">Generowanie hosta COM</span><span class="sxs-lookup"><span data-stu-id="1387c-131">Generate the COM host</span></span>

1. <span data-ttu-id="1387c-132">Otwórz `.csproj` plik projektu `<EnableComHosting>true</EnableComHosting>` i `<PropertyGroup></PropertyGroup>` dodaj go wewnątrz znacznika.</span><span class="sxs-lookup"><span data-stu-id="1387c-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="1387c-133">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="1387c-133">Build the project.</span></span>

<span data-ttu-id="1387c-134">Wynikowy wynik będzie `ProjectName.dll`miał `ProjectName.deps.json` `ProjectName.runtimeconfig.json` plik `ProjectName.comhost.dll` , i plik.</span><span class="sxs-lookup"><span data-stu-id="1387c-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="1387c-135">Zarejestruj hosta COM dla com</span><span class="sxs-lookup"><span data-stu-id="1387c-135">Register the COM host for COM</span></span>

<span data-ttu-id="1387c-136">Otwórz wiersz polecenia z `regsvr32 ProjectName.comhost.dll`podwyższonym poziomem uprawnień i uruchom polecenie .</span><span class="sxs-lookup"><span data-stu-id="1387c-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="1387c-137">Spowoduje to zarejestrowanie wszystkich obiektów platformy .NET w aplikacji COM.</span><span class="sxs-lookup"><span data-stu-id="1387c-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="1387c-138">Włączanie regfree COM</span><span class="sxs-lookup"><span data-stu-id="1387c-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="1387c-139">Otwórz `.csproj` plik projektu `<EnableRegFreeCom>true</EnableRegFreeCom>` i `<PropertyGroup></PropertyGroup>` dodaj go wewnątrz znacznika.</span><span class="sxs-lookup"><span data-stu-id="1387c-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="1387c-140">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="1387c-140">Build the project.</span></span>

<span data-ttu-id="1387c-141">Wynikowe dane wyjściowe będą `ProjectName.X.manifest` teraz również mieć plik.</span><span class="sxs-lookup"><span data-stu-id="1387c-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="1387c-142">Ten plik jest manifestem side-by-side do użytku z com bez rejestru.</span><span class="sxs-lookup"><span data-stu-id="1387c-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="1387c-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="1387c-143">Sample</span></span>

<span data-ttu-id="1387c-144">Istnieje w pełni funkcjonalny [przykład serwera COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) w repozytorium dotnet/samples w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="1387c-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="1387c-145">Uwagi dodatkowe</span><span class="sxs-lookup"><span data-stu-id="1387c-145">Additional notes</span></span>

<span data-ttu-id="1387c-146">W przeciwieństwie do programu .NET Framework w systemie .NET Core nie ma obsługi generowania biblioteki typów COM (TLB) z zestawu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1387c-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="1387c-147">Wskazówki są albo ręcznie napisać plik IDL lub nagłówek C/C++ dla natywnych deklaracji interfejsów COM.</span><span class="sxs-lookup"><span data-stu-id="1387c-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="1387c-148">[Samodzielne wdrożenia](../deploying/index.md#publish-self-contained) składników COM nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1387c-148">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="1387c-149">Obsługiwane są tylko [wdrożenia zależne od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) składników COM.</span><span class="sxs-lookup"><span data-stu-id="1387c-149">Only [runtime-dependent deployments](../deploying/index.md#publish-runtime-dependent) of COM components are supported.</span></span>

<span data-ttu-id="1387c-150">Ponadto ładowanie programu .NET Framework i .NET Core do tego samego procesu ma ograniczenia diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="1387c-150">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="1387c-151">Podstawowym ograniczeniem jest debugowanie składników zarządzanych, ponieważ nie jest możliwe debugowanie zarówno platformy .NET Framework, jak i .NET Core w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="1387c-151">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="1387c-152">Ponadto dwa wystąpienia środowiska uruchomieniowego nie współużytkują zestawy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="1387c-152">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="1387c-153">Oznacza to, że nie jest możliwe udostępnianie rzeczywistych typów .NET w dwóch środowiskach wykonywania, a zamiast tego wszystkie interakcje muszą być ograniczone do umów interfejsu COM narażonych.</span><span class="sxs-lookup"><span data-stu-id="1387c-153">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
