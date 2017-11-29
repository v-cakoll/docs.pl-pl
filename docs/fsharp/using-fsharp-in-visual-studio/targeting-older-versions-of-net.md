---
title: Kierowanie dla programu .NET Framework 2.0 w systemie Windows 8
description: "Informacje o przeznaczonych dla starszej wersji programu .NET Framework przy użyciu języka F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63989543-95c3-4ab7-81f3-3834a8b15010
ms.openlocfilehash: 2c0191267da5bee7b844c11cdee168ccfb3321c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="targeting-older-versions-of-net"></a><span data-ttu-id="0ca42-104">Przeznaczony dla starszej wersji programu .NET</span><span class="sxs-lookup"><span data-stu-id="0ca42-104">Targeting Older Versions of .NET</span></span>

> [!NOTE]
<span data-ttu-id="0ca42-105">W tym artykule nie jest aktualny najnowsze Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ca42-105">This article is not up to date with the latest Visual Studio.</span></span>  <span data-ttu-id="0ca42-106">Zostaną zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="0ca42-106">It will be updated.</span></span>

<span data-ttu-id="0ca42-107">Następujący błąd może wystąpić, Jeśli spróbujesz docelową programu .NET Framework 2.0, 3.0 lub 3.5 w języku F # projektu programu Visual Studio jest zainstalowany na Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="0ca42-107">The following error might appear if you try to target the .NET Framework 2.0, 3.0, or 3.5 in an F# project when Visual Studio is installed on Windows 8.1:</span></span> 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

<span data-ttu-id="0ca42-108">Wiadomo, że ten błąd występuje w następujących kombinacji warunki:</span><span class="sxs-lookup"><span data-stu-id="0ca42-108">This error is known to occur under the following combination of conditions:</span></span>


- <span data-ttu-id="0ca42-109">Visual Studio jest zainstalowany na Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="0ca42-109">You installed Visual Studio on Windows 8.1.</span></span>
<br />

- <span data-ttu-id="0ca42-110">Nie można włączyć program .NET Framework 3.5 przed zainstalowaniem programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ca42-110">You didn’t enable the .NET Framework 3.5 before you installed Visual Studio.</span></span>
<br />

- <span data-ttu-id="0ca42-111">Projekt jest przeznaczony dla programu .NET Framework 2.0, 3.0 lub 3.5.</span><span class="sxs-lookup"><span data-stu-id="0ca42-111">Your project targets the .NET Framework 2.0, 3.0, or 3.5.</span></span>
<br />

<span data-ttu-id="0ca42-112">Po zainstalowaniu programu Visual Studio wykryje zainstalowanych wersji programu .NET Framework i instaluje środowisko uruchomieniowe 2.0 F # tylko w przypadku programu .NET Framework 3.5 jest zainstalowany i włączony.</span><span class="sxs-lookup"><span data-stu-id="0ca42-112">When you install Visual Studio, it detects the installed versions of the .NET Framework and installs the F# 2.0 Runtime only if the .NET Framework 3.5 is installed and enabled.</span></span>


## <a name="resolving-the-error"></a><span data-ttu-id="0ca42-113">Rozwiązywanie błędu</span><span class="sxs-lookup"><span data-stu-id="0ca42-113">Resolving the Error</span></span>
<span data-ttu-id="0ca42-114">Aby rozwiązać ten problem, można miejsca docelowego nowszej wersji programu .NET Framework lub należy włączyć dla programu .NET Framework 3.5 na Windows 8.1, a następnie zainstalować środowiska uruchomieniowego języka F # 2.0, uruchamiając Instalatora programu Visual Studio z **naprawy** Opcja.</span><span class="sxs-lookup"><span data-stu-id="0ca42-114">To resolve this error, you can either target a newer version of the .NET Framework, or you can enable the .NET Framework 3.5 on Windows 8.1 and then install the F# 2.0 runtime by running the setup program for Visual Studio with the **Repair** option.</span></span>


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a><span data-ttu-id="0ca42-115">Aby włączyć dla programu .NET Framework 3.5 na Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="0ca42-115">To enable the .NET Framework 3.5 on Windows 8.1</span></span>

1. <span data-ttu-id="0ca42-116">Na **Start** ekranu, uruchom, aby wprowadzić **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="0ca42-116">On the **Start** screen, start to enter **Control Panel**.</span></span>
<br />  <span data-ttu-id="0ca42-117">Po wprowadzeniu tej samej nazwie, **Panelu sterowania** ikona jest wyświetlana w obszarze **aplikacji** nagłówka.</span><span class="sxs-lookup"><span data-stu-id="0ca42-117">As you enter that name, the **Control Panel** icon appears under the **Apps** heading.</span></span>
<br />

2. <span data-ttu-id="0ca42-118">Wybierz **Panelu sterowania** ikony, wybierz **programy** ikony, a następnie wybierz pozycję **Włącz lub wyłącz funkcje systemu Windows** łącza.</span><span class="sxs-lookup"><span data-stu-id="0ca42-118">Choose the **Control Panel** icon, choose the **Programs** icon, and then choose the **Turn Windows features on or off** link.</span></span>
<br />

3. <span data-ttu-id="0ca42-119">Upewnij się, że **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** pole wyboru jest zaznaczone, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0ca42-119">Make sure that the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box is selected, and then choose the **OK** button.</span></span>
<br />  <span data-ttu-id="0ca42-120">Nie trzeba zaznacz pola wyboru dla dowolnej węzłów podrzędnych dla składników opcjonalnych programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ca42-120">You don’t need to select the check boxes for any child nodes for optional components of the .NET Framework.</span></span>
<br />  <span data-ttu-id="0ca42-121">.NET Framework 3.5 jest włączona, jeśli nie był już.</span><span class="sxs-lookup"><span data-stu-id="0ca42-121">The .NET Framework 3.5 is enabled if it wasn't already.</span></span>
<br />


#### <a name="to-install-the-f-20-runtime"></a><span data-ttu-id="0ca42-122">Aby zainstalować środowisko uruchomieniowe języka F # 2.0</span><span class="sxs-lookup"><span data-stu-id="0ca42-122">To install the F# 2.0 runtime</span></span>

1. <span data-ttu-id="0ca42-123">W Panelu sterowania, wybierz **programy** łącza, a następnie wybierz pozycję **programy i funkcje** łącza.</span><span class="sxs-lookup"><span data-stu-id="0ca42-123">In the Control Panel, choose the **Programs** link, and then choose the **Programs and Features** link.</span></span>
<br />

2. <span data-ttu-id="0ca42-124">Na liście zainstalowanych programów, wybierz wersji programu Visual Studio, która jest zainstalowana, a następnie wybierz pozycję **zmiany** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0ca42-124">In the list of installed programs, choose the edition of Visual Studio that you installed, and then choose the **Change** button.</span></span>
<br />

3. <span data-ttu-id="0ca42-125">Po uruchomieniu Instalatora, wybierz **naprawy** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0ca42-125">After setup starts, choose the **Repair** button.</span></span>
<br />  <span data-ttu-id="0ca42-126">Aby uzyskać więcej informacji, zobacz [Instalowanie programu Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span><span class="sxs-lookup"><span data-stu-id="0ca42-126">For more information, see [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span></span>
<br />
## <a name="see-also"></a><span data-ttu-id="0ca42-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ca42-127">See Also</span></span>
[<span data-ttu-id="0ca42-128">Visual F #</span><span class="sxs-lookup"><span data-stu-id="0ca42-128">Visual F#</span></span>](../index.md)
