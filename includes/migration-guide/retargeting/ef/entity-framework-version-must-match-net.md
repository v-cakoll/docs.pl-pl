---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617196"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="44a65-101">Wersja Entity Framework musi być zgodna z wersją .NET Framework</span><span class="sxs-lookup"><span data-stu-id="44a65-101">Entity Framework version must match the .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="44a65-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="44a65-102">Details</span></span>

<span data-ttu-id="44a65-103">Wersja Entity Framework (EF) powinna być zgodna z wersją .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44a65-103">The Entity Framework (EF) version should be matched with the .NET Framework version.</span></span> <span data-ttu-id="44a65-104">Entity Framework 5 jest zalecana dla .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="44a65-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="44a65-105">Istnieją znane problemy z programem EF 4. x w projekcie .NET Framework 4,5 <xref:System.ComponentModel.DataAnnotations> .</span><span class="sxs-lookup"><span data-stu-id="44a65-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="44a65-106">W .NET Framework 4,5 te zostały przeniesione do innego zestawu, dlatego występują problemy z ustaleniem adnotacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="44a65-106">In .NET Framework 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="44a65-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="44a65-107">Suggestion</span></span>

<span data-ttu-id="44a65-108">Uaktualnij do wersji Entity Framework 5 dla .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="44a65-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>

| <span data-ttu-id="44a65-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="44a65-109">Name</span></span>    | <span data-ttu-id="44a65-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="44a65-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="44a65-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="44a65-111">Scope</span></span>   | <span data-ttu-id="44a65-112">Duży</span><span class="sxs-lookup"><span data-stu-id="44a65-112">Major</span></span>       |
| <span data-ttu-id="44a65-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="44a65-113">Version</span></span> | <span data-ttu-id="44a65-114">4.5</span><span class="sxs-lookup"><span data-stu-id="44a65-114">4.5</span></span>         |
| <span data-ttu-id="44a65-115">Typ</span><span class="sxs-lookup"><span data-stu-id="44a65-115">Type</span></span>    | <span data-ttu-id="44a65-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="44a65-116">Retargeting</span></span> |
