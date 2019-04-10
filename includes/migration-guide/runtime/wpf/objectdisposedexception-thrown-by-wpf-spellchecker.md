---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234204"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="cbe3b-101">Objectdisposedexception — generowane przez sprawdzanie pisowni w WPF</span><span class="sxs-lookup"><span data-stu-id="cbe3b-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="cbe3b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cbe3b-102">Details</span></span>|<span data-ttu-id="cbe3b-103">Aplikacje WPF od czasu do czasu awarii podczas zamykania aplikacji za pomocą <xref:System.ObjectDisposedException?displayProperty=name> zgłoszony przez sprawdzanie pisowni.</span><span class="sxs-lookup"><span data-stu-id="cbe3b-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="cbe3b-104">Problem ten został rozwiązany w .NET Framework 4.7 WPF Obsługa wyjątku bezpiecznie i zapewnić w ten sposób, że aplikacje są już naruszone.</span><span class="sxs-lookup"><span data-stu-id="cbe3b-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="cbe3b-105">Należy zauważyć, że okazjonalne wyjątki pierwszej szansy będzie w dalszym ciągu należy przestrzegać w aplikacjach działających w debugerze.</span><span class="sxs-lookup"><span data-stu-id="cbe3b-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="cbe3b-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="cbe3b-106">Suggestion</span></span>|<span data-ttu-id="cbe3b-107">Uaktualnianie do programu .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="cbe3b-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="cbe3b-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="cbe3b-108">Scope</span></span>|<span data-ttu-id="cbe3b-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="cbe3b-109">Edge</span></span>|
|<span data-ttu-id="cbe3b-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="cbe3b-110">Version</span></span>|<span data-ttu-id="cbe3b-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="cbe3b-111">4.6.1</span></span>|
|<span data-ttu-id="cbe3b-112">Typ</span><span class="sxs-lookup"><span data-stu-id="cbe3b-112">Type</span></span>|<span data-ttu-id="cbe3b-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cbe3b-113">Runtime</span></span>|
