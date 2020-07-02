---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621832"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="188eb-101">ObjectDisposedException zgłoszone przez program sprawdzania pisowni WPF</span><span class="sxs-lookup"><span data-stu-id="188eb-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="188eb-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="188eb-102">Details</span></span>

<span data-ttu-id="188eb-103">Aplikacje WPF sporadycznie uległy awarii podczas zamykania aplikacji za pomocą modułu <xref:System.ObjectDisposedException?displayProperty=fullName> sprawdzania pisowni.</span><span class="sxs-lookup"><span data-stu-id="188eb-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="188eb-104">Jest to rozwiązane w 4,7 .NET Frameworkj platformie WPF przez obsługę wyjątku i w ten sposób, dzięki czemu nie ma już negatywnego wpływ na aplikacje.</span><span class="sxs-lookup"><span data-stu-id="188eb-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="188eb-105">Należy zauważyć, że sporadyczne wyjątki pierwszej szansy byłyby nadal przestrzegane w aplikacjach uruchamianych w ramach debugera.</span><span class="sxs-lookup"><span data-stu-id="188eb-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="188eb-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="188eb-106">Suggestion</span></span>

<span data-ttu-id="188eb-107">Uaktualnij do .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="188eb-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="188eb-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="188eb-108">Name</span></span>    | <span data-ttu-id="188eb-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="188eb-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="188eb-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="188eb-110">Scope</span></span>   |<span data-ttu-id="188eb-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="188eb-111">Edge</span></span>|
|<span data-ttu-id="188eb-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="188eb-112">Version</span></span>|<span data-ttu-id="188eb-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="188eb-113">4.6.1</span></span>|
|<span data-ttu-id="188eb-114">Typ</span><span class="sxs-lookup"><span data-stu-id="188eb-114">Type</span></span>|<span data-ttu-id="188eb-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="188eb-115">Runtime</span></span>|
