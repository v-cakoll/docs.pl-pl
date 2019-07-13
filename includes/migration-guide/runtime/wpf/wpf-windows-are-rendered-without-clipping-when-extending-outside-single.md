---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858537"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="c345b-101">WPF, windows mają być renderowane bez przycinania, rozszerzając poza pojedynczy monitor</span><span class="sxs-lookup"><span data-stu-id="c345b-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c345b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c345b-102">Details</span></span>|<span data-ttu-id="c345b-103">W .NET Framework 4.6 jest uruchomiona w systemie Windows 8 lub nowszym, całe okno jest renderowany bez przycinania, gdy wykraczał poza jednym wyświetlana w przypadku wielu monitorów.</span><span class="sxs-lookup"><span data-stu-id="c345b-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="c345b-104">To różni się od poprzednich wersji programu .NET Framework, która będzie obcina okna WPF, które wykracza poza pojedynczy ekran.</span><span class="sxs-lookup"><span data-stu-id="c345b-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="c345b-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c345b-105">Suggestion</span></span>|<span data-ttu-id="c345b-106">To zachowanie, (, kiedy należy przyciąć, czy nie) może być jawnie ustawione, za pomocą <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element <code>&lt;appSettings&gt;</code> w pliku konfiguracji aplikacji lub poprzez skonfigurowanie <code>EnableMultiMonitorDisplayClipping</code> właściwość przy uruchamianiu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c345b-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="c345b-107">Scope</span><span class="sxs-lookup"><span data-stu-id="c345b-107">Scope</span></span>|<span data-ttu-id="c345b-108">Mały</span><span class="sxs-lookup"><span data-stu-id="c345b-108">Minor</span></span>|
|<span data-ttu-id="c345b-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="c345b-109">Version</span></span>|<span data-ttu-id="c345b-110">4.6</span><span class="sxs-lookup"><span data-stu-id="c345b-110">4.6</span></span>|
|<span data-ttu-id="c345b-111">Typ</span><span class="sxs-lookup"><span data-stu-id="c345b-111">Type</span></span>|<span data-ttu-id="c345b-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c345b-112">Runtime</span></span>|

