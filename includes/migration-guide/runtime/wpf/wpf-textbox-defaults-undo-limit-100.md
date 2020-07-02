---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620478"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="d1d38-101">Wartość pola tekstowego WPF jest domyślna dla limitu cofania 100</span><span class="sxs-lookup"><span data-stu-id="d1d38-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="d1d38-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d1d38-102">Details</span></span>

<span data-ttu-id="d1d38-103">W .NET Framework 4,5 domyślny limit cofania dla pola tekstowego WPF to 100 (w przeciwieństwie do nieograniczonego w .NET Framework 4,0)</span><span class="sxs-lookup"><span data-stu-id="d1d38-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d1d38-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d1d38-104">Suggestion</span></span>

<span data-ttu-id="d1d38-105">Jeśli limit cofania wynoszący 100 jest zbyt niski, limit może być jawnie ustawiony z<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span><span class="sxs-lookup"><span data-stu-id="d1d38-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="d1d38-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d1d38-106">Name</span></span>    | <span data-ttu-id="d1d38-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="d1d38-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d1d38-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="d1d38-108">Scope</span></span>   |<span data-ttu-id="d1d38-109">Brzeg</span><span class="sxs-lookup"><span data-stu-id="d1d38-109">Edge</span></span>|
|<span data-ttu-id="d1d38-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="d1d38-110">Version</span></span>|<span data-ttu-id="d1d38-111">4.5</span><span class="sxs-lookup"><span data-stu-id="d1d38-111">4.5</span></span>|
|<span data-ttu-id="d1d38-112">Typ</span><span class="sxs-lookup"><span data-stu-id="d1d38-112">Type</span></span>|<span data-ttu-id="d1d38-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d1d38-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1d38-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d1d38-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
