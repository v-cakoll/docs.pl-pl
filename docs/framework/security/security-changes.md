---
title: Zmiany zabezpieczeń w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204505"
---
# <a name="security-changes-in-the-net-framework"></a>Zmiany zabezpieczeń w programie .NET Framework

Najważniejsze zmiany zabezpieczeń w .NET Framework 4,5 są w silnym nazewnictwie. Aby uzyskać opis tych zmian, zobacz [ulepszona silna nazwa](../../standard/assembly/enhanced-strong-naming.md) .  
  
.NET Framework zapewnia dwuwarstwowy model zabezpieczeń dla aplikacji zarządzanych. Aplikacje ze sklepu Windows 8. x działają w kontenerze zabezpieczeń systemu Windows, który ogranicza dostęp do zasobów. W tym kontenerze aplikacje zarządzane działają w pełni zaufane. Z punktu widzenia zabezpieczeń dostępu kodu (CAS) nie ma niczego, aby deweloperzy mogli podwyższyć poziom uprawnień. Aby uzyskać informacje o uprawnieniach przyznanych przez system Windows, zobacz [deklaracje możliwości aplikacji (aplikacje ze sklepu Windows)](https://go.microsoft.com/fwlink/?LinkId=230436) w centrum deweloperów systemu Windows. Aby uzyskać informacje na temat tworzenia aplikacji do sklepu Windows 8. x, zobacz [Tworzenie pierwszej aplikacji do sklepu C# Windows przy użyciu lub Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
