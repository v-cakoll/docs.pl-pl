---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802563"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="1dfc5-101">ObjectDisposedException rzucony przez wpfwętny WPF</span><span class="sxs-lookup"><span data-stu-id="1dfc5-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1dfc5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1dfc5-102">Details</span></span>|<span data-ttu-id="1dfc5-103">Aplikacje WPF od czasu do <xref:System.ObjectDisposedException?displayProperty=name> czasu ulegają awarii podczas zamykania aplikacji z rzuconym przez moduł sprawdzania pisowni.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="1dfc5-104">Jest to ustalone w .NET Framework 4.7 WPF przez obsługę wyjątku bezpiecznie, a tym samym zapewnienie, że aplikacje nie są już niekorzystne.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="1dfc5-105">Należy zauważyć, że okazjonalne wyjątki pierwszej szansy będą nadal obserwowane w aplikacjach działających pod debugerem.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="1dfc5-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1dfc5-106">Suggestion</span></span>|<span data-ttu-id="1dfc5-107">Uaktualnienie do programu .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="1dfc5-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="1dfc5-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="1dfc5-108">Scope</span></span>|<span data-ttu-id="1dfc5-109">Brzeg</span><span class="sxs-lookup"><span data-stu-id="1dfc5-109">Edge</span></span>|
|<span data-ttu-id="1dfc5-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="1dfc5-110">Version</span></span>|<span data-ttu-id="1dfc5-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="1dfc5-111">4.6.1</span></span>|
|<span data-ttu-id="1dfc5-112">Typ</span><span class="sxs-lookup"><span data-stu-id="1dfc5-112">Type</span></span>|<span data-ttu-id="1dfc5-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1dfc5-113">Runtime</span></span>|
