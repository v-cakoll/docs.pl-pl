---
title: Omówienie narzędzi diagnostycznych — .NET Core
description: Przegląd narzędzi i technik dostępnych do diagnozowania aplikacji .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974127"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Jakie narzędzia diagnostyczne są dostępne w środowisku .NET Core?

Oprogramowanie nie zawsze zachowuje się w oczekiwany sposób, ale .NET Core ma narzędzia i interfejsy API, które ułatwią zdiagnozowanie tych problemów szybko i efektywnie.

Ten artykuł ułatwia znalezienie różnych potrzebnych narzędzi.

## <a name="managed-debuggersmanaged-debuggersmd"></a>[Zarządzane debugery](managed-debuggers.md)
Zarządzane debugery umożliwiają korzystanie z programu. Wstrzymywanie, przyrostowe wykonywanie, badanie i wznawianie zawiera szczegółowe informacje o zachowaniu kodu. Debuger to pierwszy wybór służący do diagnozowania problemów funkcjonalnych, które można łatwo odtworzyć.

## <a name="logging-and-tracinglogging-tracingmd"></a>[Rejestrowanie i śledzenie](logging-tracing.md)
Rejestrowanie i śledzenie to powiązane techniki. Odnoszą się one do kodu instrumentacji do tworzenia plików dziennika. Pliki rejestrują szczegóły działania programu. Te szczegółowe informacje mogą służyć do diagnozowania najbardziej złożonych problemów. W połączeniu z sygnaturami czasowymi te techniki są również przydatne w badaniach wydajności.

## <a name="unit-testingtestingindexmd"></a>[Testowanie jednostek](../testing/index.md)
Testowanie jednostkowe to kluczowy składnik ciągłej integracji i wdrażania wysokiej jakości oprogramowania. Testy jednostkowe zostały zaprojektowane w celu zapewnienia wczesnego ostrzegania w przypadku wystąpienia elementu.
