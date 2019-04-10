---
ms.openlocfilehash: 1721d32f8cdc9b6ea4b4732e38afa56a8a532600
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234821"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="d2c7c-101">Właściwości DbParameter.Precision i DbParameter.Scale są teraz publicznymi wirtualnymi elementami członkowskimi</span><span class="sxs-lookup"><span data-stu-id="d2c7c-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d2c7c-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d2c7c-102">Details</span></span>|<xref:System.Data.Common.DbParameter.Precision> <span data-ttu-id="d2c7c-103">i <xref:System.Data.Common.DbParameter.Scale> są implementowane jako właściwości publiczne wirtualne.</span><span class="sxs-lookup"><span data-stu-id="d2c7c-103">and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="d2c7c-104">Zastępują one odpowiednie implementacje interfejsu jawnego <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> i <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span><span class="sxs-lookup"><span data-stu-id="d2c7c-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>|
|<span data-ttu-id="d2c7c-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d2c7c-105">Suggestion</span></span>|<span data-ttu-id="d2c7c-106">Podczas ponownego kompilowania dostawcy bazy danych programu ADO.NET te różnice będą wymagać zastosowania słowa kluczowego „override” do właściwości Precision i Scale.</span><span class="sxs-lookup"><span data-stu-id="d2c7c-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="d2c7c-107">Jest to potrzebne tylko w przypadku ponownego kompilowania składników; istniejące pliki binarne będą nadal działać.</span><span class="sxs-lookup"><span data-stu-id="d2c7c-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>|
|<span data-ttu-id="d2c7c-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="d2c7c-108">Scope</span></span>|<span data-ttu-id="d2c7c-109">Mały</span><span class="sxs-lookup"><span data-stu-id="d2c7c-109">Minor</span></span>|
|<span data-ttu-id="d2c7c-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="d2c7c-110">Version</span></span>|<span data-ttu-id="d2c7c-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d2c7c-111">4.5.1</span></span>|
|<span data-ttu-id="d2c7c-112">Typ</span><span class="sxs-lookup"><span data-stu-id="d2c7c-112">Type</span></span>|<span data-ttu-id="d2c7c-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="d2c7c-113">Retargeting</span></span>|
|<span data-ttu-id="d2c7c-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d2c7c-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|
