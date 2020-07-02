---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616109"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="92d8e-101">Właściwości DbParameter.Precision i DbParameter.Scale są teraz publicznymi wirtualnymi elementami członkowskimi</span><span class="sxs-lookup"><span data-stu-id="92d8e-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

#### <a name="details"></a><span data-ttu-id="92d8e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="92d8e-102">Details</span></span>

<span data-ttu-id="92d8e-103"><xref:System.Data.Common.DbParameter.Precision> i <xref:System.Data.Common.DbParameter.Scale> są implementowane jako publiczne właściwości wirtualne.</span><span class="sxs-lookup"><span data-stu-id="92d8e-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="92d8e-104">Zastępują one odpowiednie implementacje interfejsu jawnego <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> i <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span><span class="sxs-lookup"><span data-stu-id="92d8e-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="92d8e-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="92d8e-105">Suggestion</span></span>

<span data-ttu-id="92d8e-106">Podczas ponownego kompilowania dostawcy bazy danych programu ADO.NET te różnice będą wymagać zastosowania słowa kluczowego „override” do właściwości Precision i Scale.</span><span class="sxs-lookup"><span data-stu-id="92d8e-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="92d8e-107">Jest to potrzebne tylko w przypadku ponownego kompilowania składników; istniejące pliki binarne będą nadal działać.</span><span class="sxs-lookup"><span data-stu-id="92d8e-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>

| <span data-ttu-id="92d8e-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="92d8e-108">Name</span></span>    | <span data-ttu-id="92d8e-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="92d8e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="92d8e-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="92d8e-110">Scope</span></span>   | <span data-ttu-id="92d8e-111">Mały</span><span class="sxs-lookup"><span data-stu-id="92d8e-111">Minor</span></span>       |
| <span data-ttu-id="92d8e-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="92d8e-112">Version</span></span> | <span data-ttu-id="92d8e-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="92d8e-113">4.5.1</span></span>       |
| <span data-ttu-id="92d8e-114">Typ</span><span class="sxs-lookup"><span data-stu-id="92d8e-114">Type</span></span>    | <span data-ttu-id="92d8e-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="92d8e-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="92d8e-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="92d8e-116">Affected APIs</span></span>

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
