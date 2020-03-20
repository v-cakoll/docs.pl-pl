---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858598"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="4b8d8-101">Null coalescer wartości nie są widoczne w debugerze, aż jeden krok później</span><span class="sxs-lookup"><span data-stu-id="4b8d8-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4b8d8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4b8d8-102">Details</span></span>|<span data-ttu-id="4b8d8-103">Błąd w programie .NET Framework 4.5 powoduje, że wartości ustawione za pomocą operacji scalania null nie są widoczne w debugerze natychmiast po wykonaniu operacji przypisania podczas uruchamiania w 64-bitowej wersji frameworka.</span><span class="sxs-lookup"><span data-stu-id="4b8d8-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="4b8d8-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="4b8d8-104">Suggestion</span></span>|<span data-ttu-id="4b8d8-105">Krok po jednym dodatkowym czasie w debugerze spowoduje, że wartość lokalnego/pola zostanie poprawnie zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="4b8d8-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="4b8d8-106">Ponadto ten problem został rozwiązany w .NET Framework 4.6; aktualizacji do tej wersji ram, należy rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="4b8d8-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="4b8d8-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="4b8d8-107">Scope</span></span>|<span data-ttu-id="4b8d8-108">Brzeg</span><span class="sxs-lookup"><span data-stu-id="4b8d8-108">Edge</span></span>|
|<span data-ttu-id="4b8d8-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="4b8d8-109">Version</span></span>|<span data-ttu-id="4b8d8-110">4.5</span><span class="sxs-lookup"><span data-stu-id="4b8d8-110">4.5</span></span>|
|<span data-ttu-id="4b8d8-111">Typ</span><span class="sxs-lookup"><span data-stu-id="4b8d8-111">Type</span></span>|<span data-ttu-id="4b8d8-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4b8d8-112">Runtime</span></span>|
