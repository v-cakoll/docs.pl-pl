---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804674"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="32136-101">VB.NET nie obsługuje już częściowej kwalifikacji obszaru nazw dla interfejsów API systemu.Windows</span><span class="sxs-lookup"><span data-stu-id="32136-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="32136-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="32136-102">Details</span></span>|<span data-ttu-id="32136-103">Począwszy od programu .NET Framework 4.5.2 VB.NET projektów nie może określić interfejsów API systemu System.Windows z częściowo kwalifikowanymi obszarami nazw.</span><span class="sxs-lookup"><span data-stu-id="32136-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="32136-104">Na przykład odwoływanie <code>Windows.Forms.DialogResult</code> się do zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="32136-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="32136-105">Zamiast tego kod musi odwoływać się<xref:System.Windows.Forms.DialogResult>do w pełni kwalifikowanej nazwy <xref:System.Windows.Forms.DialogResult?displayProperty=name>( ) lub importować określony obszar nazw i odnosić się po prostu do .</span><span class="sxs-lookup"><span data-stu-id="32136-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="32136-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="32136-106">Suggestion</span></span>|<span data-ttu-id="32136-107">Kod powinien być aktualizowany w celu odwoływania się do <code>System.Windows</code> interfejsów API za pomocą prostych nazw (i importowania odpowiedniego obszaru nazw) lub z w pełni kwalifikowanymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="32136-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="32136-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="32136-108">Scope</span></span>|<span data-ttu-id="32136-109">Mały</span><span class="sxs-lookup"><span data-stu-id="32136-109">Minor</span></span>|
|<span data-ttu-id="32136-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="32136-110">Version</span></span>|<span data-ttu-id="32136-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="32136-111">4.5.2</span></span>|
|<span data-ttu-id="32136-112">Typ</span><span class="sxs-lookup"><span data-stu-id="32136-112">Type</span></span>|<span data-ttu-id="32136-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="32136-113">Retargeting</span></span>|
