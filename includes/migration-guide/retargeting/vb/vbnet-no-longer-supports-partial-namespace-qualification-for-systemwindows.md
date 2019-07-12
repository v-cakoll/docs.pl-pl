---
ms.openlocfilehash: 43e9c1c2f03daedf4d56152da5672b89399a3c69
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804674"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="9b95b-101">VB.NET nie obsługuje już kwalifikacji częściowego przestrzeń nazw System.Windows interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9b95b-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9b95b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9b95b-102">Details</span></span>|<span data-ttu-id="9b95b-103">Począwszy od .NET Framework 4.5.2 projektów VB.NET, nie można określić System.Windows interfejsów API przy użyciu częściowo kwalifikowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9b95b-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="9b95b-104">Na przykład, odnoszące się do <code>Windows.Forms.DialogResult</code> zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9b95b-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="9b95b-105">Zamiast tego kod musi odwoływać się do w pełni kwalifikowana nazwa (<xref:System.Windows.Forms.DialogResult>) lub importowanie określonej przestrzeni nazw i odwoływać się tylko do <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="9b95b-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="9b95b-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="9b95b-106">Suggestion</span></span>|<span data-ttu-id="9b95b-107">Kod powinien zostać zaktualizowany do odwoływania się do <code>System.Windows</code> interfejsów API przy użyciu prostego nazwy (i importowania odpowiednich przestrzeni nazw) lub za pomocą w pełni kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="9b95b-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="9b95b-108">Scope</span><span class="sxs-lookup"><span data-stu-id="9b95b-108">Scope</span></span>|<span data-ttu-id="9b95b-109">Mały</span><span class="sxs-lookup"><span data-stu-id="9b95b-109">Minor</span></span>|
|<span data-ttu-id="9b95b-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="9b95b-110">Version</span></span>|<span data-ttu-id="9b95b-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9b95b-111">4.5.2</span></span>|
|<span data-ttu-id="9b95b-112">Typ</span><span class="sxs-lookup"><span data-stu-id="9b95b-112">Type</span></span>|<span data-ttu-id="9b95b-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="9b95b-113">Retargeting</span></span>|

