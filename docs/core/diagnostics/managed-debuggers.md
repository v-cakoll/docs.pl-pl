---
title: Zarządzane debugery — .NET Core
description: Przegląd programów Visual Studio i Visual Studio Code Managed Debuggers.
ms.date: 08/05/2019
ms.openlocfilehash: 28cc21980bc78234f7af3b4668e2fa77fbf8ce5b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84200862"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="83a69-103">Zarządzane debugery programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="83a69-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="83a69-104">Debugery umożliwiają Wstrzymywanie lub wykonywanie programów krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="83a69-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="83a69-105">W przypadku wstrzymania bieżący stan procesu może być wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="83a69-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="83a69-106">Poprzez przechodzenie przez najważniejsze sekcje, możesz zrozumieć swój kod i dlaczego generuje wynik.</span><span class="sxs-lookup"><span data-stu-id="83a69-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="83a69-107">Firma Microsoft udostępnia debugery dla kodu zarządzanego w programie **Visual Studio** i **Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="83a69-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="83a69-108">Debuger zarządzany programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83a69-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="83a69-109">**Program Visual Studio** to zintegrowane środowisko programistyczne z najpełniejszym dostępnym debugerem.</span><span class="sxs-lookup"><span data-stu-id="83a69-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="83a69-110">Program Visual Studio to doskonały wybór dla deweloperów pracujących nad systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="83a69-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="83a69-111">Samouczek — debugowanie aplikacji .NET Core w systemie Windows przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83a69-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="83a69-112">Mimo że program Visual Studio jest aplikacją systemu Windows, może być nadal używany do zdalnego debugowania aplikacji Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="83a69-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="83a69-113">Debugowanie aplikacji .NET Core w systemie Linux/OSX przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83a69-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="83a69-114">Debugowanie ASP.NET Core aplikacji wymaga nieco innych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="83a69-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="83a69-115">Debugowanie aplikacji ASP.NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83a69-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="83a69-116">Debuger zarządzanego Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="83a69-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="83a69-117">**Visual Studio Code** to lekki Edytor kodu dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="83a69-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="83a69-118">Używa tej samej implementacji debugera platformy .NET Core jako programu Visual Studio, ale przy użyciu uproszczonego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83a69-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="83a69-119">Samouczek — debugowanie aplikacji .NET Core za pomocą Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="83a69-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/debugging-with-visual-studio-code.md)
- [<span data-ttu-id="83a69-120">Debugowanie w Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="83a69-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
