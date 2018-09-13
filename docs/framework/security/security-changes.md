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
ms.openlocfilehash: c62a469b3e31283e5790c747092a8fe504ef8c2a
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705095"
---
# <a name="security-changes-in-the-net-framework"></a>Zmiany zabezpieczeń w programie .NET Framework
Najważniejsze zmiany w zabezpieczeniach [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] trwa — silne nazwy. Zobacz [rozszerzone silne nazewnictwo](../../../docs/framework/app-domains/enhanced-strong-naming.md) opis tych zmian.  
  
 .NET Framework oferuje model zabezpieczeń dwuwarstwowej dla zarządzanych aplikacji. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje działają w kontenerze zabezpieczeń Windows, który ogranicza dostęp do zasobów. W tym kontenerze zarządzane aplikacje są uruchamiane w pełni zaufany. Z punktu widzenia zabezpieczeń (CAS) kod dostępu nie ma nic zrobić przez dewelopera do podniesienia uprawnień. Aby uzyskać informacji na temat uprawnień przyznanych przez Windows, zobacz [deklaracje możliwości aplikacji (aplikacje Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) w Centrum deweloperów Windows. Aby uzyskać informacje o tworzeniu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie pierwszej aplikacji Windows Store przy użyciu języka C# lub Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
