---
ms.openlocfilehash: 38c35f3f6f2262d06409690d2326d9b982e1ec86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235771"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="bd8ea-101">Kontrolki hostingu programu Managed browser z .NET Framework 1.1 i 2.0 są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="bd8ea-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bd8ea-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bd8ea-102">Details</span></span>|<span data-ttu-id="bd8ea-103">Obsługa tych formantów jest zablokowana w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="bd8ea-103">Hosting these controls is blocked in Internet Explorer.</span></span>|
|<span data-ttu-id="bd8ea-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="bd8ea-104">Suggestion</span></span>|<span data-ttu-id="bd8ea-105">Program Internet Explorer nie będzie mógł uruchomić aplikacji, która używa formantów zarządzanego hostingu w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="bd8ea-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="bd8ea-106">Poprzednie zachowanie można przywrócić, ustawiając wartość EnableIEHosting podklucza rejestru <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> do <code>1</code> dla x86 systemów i procesów 32-bitowych w x64 systemów i ustawiając <code>EnableIEHosting</code> wartość podklucza rejestru <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>do <code>1</code> dla procesów 64-bitowego na x64 systemów.</span><span class="sxs-lookup"><span data-stu-id="bd8ea-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>|
|<span data-ttu-id="bd8ea-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="bd8ea-107">Scope</span></span>|<span data-ttu-id="bd8ea-108">Mały</span><span class="sxs-lookup"><span data-stu-id="bd8ea-108">Minor</span></span>|
|<span data-ttu-id="bd8ea-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="bd8ea-109">Version</span></span>|<span data-ttu-id="bd8ea-110">4.5</span><span class="sxs-lookup"><span data-stu-id="bd8ea-110">4.5</span></span>|
|<span data-ttu-id="bd8ea-111">Typ</span><span class="sxs-lookup"><span data-stu-id="bd8ea-111">Type</span></span>|<span data-ttu-id="bd8ea-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="bd8ea-112">Runtime</span></span>|
