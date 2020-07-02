---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622116"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a><span data-ttu-id="74a4a-101">Naprawiono zawieszenie, gdy pole listy zawiera zduplikowane typy wartości</span><span class="sxs-lookup"><span data-stu-id="74a4a-101">Fixed a hang when ListBox contains duplicate value-types</span></span>

#### <a name="details"></a><span data-ttu-id="74a4a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="74a4a-102">Details</span></span>

<span data-ttu-id="74a4a-103">Rozwiązano problem polegający na tym, że wirtualizacja <xref:System.Windows.Controls.ItemsControl> może się zawiesić podczas przewijania, gdy kolekcja elementów zawiera zduplikowane obiekty z typem wartości.</span><span class="sxs-lookup"><span data-stu-id="74a4a-103">Fixed a problem where a virtualizing<xref:System.Windows.Controls.ItemsControl> can hang during scrolling when its Items collection contains duplicate value-typed objects.</span></span>

| <span data-ttu-id="74a4a-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="74a4a-104">Name</span></span>    | <span data-ttu-id="74a4a-105">Wartość</span><span class="sxs-lookup"><span data-stu-id="74a4a-105">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="74a4a-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="74a4a-106">Scope</span></span>   |<span data-ttu-id="74a4a-107">Duży</span><span class="sxs-lookup"><span data-stu-id="74a4a-107">Major</span></span>|
|<span data-ttu-id="74a4a-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="74a4a-108">Version</span></span>|<span data-ttu-id="74a4a-109">4,8</span><span class="sxs-lookup"><span data-stu-id="74a4a-109">4.8</span></span>|
|<span data-ttu-id="74a4a-110">Typ</span><span class="sxs-lookup"><span data-stu-id="74a4a-110">Type</span></span>|<span data-ttu-id="74a4a-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="74a4a-111">Runtime</span></span>|
