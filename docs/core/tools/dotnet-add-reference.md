---
title: polecenie "Add Reference" dotnet
description: Polecenie "Dodaj odwołanie" dotnet udostępnia wygodną opcję dodawania projektu do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: b261e24ed6a9d5bd489d317d2663b1420b5c34ff
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158323"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="a3738-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="a3738-103">dotnet add reference</span></span>

<span data-ttu-id="a3738-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="a3738-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a3738-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a3738-105">Name</span></span>

<span data-ttu-id="a3738-106">`dotnet add reference`-Dodaje odwołania projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="a3738-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a3738-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a3738-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a><span data-ttu-id="a3738-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a3738-108">Description</span></span>

<span data-ttu-id="a3738-109">`dotnet add reference` Polecenie udostępnia wygodną opcję dodawania odwołań projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="a3738-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="a3738-110">Po uruchomieniu polecenia `<ProjectReference>` elementy są dodawane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a3738-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="a3738-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a3738-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="a3738-112">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="a3738-112">Specifies the project file.</span></span> <span data-ttu-id="a3738-113">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="a3738-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="a3738-114">Odwołania projektu do projektu (P2P) do dodania.</span><span class="sxs-lookup"><span data-stu-id="a3738-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="a3738-115">Określ jeden lub więcej projektów.</span><span class="sxs-lookup"><span data-stu-id="a3738-115">Specify one or more projects.</span></span> <span data-ttu-id="a3738-116">[Wzorce globalizowania](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="a3738-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="a3738-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="a3738-117">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a3738-118">Dodaje odwołania do projektu tylko w przypadku określenia konkretnej [struktury](../../standard/frameworks.md) przy użyciu formatu TFM.</span><span class="sxs-lookup"><span data-stu-id="a3738-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a3738-119">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a3738-119">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="a3738-120">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (zazwyczaj używany do całkowitego uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="a3738-120">Allows the command to stop and wait for user input or action (typically used to complete authentication).</span></span> <span data-ttu-id="a3738-121">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a3738-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="a3738-122">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a3738-122">Examples</span></span>

- <span data-ttu-id="a3738-123">Dodaj odwołanie do projektu:</span><span class="sxs-lookup"><span data-stu-id="a3738-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="a3738-124">Dodaj wiele odwołań projektu do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a3738-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="a3738-125">Dodaj odwołania do wielu projektów za pomocą wzorca obsługi symboli wieloznacznych w systemie Linux/UNIX:</span><span class="sxs-lookup"><span data-stu-id="a3738-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
