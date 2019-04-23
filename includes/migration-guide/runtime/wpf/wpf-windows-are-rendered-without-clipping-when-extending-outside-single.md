---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118760"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="e4390-101">WPF, windows mają być renderowane bez przycinania, rozszerzając poza pojedynczy monitor</span><span class="sxs-lookup"><span data-stu-id="e4390-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e4390-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e4390-102">Details</span></span>|<span data-ttu-id="e4390-103">W .NET Framework 4.6 jest uruchomiona w systemie Windows 8 lub nowszym, całe okno jest renderowany bez przycinania, gdy wykraczał poza jednym wyświetlana w przypadku wielu monitorów.</span><span class="sxs-lookup"><span data-stu-id="e4390-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="e4390-104">To różni się od poprzednich wersji programu .NET Framework, która będzie obcina okna WPF, które wykracza poza pojedynczy ekran.</span><span class="sxs-lookup"><span data-stu-id="e4390-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="e4390-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e4390-105">Suggestion</span></span>|<span data-ttu-id="e4390-106">To zachowanie, (, kiedy należy przyciąć, czy nie) może być jawnie ustawione, za pomocą <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element <code>&lt;appSettings&gt;</code> w pliku konfiguracji aplikacji lub poprzez skonfigurowanie <code>EnableMultiMonitorDisplayClipping</code> właściwość przy uruchamianiu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4390-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="e4390-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="e4390-107">Scope</span></span>|<span data-ttu-id="e4390-108">Mały</span><span class="sxs-lookup"><span data-stu-id="e4390-108">Minor</span></span>|
|<span data-ttu-id="e4390-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="e4390-109">Version</span></span>|<span data-ttu-id="e4390-110">4.6</span><span class="sxs-lookup"><span data-stu-id="e4390-110">4.6</span></span>|
|<span data-ttu-id="e4390-111">Typ</span><span class="sxs-lookup"><span data-stu-id="e4390-111">Type</span></span>|<span data-ttu-id="e4390-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e4390-112">Runtime</span></span>|
