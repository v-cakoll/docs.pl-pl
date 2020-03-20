---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803204"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="d1497-101">Nie można już ustawić opcji EnableViewStateMac na false</span><span class="sxs-lookup"><span data-stu-id="d1497-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d1497-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d1497-102">Details</span></span>|<span data-ttu-id="d1497-103">ASP.NET nie pozwala już deweloperom na określenie <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> lub <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="d1497-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="d1497-104">Kod uwierzytelniania wiadomości o stanie widoku (MAC) jest teraz wymuszany dla wszystkich żądań ze stanem widoku osadzonego.</span><span class="sxs-lookup"><span data-stu-id="d1497-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="d1497-105">Dotyczy to tylko aplikacji, które jawnie <code>false</code> ustawić EnableViewStateMac właściwość dotyczy.</span><span class="sxs-lookup"><span data-stu-id="d1497-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="d1497-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d1497-106">Suggestion</span></span>|<span data-ttu-id="d1497-107">EnableViewStateMac należy przyjąć, że jest true, a wszelkie wynikające błędy MAC muszą być rozwiązane (jak wyjaśniono w [niniejszych wytycznych,](https://support.microsoft.com/kb/2915218)który zawiera wiele rozdzielczości w zależności od specyfiki tego, co jest przyczyną błędów MAC).</span><span class="sxs-lookup"><span data-stu-id="d1497-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="d1497-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="d1497-108">Scope</span></span>|<span data-ttu-id="d1497-109">Duży</span><span class="sxs-lookup"><span data-stu-id="d1497-109">Major</span></span>|
|<span data-ttu-id="d1497-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="d1497-110">Version</span></span>|<span data-ttu-id="d1497-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="d1497-111">4.5.2</span></span>|
|<span data-ttu-id="d1497-112">Typ</span><span class="sxs-lookup"><span data-stu-id="d1497-112">Type</span></span>|<span data-ttu-id="d1497-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d1497-113">Runtime</span></span>|
