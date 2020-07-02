---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620170"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="0955f-101">Nie można już ustawić EnableViewStateMac na FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="0955f-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="0955f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0955f-102">Details</span></span>

<span data-ttu-id="0955f-103">ASP.NET nie pozwala już deweloperom na określanie <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> lub <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code> .</span><span class="sxs-lookup"><span data-stu-id="0955f-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="0955f-104">Kod uwierzytelniania komunikatów o stanie (MAC) jest teraz wymuszany dla wszystkich żądań z osadzonym stanem widoku.</span><span class="sxs-lookup"><span data-stu-id="0955f-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="0955f-105">Dotyczy to tylko aplikacji, które jawnie ustawili Właściwość EnableViewStateMac <code>false</code> .</span><span class="sxs-lookup"><span data-stu-id="0955f-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0955f-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="0955f-106">Suggestion</span></span>

<span data-ttu-id="0955f-107">Należy przyjąć, że EnableViewStateMac należy mieć wartość true, a wszystkie wynikowe błędy w systemie MAC muszą zostać rozwiązane (jak wyjaśniono w [niniejszych wskazówkach](https://support.microsoft.com/kb/2915218), które zawierają wiele rozwiązań w zależności od tego, co powoduje błędy w przypadku komputerów Mac).</span><span class="sxs-lookup"><span data-stu-id="0955f-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="0955f-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0955f-108">Name</span></span>    | <span data-ttu-id="0955f-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="0955f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0955f-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="0955f-110">Scope</span></span>   |<span data-ttu-id="0955f-111">Duży</span><span class="sxs-lookup"><span data-stu-id="0955f-111">Major</span></span>|
|<span data-ttu-id="0955f-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="0955f-112">Version</span></span>|<span data-ttu-id="0955f-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="0955f-113">4.5.2</span></span>|
|<span data-ttu-id="0955f-114">Typ</span><span class="sxs-lookup"><span data-stu-id="0955f-114">Type</span></span>|<span data-ttu-id="0955f-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0955f-115">Runtime</span></span>|
