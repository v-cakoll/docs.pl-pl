---
title: Współdziałanie modelu COM w programie .NET
description: Dowiedz się, jak współpracować z bibliotekami COM w programie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 07/11/2019
ms.openlocfilehash: 9355e2ae84da623ffa725f5b2ac1bdee25b966d8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971891"
---
# <a name="com-interop-in-net"></a><span data-ttu-id="7bcdd-103">Współdziałanie modelu COM w programie .NET</span><span class="sxs-lookup"><span data-stu-id="7bcdd-103">COM Interop in .NET</span></span>

<span data-ttu-id="7bcdd-104">Component Object Model (COM) umożliwia obiektowi uwidocznienie jego funkcjonalności innym składnikom i hostowanie aplikacji na platformach Windows.</span><span class="sxs-lookup"><span data-stu-id="7bcdd-104">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications on Windows platforms.</span></span> <span data-ttu-id="7bcdd-105">Aby ułatwić użytkownikom współdziałanie z istniejącymi bazami kodu, .NET Framework zawsze zapewniał silną pomoc techniczną dotyczącą współpracy z bibliotekami COM.</span><span class="sxs-lookup"><span data-stu-id="7bcdd-105">To help enable users to interoperate with their existing code bases, the .NET Framework has always provided strong support for interoperating with COM libraries.</span></span> <span data-ttu-id="7bcdd-106">W przypadku platformy .NET Core 3,0 w systemie Windows dodano dużą część tego wsparcia do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7bcdd-106">In .NET Core 3.0, a large portion of this support has been added to .NET Core on Windows.</span></span> <span data-ttu-id="7bcdd-107">W tej dokumentacji wyjaśniono, jak wspólna współdziałanie modelu COM Techonologies i jak można je wykorzystać do współpracy z istniejącymi bibliotekami COM.</span><span class="sxs-lookup"><span data-stu-id="7bcdd-107">The documentation here will explain how the common COM interop techonologies work and how you can utilize them to interoperate with your existing COM libraries.</span></span>

- [<span data-ttu-id="7bcdd-108">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="7bcdd-108">COM Wrappers</span></span>](./com-wrappers.md)
- [<span data-ttu-id="7bcdd-109">Wywoływane otoki COM</span><span class="sxs-lookup"><span data-stu-id="7bcdd-109">COM Callable Wrappers</span></span>](./com-callable-wrapper.md)
- [<span data-ttu-id="7bcdd-110">Wywoływane otoki środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7bcdd-110">Runtime Callable Wrappers</span></span>](./runtime-callable-wrapper.md)
- [<span data-ttu-id="7bcdd-111">Kwalifikowanie typów .NET do współdziałania z modelem COM</span><span class="sxs-lookup"><span data-stu-id="7bcdd-111">Qualifying .NET Types for COM Interoperation</span></span>](./qualify-net-types-for-interoperation.md)
