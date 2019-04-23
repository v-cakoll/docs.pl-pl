---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804765"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="8a2e6-101">Karty strumienia WinRT nie są już wywoływać FlushAsync automatycznie przy zamykaniu</span><span class="sxs-lookup"><span data-stu-id="8a2e6-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8a2e6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8a2e6-102">Details</span></span>|<span data-ttu-id="8a2e6-103">W aplikacjach Windows Store kart strumienia środowiska wykonawczego Windows nie jest już wywołać metodę FlushAsync z metody Dispose.</span><span class="sxs-lookup"><span data-stu-id="8a2e6-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="8a2e6-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8a2e6-104">Suggestion</span></span>|<span data-ttu-id="8a2e6-105">Ta zmiana powinny być przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="8a2e6-105">This change should be transparent.</span></span> <span data-ttu-id="8a2e6-106">Deweloperzy mogą przywrócić poprzednie zachowanie przez pisanie kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8a2e6-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="8a2e6-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="8a2e6-107">Scope</span></span>|<span data-ttu-id="8a2e6-108">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="8a2e6-108">Transparent</span></span>|
|<span data-ttu-id="8a2e6-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="8a2e6-109">Version</span></span>|<span data-ttu-id="8a2e6-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8a2e6-110">4.5.1</span></span>|
|<span data-ttu-id="8a2e6-111">Typ</span><span class="sxs-lookup"><span data-stu-id="8a2e6-111">Type</span></span>|<span data-ttu-id="8a2e6-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="8a2e6-112">Runtime</span></span>|
