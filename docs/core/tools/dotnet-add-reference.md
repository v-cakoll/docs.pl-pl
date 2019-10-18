---
title: dotnet-Dodaj polecenie referencyjne
description: Polecenie "Dodaj odwołanie" dotnet udostępnia wygodną opcję dodawania projektu do odwołań do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: 79c8a787079e02f6cf227820c24bb4157b0292c6
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522768"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="be8c0-103">dotnet — Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="be8c0-103">dotnet-add reference</span></span>

<span data-ttu-id="be8c0-104">**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="be8c0-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="be8c0-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="be8c0-105">Name</span></span>

<span data-ttu-id="be8c0-106">`dotnet add reference` — dodaje odwołania projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="be8c0-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="be8c0-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="be8c0-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="be8c0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="be8c0-108">Description</span></span>

<span data-ttu-id="be8c0-109">Polecenie `dotnet add reference` udostępnia wygodną opcję dodawania odwołań projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="be8c0-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="be8c0-110">Po uruchomieniu polecenia elementy `<ProjectReference>` są dodawane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="be8c0-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="be8c0-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="be8c0-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="be8c0-112">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="be8c0-112">Specifies the project file.</span></span> <span data-ttu-id="be8c0-113">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="be8c0-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="be8c0-114">Odwołania projektu do projektu (P2P) do dodania.</span><span class="sxs-lookup"><span data-stu-id="be8c0-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="be8c0-115">Określ jeden lub więcej projektów.</span><span class="sxs-lookup"><span data-stu-id="be8c0-115">Specify one or more projects.</span></span> <span data-ttu-id="be8c0-116">[Wzorce globalizowania](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="be8c0-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="be8c0-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="be8c0-117">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="be8c0-118">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="be8c0-118">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="be8c0-119">Dodaje odwołania do projektu tylko w przypadku określania konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="be8c0-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`--interactive`**

  <span data-ttu-id="be8c0-120">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="be8c0-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="be8c0-121">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="be8c0-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="be8c0-122">Przykłady</span><span class="sxs-lookup"><span data-stu-id="be8c0-122">Examples</span></span>

- <span data-ttu-id="be8c0-123">Dodaj odwołanie do projektu:</span><span class="sxs-lookup"><span data-stu-id="be8c0-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="be8c0-124">Dodaj wiele odwołań projektu do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="be8c0-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="be8c0-125">Dodaj odwołania do wielu projektów za pomocą wzorca obsługi symboli wieloznacznych w systemie Linux/UNIX:</span><span class="sxs-lookup"><span data-stu-id="be8c0-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
