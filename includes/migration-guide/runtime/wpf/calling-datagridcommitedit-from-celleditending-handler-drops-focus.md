---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622126"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="829cc-101">Wywołanie elementu DataGrid. CommitEdit z obsługi CellEditEnding powoduje odrzucenie fokusu</span><span class="sxs-lookup"><span data-stu-id="829cc-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="829cc-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="829cc-102">Details</span></span>

<span data-ttu-id="829cc-103">Wywołanie <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednego z <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> programów obsługi zdarzeń powoduje <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> utratę fokusu.</span><span class="sxs-lookup"><span data-stu-id="829cc-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="829cc-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="829cc-104">Suggestion</span></span>

<span data-ttu-id="829cc-105">Ta usterka została rozwiązana w .NET Framework 4.5.2, dlatego można ją uniknąć, uaktualniając .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="829cc-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="829cc-106">Alternatywnie można to uniknąć przez jawne ponowne wybranie polecenia <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> po wywołaniu <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="829cc-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="829cc-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="829cc-107">Name</span></span>    | <span data-ttu-id="829cc-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="829cc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="829cc-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="829cc-109">Scope</span></span>   |<span data-ttu-id="829cc-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="829cc-110">Edge</span></span>|
|<span data-ttu-id="829cc-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="829cc-111">Version</span></span>|<span data-ttu-id="829cc-112">4.5</span><span class="sxs-lookup"><span data-stu-id="829cc-112">4.5</span></span>|
|<span data-ttu-id="829cc-113">Typ</span><span class="sxs-lookup"><span data-stu-id="829cc-113">Type</span></span>|<span data-ttu-id="829cc-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="829cc-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="829cc-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="829cc-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
