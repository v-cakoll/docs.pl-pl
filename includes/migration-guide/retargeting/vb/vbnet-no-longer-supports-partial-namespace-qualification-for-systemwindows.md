---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640145"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="3fbd2-101">VB.NET nie obsługuje już kwalifikacji częściowego przestrzeń nazw System.Windows interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3fbd2-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3fbd2-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3fbd2-102">Details</span></span>|<span data-ttu-id="3fbd2-103">Począwszy od .NET Framework 4.5.2 projektów VB.NET, nie można określić System.Windows interfejsów API przy użyciu częściowo kwalifikowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3fbd2-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="3fbd2-104">Na przykład, odnoszące się do <code>Windows.Forms.DialogResult</code> zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3fbd2-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="3fbd2-105">Zamiast tego kod musi odwoływać się do w pełni kwalifikowana nazwa (<xref:System.Windows.Forms.DialogResult>) lub importowanie określonej przestrzeni nazw i odwoływać się tylko do <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="3fbd2-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="3fbd2-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3fbd2-106">Suggestion</span></span>|<span data-ttu-id="3fbd2-107">Kod powinien zostać zaktualizowany do odwoływania się do <code>System.Windows</code> interfejsów API przy użyciu prostego nazwy (i importowania odpowiednich przestrzeni nazw) lub za pomocą w pełni kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="3fbd2-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="3fbd2-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="3fbd2-108">Scope</span></span>|<span data-ttu-id="3fbd2-109">Mały</span><span class="sxs-lookup"><span data-stu-id="3fbd2-109">Minor</span></span>|
|<span data-ttu-id="3fbd2-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="3fbd2-110">Version</span></span>|<span data-ttu-id="3fbd2-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="3fbd2-111">4.5.2</span></span>|
|<span data-ttu-id="3fbd2-112">Typ</span><span class="sxs-lookup"><span data-stu-id="3fbd2-112">Type</span></span>|<span data-ttu-id="3fbd2-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="3fbd2-113">Retargeting</span></span>|
