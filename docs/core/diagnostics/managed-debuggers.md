---
title: Zarządzane debugery — .NET Core
description: Przegląd programów Visual Studio i Visual Studio Code Managed Debuggers.
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715565"
---
# <a name="net-core-managed-debuggers"></a>Zarządzane debugery programu .NET Core

Debugery umożliwiają Wstrzymywanie lub wykonywanie programów krok po kroku. W przypadku wstrzymania bieżący stan procesu może być wyświetlany. Poprzez przechodzenie przez najważniejsze sekcje, możesz zrozumieć swój kod i dlaczego generuje wynik.

Firma Microsoft udostępnia debugery dla kodu zarządzanego w programie **Visual Studio** i **Visual Studio Code**.

## <a name="visual-studio-managed-debugger"></a>Debuger zarządzany programu Visual Studio

**Program Visual Studio** to zintegrowane środowisko programistyczne z najpełniejszym dostępnym debugerem. Program Visual Studio to doskonały wybór dla deweloperów pracujących nad systemem Windows.

- [Samouczek — debugowanie aplikacji .NET Core w systemie Windows przy użyciu programu Visual Studio](../tutorials/debugging-with-visual-studio.md)

Mimo że program Visual Studio jest aplikacją systemu Windows, może być nadal używany do zdalnego debugowania aplikacji Linux i macOS.

- [Debugowanie aplikacji .NET Core w systemie Linux/OSX przy użyciu programu Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 Debugowanie ASP.NET Core aplikacji wymaga nieco innych instrukcji.

- [Debugowanie aplikacji ASP.NET Core w programie Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Debuger zarządzanego Visual Studio Code

**Visual Studio Code** to lekki Edytor kodu dla wielu platform. Używa tej samej implementacji debugera platformy .NET Core jako programu Visual Studio, ale przy użyciu uproszczonego interfejsu użytkownika.

- [Samouczek — debugowanie aplikacji .NET Core za pomocą Visual Studio Code](../tutorials/with-visual-studio-code.md#debug)
- [Debugowanie w Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)
