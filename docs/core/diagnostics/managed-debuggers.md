---
title: Zarządzane debugery - .NET Core
description: Przegląd debugerów zarządzanych przez program Visual Studio i Visual Studio Code.
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715565"
---
# <a name="net-core-managed-debuggers"></a>Debugery zarządzane przez program .NET Core

Debuggery umożliwiają wstrzymywanie lub wykonywania programów krok po kroku. Po wstrzymaniu można wyświetlić bieżący stan procesu. Przez krok po kroku kluczowych sekcji, można uzyskać zrozumienie kodu i dlaczego daje wynik, który robi.

Firma Microsoft udostępnia debugery kodu zarządzanego w **programie Visual Studio** i Visual Studio **Code**.

## <a name="visual-studio-managed-debugger"></a>Debuger zarządzany w programie Visual Studio

**Visual Studio** to zintegrowane środowisko programistyczne z najbardziej wszechstronnym debugerem. Visual Studio to doskonały wybór dla programistów pracujących w systemie Windows.

- [Samouczek — debugowanie aplikacji .NET Core w systemie Windows za pomocą programu Visual Studio](../tutorials/debugging-with-visual-studio.md)

Program Visual Studio jest aplikacją systemu Windows, ale nadal może być używany do zdalnego debugowania aplikacji systemu Linux i systemu macOS.

- [Debugowanie aplikacji .NET Core w systemie Linux/OSX za pomocą programu Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 Debugowanie ASP.NET aplikacje Core wymagają nieco innych instrukcji.

- [Debugowanie aplikacji ASP.NET Core w programie Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Debuger zarządzany przez kod programu Visual Studio

**Visual Studio Code** to lekki edytor kodu między platformami. Używa tej samej implementacji debugera .NET Core co Visual Studio, ale z uproszczonym interfejsem użytkownika.

- [Samouczek — debugowanie aplikacji .NET Core za pomocą kodu programu Visual Studio](../tutorials/with-visual-studio-code.md#debug)
- [Debugowanie w kodzie programu Visual Studio](https://code.visualstudio.com/docs/editor/debugging)
