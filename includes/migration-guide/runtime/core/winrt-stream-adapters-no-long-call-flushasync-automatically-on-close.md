---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649361"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="63dec-101">Karty strumienia WinRT nie są już wywoływać FlushAsync automatycznie przy zamykaniu</span><span class="sxs-lookup"><span data-stu-id="63dec-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="63dec-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="63dec-102">Details</span></span>|<span data-ttu-id="63dec-103">W aplikacjach Windows Store kart strumienia środowiska wykonawczego Windows nie jest już wywołać metodę FlushAsync z metody Dispose.</span><span class="sxs-lookup"><span data-stu-id="63dec-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="63dec-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="63dec-104">Suggestion</span></span>|<span data-ttu-id="63dec-105">Ta zmiana powinny być przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="63dec-105">This change should be transparent.</span></span> <span data-ttu-id="63dec-106">Deweloperzy mogą przywrócić poprzednie zachowanie przez pisanie kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="63dec-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="63dec-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="63dec-107">Scope</span></span>|<span data-ttu-id="63dec-108">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="63dec-108">Transparent</span></span>|
|<span data-ttu-id="63dec-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="63dec-109">Version</span></span>|<span data-ttu-id="63dec-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="63dec-110">4.5.1</span></span>|
|<span data-ttu-id="63dec-111">Typ</span><span class="sxs-lookup"><span data-stu-id="63dec-111">Type</span></span>|<span data-ttu-id="63dec-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="63dec-112">Runtime</span></span>|
