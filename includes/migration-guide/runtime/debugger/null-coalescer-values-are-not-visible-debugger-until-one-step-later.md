---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620297"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="bfcf6-101">Wartości parametrów łączenia wartości null nie są widoczne w debugerze, dopóki nie zostanie później jeden krok</span><span class="sxs-lookup"><span data-stu-id="bfcf6-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="bfcf6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bfcf6-102">Details</span></span>

<span data-ttu-id="bfcf6-103">Usterka w .NET Framework 4,5 powoduje, że wartości ustawione za pośrednictwem operacji łączenia zerowego nie będą widoczne w debugerze natychmiast po wykonaniu operacji przypisania w przypadku uruchamiania w wersji 64-bitowej struktury.</span><span class="sxs-lookup"><span data-stu-id="bfcf6-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bfcf6-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="bfcf6-104">Suggestion</span></span>

<span data-ttu-id="bfcf6-105">Przechodzenie po jednym dodatkowym czasie w debugerze spowoduje, że wartość lokalna/pole zostanie prawidłowo zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="bfcf6-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="bfcf6-106">Ten problem został również rozwiązany w .NET Framework 4,6; uaktualnienie do tej wersji środowiska powinno rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="bfcf6-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="bfcf6-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="bfcf6-107">Name</span></span>    | <span data-ttu-id="bfcf6-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="bfcf6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bfcf6-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="bfcf6-109">Scope</span></span>   |<span data-ttu-id="bfcf6-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="bfcf6-110">Edge</span></span>|
|<span data-ttu-id="bfcf6-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="bfcf6-111">Version</span></span>|<span data-ttu-id="bfcf6-112">4.5</span><span class="sxs-lookup"><span data-stu-id="bfcf6-112">4.5</span></span>|
|<span data-ttu-id="bfcf6-113">Typ</span><span class="sxs-lookup"><span data-stu-id="bfcf6-113">Type</span></span>|<span data-ttu-id="bfcf6-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="bfcf6-114">Runtime</span></span>|
