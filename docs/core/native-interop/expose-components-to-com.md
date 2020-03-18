---
title: Wystawianie składników .NET Core do com
description: W tym samouczku pokazano, jak udostępnić klasę do com z .NET Core. Serwer COM i manifest serwera side-by-side dla com bez rejestru.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 98d303c99693a8aadb23da509a700772db69c0e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146661"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="18af9-104">Wystawianie składników .NET Core do com</span><span class="sxs-lookup"><span data-stu-id="18af9-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="18af9-105">W .NET Core proces ujawniania obiektów .NET do com został znacznie usprawniony w porównaniu do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18af9-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="18af9-106">Poniższy proces przeprowadzi Cię przez jak udostępnić klasy do COM.</span><span class="sxs-lookup"><span data-stu-id="18af9-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="18af9-107">Ten samouczek przedstawia sposób wykonania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="18af9-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="18af9-108">Uwidaczniaklasę do com z .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18af9-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="18af9-109">Wygeneruj serwer COM w ramach tworzenia biblioteki .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18af9-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="18af9-110">Automatycznie generuj manifest serwera side-by-side dla com bez rejestru.</span><span class="sxs-lookup"><span data-stu-id="18af9-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18af9-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="18af9-111">Prerequisites</span></span>

- <span data-ttu-id="18af9-112">Zainstaluj [zestaw SDK .NET Core 3.0](https://dotnet.microsoft.com/download) lub nowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="18af9-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="18af9-113">Tworzenie biblioteki</span><span class="sxs-lookup"><span data-stu-id="18af9-113">Create the library</span></span>

<span data-ttu-id="18af9-114">Pierwszym krokiem jest utworzenie biblioteki.</span><span class="sxs-lookup"><span data-stu-id="18af9-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="18af9-115">Utwórz nowy folder, a w tym folderze uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="18af9-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="18af9-116">Otwórz plik `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="18af9-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="18af9-117">Dodaj `using System.Runtime.InteropServices;` do górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="18af9-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="18af9-118">Utwórz interfejs `IServer`o nazwie .</span><span class="sxs-lookup"><span data-stu-id="18af9-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="18af9-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="18af9-119">For example:</span></span>

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

5. <span data-ttu-id="18af9-120">Dodaj `[Guid("<IID>")]` atrybut do interfejsu, z interfejsem GUID dla interfejsu COM, który implementujesz.</span><span class="sxs-lookup"><span data-stu-id="18af9-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="18af9-121">Na przykład `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="18af9-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="18af9-122">Należy zauważyć, że ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="18af9-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="18af9-123">W programie Visual Studio można wygenerować identyfikator GUID, przechodząc do narzędzia > tworzenie identyfikatora GUID, aby otworzyć narzędzie Tworzenie identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="18af9-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="18af9-124">Dodaj `[InterfaceType]` atrybut do interfejsu i określ, jakie podstawowe interfejsy COM powinien zaimplementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="18af9-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="18af9-125">Utwórz klasę `Server` o `IServer`nazwie, która implementuje .</span><span class="sxs-lookup"><span data-stu-id="18af9-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="18af9-126">Dodaj `[Guid("<CLSID>")]` atrybut do klasy, z identyfikatorem identyfikatora klasy GUID dla klasy COM, którą implementujesz.</span><span class="sxs-lookup"><span data-stu-id="18af9-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="18af9-127">Na przykład `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="18af9-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="18af9-128">Podobnie jak w interfejsie GUID, ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu do modelu COM.</span><span class="sxs-lookup"><span data-stu-id="18af9-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="18af9-129">Dodaj `[ComVisible(true)]` atrybut do interfejsu i klasy.</span><span class="sxs-lookup"><span data-stu-id="18af9-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18af9-130">W przeciwieństwie do programu .NET Framework program .NET Core wymaga określenia identyfikatora CLSID dowolnej klasy, którą chcesz aktywować za pośrednictwem systemu COM.</span><span class="sxs-lookup"><span data-stu-id="18af9-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="18af9-131">Generowanie hosta COM</span><span class="sxs-lookup"><span data-stu-id="18af9-131">Generate the COM host</span></span>

1. <span data-ttu-id="18af9-132">Otwórz `.csproj` plik projektu `<EnableComHosting>true</EnableComHosting>` i `<PropertyGroup></PropertyGroup>` dodaj wewnątrz znacznika.</span><span class="sxs-lookup"><span data-stu-id="18af9-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="18af9-133">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="18af9-133">Build the project.</span></span>

<span data-ttu-id="18af9-134">Wynikowe dane wyjściowe `ProjectName.dll` `ProjectName.deps.json`będą `ProjectName.runtimeconfig.json` `ProjectName.comhost.dll` miały , i plik.</span><span class="sxs-lookup"><span data-stu-id="18af9-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="18af9-135">Zarejestruj hosta COM dla COM</span><span class="sxs-lookup"><span data-stu-id="18af9-135">Register the COM host for COM</span></span>

<span data-ttu-id="18af9-136">Otwórz wiersz polecenia z `regsvr32 ProjectName.comhost.dll`podwyższonym poziomem uprawnień i uruchom .</span><span class="sxs-lookup"><span data-stu-id="18af9-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="18af9-137">Spowoduje to zarejestrowanie wszystkich narażonych obiektów .NET w kom.</span><span class="sxs-lookup"><span data-stu-id="18af9-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="18af9-138">Włączanie regfree COM</span><span class="sxs-lookup"><span data-stu-id="18af9-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="18af9-139">Otwórz `.csproj` plik projektu `<EnableRegFreeCom>true</EnableRegFreeCom>` i `<PropertyGroup></PropertyGroup>` dodaj wewnątrz znacznika.</span><span class="sxs-lookup"><span data-stu-id="18af9-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="18af9-140">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="18af9-140">Build the project.</span></span>

<span data-ttu-id="18af9-141">Wynikowe dane wyjściowe będą `ProjectName.X.manifest` teraz również mieć plik.</span><span class="sxs-lookup"><span data-stu-id="18af9-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="18af9-142">Ten plik jest manifestem side-by-side do użytku z com bez rejestru.</span><span class="sxs-lookup"><span data-stu-id="18af9-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="18af9-143">Sample</span><span class="sxs-lookup"><span data-stu-id="18af9-143">Sample</span></span>

<span data-ttu-id="18af9-144">W [repozytorium](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) dotnet/samples w githubie znajduje się w pełni funkcjonalny przykład serwera COM.</span><span class="sxs-lookup"><span data-stu-id="18af9-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="18af9-145">Uwagi dodatkowe</span><span class="sxs-lookup"><span data-stu-id="18af9-145">Additional notes</span></span>

<span data-ttu-id="18af9-146">W przeciwieństwie do programu .NET Framework w platformie .NET Core nie ma obsługi generowania biblioteki typów COM (TLB) z zestawu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18af9-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="18af9-147">Wskazówki dotyczące ręcznego zapisu pliku IDL lub nagłówka C/C++ dla natywnych deklaracji interfejsów COM.</span><span class="sxs-lookup"><span data-stu-id="18af9-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="18af9-148">Ponadto ładowanie zarówno .NET Framework i .NET Core do tego samego procesu ma ograniczenia diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="18af9-148">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="18af9-149">Podstawowym ograniczeniem jest debugowanie zarządzanych składników, ponieważ nie jest możliwe debugowanie zarówno .NET Framework, jak i .NET Core w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="18af9-149">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="18af9-150">Ponadto dwa wystąpienia czasu uruchomieniowego nie współużytkują zestawów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="18af9-150">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="18af9-151">Oznacza to, że nie jest możliwe udostępnianie rzeczywistych typów platformy .NET w dwóch wykonawczych i zamiast tego wszystkie interakcje muszą być ograniczone do kontraktów interfejsu uniewinnionego com.</span><span class="sxs-lookup"><span data-stu-id="18af9-151">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
