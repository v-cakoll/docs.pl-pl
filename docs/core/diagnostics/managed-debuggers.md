---
title: Zarządzane debugery — .NET Core
description: Przegląd programów Visual Studio i Visual Studio Code Managed Debuggers.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 8110ecb10ad2e6213e15df8848abab73d07d89b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974133"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="66d11-103">Zarządzane debugery programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="66d11-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="66d11-104">Debugery umożliwiają Wstrzymywanie lub wykonywanie programów krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="66d11-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="66d11-105">W przypadku wstrzymania bieżący stan procesu może być wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="66d11-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="66d11-106">Poprzez przechodzenie przez najważniejsze sekcje, możesz zrozumieć swój kod i dlaczego generuje wynik.</span><span class="sxs-lookup"><span data-stu-id="66d11-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="66d11-107">Firma Microsoft udostępnia debugery dla kodu zarządzanego w programie **Visual Studio** i **Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="66d11-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="66d11-108">Debuger zarządzany programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66d11-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="66d11-109">**Program Visual Studio** to zintegrowane środowisko programistyczne z najpełniejszym dostępnym debugerem.</span><span class="sxs-lookup"><span data-stu-id="66d11-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="66d11-110">Program Visual Studio to doskonały wybór dla deweloperów pracujących nad systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="66d11-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>
- [<span data-ttu-id="66d11-111">Samouczek — debugowanie aplikacji .NET Core w systemie Windows przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66d11-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="66d11-112">Mimo że program Visual Studio jest aplikacją systemu Windows, może być nadal używany do zdalnego debugowania aplikacji Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="66d11-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>
- [<span data-ttu-id="66d11-113">Debugowanie aplikacji .NET Core w systemie Linux/OSX przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66d11-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="66d11-114">Debugowanie ASP.NET Core aplikacji wymaga nieco innych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="66d11-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="66d11-115">Debugowanie aplikacji ASP.NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66d11-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="66d11-116">Debuger zarządzanego Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66d11-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="66d11-117">**Visual Studio Code** to lekki Edytor kodu dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="66d11-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="66d11-118">Używa tej samej implementacji debugera platformy .NET Core jako programu Visual Studio, ale przy użyciu uproszczonego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="66d11-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="66d11-119">Samouczek — debugowanie aplikacji .NET Core za pomocą Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66d11-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="66d11-120">Debugowanie w Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66d11-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
