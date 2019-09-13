---
title: Zarządzane debugery — .NET Core
description: Przegląd programów Visual Studio i Visual Studio Code Managed Debuggers.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 3741011d22ab6c4240b7f88a9ab790ea61ecd0d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926439"
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
