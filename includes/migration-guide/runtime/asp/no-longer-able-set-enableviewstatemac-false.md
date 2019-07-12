---
ms.openlocfilehash: 78f4d533f1efdc8d43a9ab96508b84a77e3260bc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803204"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="aa7dd-101">Nie będzie możliwe ustawienie EnableViewStateMac na wartość false</span><span class="sxs-lookup"><span data-stu-id="aa7dd-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="aa7dd-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="aa7dd-102">Details</span></span>|<span data-ttu-id="aa7dd-103">Program ASP.NET nie zezwala już deweloperom określenie <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> lub <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="aa7dd-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="aa7dd-104">Wyświetl stan kodu uwierzytelniania wiadomości (MAC) jest teraz wymuszane na wszystkie żądania z osadzonych widoku stanu.</span><span class="sxs-lookup"><span data-stu-id="aa7dd-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="aa7dd-105">Tylko te aplikacje, które jawnie ustawione właściwości EnableViewStateMac <code>false</code> dotyczy problem.</span><span class="sxs-lookup"><span data-stu-id="aa7dd-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="aa7dd-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="aa7dd-106">Suggestion</span></span>|<span data-ttu-id="aa7dd-107">EnableViewStateMac musi być zakłada się, że wartość true, a wszystkie wynikowe błędy MAC musi być rozwiązane (zgodnie z opisem w [Niniejsze wskazówki](https://support.microsoft.com/kb/2915218), który zawiera wielu rozdzielczości w zależności od tego, co jest przyczyną błędów MAC szczegółowych).</span><span class="sxs-lookup"><span data-stu-id="aa7dd-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="aa7dd-108">Scope</span><span class="sxs-lookup"><span data-stu-id="aa7dd-108">Scope</span></span>|<span data-ttu-id="aa7dd-109">Duży</span><span class="sxs-lookup"><span data-stu-id="aa7dd-109">Major</span></span>|
|<span data-ttu-id="aa7dd-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="aa7dd-110">Version</span></span>|<span data-ttu-id="aa7dd-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="aa7dd-111">4.5.2</span></span>|
|<span data-ttu-id="aa7dd-112">Typ</span><span class="sxs-lookup"><span data-stu-id="aa7dd-112">Type</span></span>|<span data-ttu-id="aa7dd-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="aa7dd-113">Runtime</span></span>|

