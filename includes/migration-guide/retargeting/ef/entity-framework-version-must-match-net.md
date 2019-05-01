---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091705"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="54e0c-101">Entity Framework w wersji musi odpowiadać wersji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="54e0c-101">Entity Framework version must match the .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="54e0c-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="54e0c-102">Details</span></span>|<span data-ttu-id="54e0c-103">Programu entity framework w wersji powinny zostać dopasowane do wersji programu .NET framework.</span><span class="sxs-lookup"><span data-stu-id="54e0c-103">The entity framework version should be matched with the .NET framework version.</span></span> <span data-ttu-id="54e0c-104">Entity Framework 5 jest zalecane dla platformy .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="54e0c-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="54e0c-105">Istnieje kilka znanych problemów z programem EF 4.x w projekcie programu .NET Framework 4.5 wokół <xref:System.ComponentModel.DataAnnotations>.</span><span class="sxs-lookup"><span data-stu-id="54e0c-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="54e0c-106">W .NET 4.5 te zostały przeniesione do innego zestawu, dzięki czemu nie występują problemy, określająca, które adnotacje do użycia.</span><span class="sxs-lookup"><span data-stu-id="54e0c-106">In .NET 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>|
|<span data-ttu-id="54e0c-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="54e0c-107">Suggestion</span></span>|<span data-ttu-id="54e0c-108">Uaktualnianie do programu Entity Framework 5 dla programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="54e0c-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>|
|<span data-ttu-id="54e0c-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="54e0c-109">Scope</span></span>|<span data-ttu-id="54e0c-110">Duży</span><span class="sxs-lookup"><span data-stu-id="54e0c-110">Major</span></span>|
|<span data-ttu-id="54e0c-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="54e0c-111">Version</span></span>|<span data-ttu-id="54e0c-112">4.5</span><span class="sxs-lookup"><span data-stu-id="54e0c-112">4.5</span></span>|
|<span data-ttu-id="54e0c-113">Typ</span><span class="sxs-lookup"><span data-stu-id="54e0c-113">Type</span></span>|<span data-ttu-id="54e0c-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="54e0c-114">Retargeting</span></span>|
