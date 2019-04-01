---
ms.openlocfilehash: 9bf6972812bdf4a385b99fe34d2cd3cd8a91c8cf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761095"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="73c5c-101">ClickOnce obsługuje algorytm SHA-256 w aplikacjach docelowych 4.0</span><span class="sxs-lookup"><span data-stu-id="73c5c-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="73c5c-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="73c5c-102">Details</span></span>|<span data-ttu-id="73c5c-103">Wcześniej aplikacji ClickOnce za pomocą certyfikatu, który został podpisany za pomocą algorytmu SHA-256 wymaga .NET Framework 4.5 lub nowszej być obecne, nawet wtedy, gdy aplikacja docelowej 4.0.</span><span class="sxs-lookup"><span data-stu-id="73c5c-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="73c5c-104">Teraz, ukierunkowane na .NET Framework 4.0 ClickOnce aplikacje mogą być uruchamiane na .NET Framework 4.0, nawet jeśli podpisany przy użyciu algorytmu SHA-256.</span><span class="sxs-lookup"><span data-stu-id="73c5c-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="73c5c-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="73c5c-105">Suggestion</span></span>|<span data-ttu-id="73c5c-106">Ta zmiana spowoduje usunięcie tej zależności i umożliwi certyfikatów SHA-256, ma być używany do podpisywania aplikacji ClickOnce, przeznaczonych dla platformy .NET Framework 4 i starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="73c5c-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="73c5c-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="73c5c-107">Scope</span></span>|<span data-ttu-id="73c5c-108">Mały</span><span class="sxs-lookup"><span data-stu-id="73c5c-108">Minor</span></span>|
|<span data-ttu-id="73c5c-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="73c5c-109">Version</span></span>|<span data-ttu-id="73c5c-110">4.6</span><span class="sxs-lookup"><span data-stu-id="73c5c-110">4.6</span></span>|
|<span data-ttu-id="73c5c-111">Typ</span><span class="sxs-lookup"><span data-stu-id="73c5c-111">Type</span></span>|<span data-ttu-id="73c5c-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="73c5c-112">Retargeting</span></span>|

