---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804688"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="463a6-101">Metoda Replace w adresach URL OData jest domyślnie wyłączony</span><span class="sxs-lookup"><span data-stu-id="463a6-101">The Replace method in OData URLs is disabled by default</span></span>

|   |   |
|---|---|
|<span data-ttu-id="463a6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="463a6-102">Details</span></span>|<span data-ttu-id="463a6-103">Począwszy od programu .NET Framework 4.5, metoda Replace w adresach URL OData jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="463a6-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="463a6-104">Gdy Zastąp OData jest wyłączona (teraz domyślnie), wszystkie żądania użytkowników, w tym funkcje replace, (które są rzadko) zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="463a6-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>|
|<span data-ttu-id="463a6-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="463a6-105">Suggestion</span></span>|<span data-ttu-id="463a6-106">Jeśli wymagana jest metoda replace (czyli rzadko), można ponownie włączyć za pomocą ustawień konfiguracji (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span><span class="sxs-lookup"><span data-stu-id="463a6-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span></span> <span data-ttu-id="463a6-107">Jednak metoda włączone zastępowanie można otworzyć luk w zabezpieczeniach i powinna być używana tylko po dokładnej przeglądu.</span><span class="sxs-lookup"><span data-stu-id="463a6-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>|
|<span data-ttu-id="463a6-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="463a6-108">Scope</span></span>|<span data-ttu-id="463a6-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="463a6-109">Edge</span></span>|
|<span data-ttu-id="463a6-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="463a6-110">Version</span></span>|<span data-ttu-id="463a6-111">4.5</span><span class="sxs-lookup"><span data-stu-id="463a6-111">4.5</span></span>|
|<span data-ttu-id="463a6-112">Typ</span><span class="sxs-lookup"><span data-stu-id="463a6-112">Type</span></span>|<span data-ttu-id="463a6-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="463a6-113">Runtime</span></span>|
|<span data-ttu-id="463a6-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="463a6-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
