---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802563"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="1d8d4-101">Objectdisposedexception — generowane przez sprawdzanie pisowni w WPF</span><span class="sxs-lookup"><span data-stu-id="1d8d4-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1d8d4-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1d8d4-102">Details</span></span>|<span data-ttu-id="1d8d4-103">Aplikacje WPF od czasu do czasu awarii podczas zamykania aplikacji za pomocą <xref:System.ObjectDisposedException?displayProperty=name> zgłoszony przez sprawdzanie pisowni.</span><span class="sxs-lookup"><span data-stu-id="1d8d4-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="1d8d4-104">Problem ten został rozwiązany w .NET Framework 4.7 WPF Obsługa wyjątku bezpiecznie i zapewnić w ten sposób, że aplikacje są już naruszone.</span><span class="sxs-lookup"><span data-stu-id="1d8d4-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="1d8d4-105">Należy zauważyć, że okazjonalne wyjątki pierwszej szansy będzie w dalszym ciągu należy przestrzegać w aplikacjach działających w debugerze.</span><span class="sxs-lookup"><span data-stu-id="1d8d4-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="1d8d4-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1d8d4-106">Suggestion</span></span>|<span data-ttu-id="1d8d4-107">Uaktualnianie do programu .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="1d8d4-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="1d8d4-108">Scope</span><span class="sxs-lookup"><span data-stu-id="1d8d4-108">Scope</span></span>|<span data-ttu-id="1d8d4-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="1d8d4-109">Edge</span></span>|
|<span data-ttu-id="1d8d4-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="1d8d4-110">Version</span></span>|<span data-ttu-id="1d8d4-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="1d8d4-111">4.6.1</span></span>|
|<span data-ttu-id="1d8d4-112">Typ</span><span class="sxs-lookup"><span data-stu-id="1d8d4-112">Type</span></span>|<span data-ttu-id="1d8d4-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1d8d4-113">Runtime</span></span>|

