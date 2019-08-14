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
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="a7f6a-103">Jakie narzędzia diagnostyczne są dostępne w środowisku .NET Core?</span><span class="sxs-lookup"><span data-stu-id="a7f6a-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="a7f6a-104">Oprogramowanie nie zawsze zachowuje się w oczekiwany sposób, ale .NET Core ma narzędzia i interfejsy API, które ułatwią zdiagnozowanie tych problemów szybko i efektywnie.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="a7f6a-105">Ten artykuł ułatwia znalezienie różnych potrzebnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggersmanaged-debuggersmd"></a>[<span data-ttu-id="a7f6a-106">Zarządzane debugery</span><span class="sxs-lookup"><span data-stu-id="a7f6a-106">Managed debuggers</span></span>](managed-debuggers.md)
<span data-ttu-id="a7f6a-107">Zarządzane debugery umożliwiają korzystanie z programu.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-107">Managed debuggers allow you to interact with your program.</span></span> <span data-ttu-id="a7f6a-108">Wstrzymywanie, przyrostowe wykonywanie, badanie i wznawianie zawiera szczegółowe informacje o zachowaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="a7f6a-109">Debuger to pierwszy wybór służący do diagnozowania problemów funkcjonalnych, które można łatwo odtworzyć.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracinglogging-tracingmd"></a>[<span data-ttu-id="a7f6a-110">Rejestrowanie i śledzenie</span><span class="sxs-lookup"><span data-stu-id="a7f6a-110">Logging and tracing</span></span>](logging-tracing.md)
<span data-ttu-id="a7f6a-111">Rejestrowanie i śledzenie to powiązane techniki.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-111">Logging and tracing are related techniques.</span></span> <span data-ttu-id="a7f6a-112">Odnoszą się one do kodu instrumentacji do tworzenia plików dziennika.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="a7f6a-113">Pliki rejestrują szczegóły działania programu.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-113">The files record the details of what a program does.</span></span> <span data-ttu-id="a7f6a-114">Te szczegółowe informacje mogą służyć do diagnozowania najbardziej złożonych problemów.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="a7f6a-115">W połączeniu z sygnaturami czasowymi te techniki są również przydatne w badaniach wydajności.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testingtestingindexmd"></a>[<span data-ttu-id="a7f6a-116">Testowanie jednostek</span><span class="sxs-lookup"><span data-stu-id="a7f6a-116">Unit testing</span></span>](../testing/index.md)
<span data-ttu-id="a7f6a-117">Testowanie jednostkowe to kluczowy składnik ciągłej integracji i wdrażania wysokiej jakości oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-117">Unit testing is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="a7f6a-118">Testy jednostkowe zostały zaprojektowane w celu zapewnienia wczesnego ostrzegania w przypadku wystąpienia elementu.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-118">Unit tests are designed to give you an early warning when you break something.</span></span>
