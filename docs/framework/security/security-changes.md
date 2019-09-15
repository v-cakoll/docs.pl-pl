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
ms.openlocfilehash: bfc48d4fed127b288353f0295f2de1ca33e0a8fe
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971209"
---
# <a name="security-changes-in-the-net-framework"></a>Zmiany zabezpieczeń w programie .NET Framework
Najważniejsze zmiany zabezpieczeń w .NET Framework 4,5 są w silnym nazewnictwie. Aby uzyskać opis tych zmian, zobacz [ulepszona silna nazwa](../../standard/assembly/enhanced-strong-naming.md) .  
  
 .NET Framework zapewnia dwuwarstwowy model zabezpieczeń dla aplikacji zarządzanych. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikacje działają w kontenerze zabezpieczeń systemu Windows, który ogranicza dostęp do zasobów. W tym kontenerze aplikacje zarządzane działają w pełni zaufane. Z punktu widzenia zabezpieczeń dostępu kodu (CAS) nie ma niczego, aby deweloperzy mogli podwyższyć poziom uprawnień. Aby uzyskać informacje o uprawnieniach przyznanych przez system Windows, zobacz [deklaracje możliwości aplikacji (aplikacje ze sklepu Windows)](https://go.microsoft.com/fwlink/?LinkId=230436) w centrum deweloperów systemu Windows. Aby uzyskać informacje na temat [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] tworzenia aplikacji, zobacz [Tworzenie pierwszej aplikacji do sklepu Windows C# przy użyciu lub Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
