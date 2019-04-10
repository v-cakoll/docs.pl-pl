---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234566"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="f4007-101">ClickOnce obsługuje algorytm SHA-256 w aplikacjach docelowych 4.0</span><span class="sxs-lookup"><span data-stu-id="f4007-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f4007-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f4007-102">Details</span></span>|<span data-ttu-id="f4007-103">Wcześniej aplikacji ClickOnce za pomocą certyfikatu, który został podpisany za pomocą algorytmu SHA-256 wymaga .NET Framework 4.5 lub nowszej być obecne, nawet wtedy, gdy aplikacja docelowej 4.0.</span><span class="sxs-lookup"><span data-stu-id="f4007-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="f4007-104">Teraz, ukierunkowane na .NET Framework 4.0 ClickOnce aplikacje mogą być uruchamiane na .NET Framework 4.0, nawet jeśli podpisany przy użyciu algorytmu SHA-256.</span><span class="sxs-lookup"><span data-stu-id="f4007-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="f4007-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f4007-105">Suggestion</span></span>|<span data-ttu-id="f4007-106">Ta zmiana spowoduje usunięcie tej zależności i umożliwi certyfikatów SHA-256, ma być używany do podpisywania aplikacji ClickOnce, przeznaczonych dla platformy .NET Framework 4 i starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="f4007-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="f4007-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="f4007-107">Scope</span></span>|<span data-ttu-id="f4007-108">Mały</span><span class="sxs-lookup"><span data-stu-id="f4007-108">Minor</span></span>|
|<span data-ttu-id="f4007-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="f4007-109">Version</span></span>|<span data-ttu-id="f4007-110">4.6</span><span class="sxs-lookup"><span data-stu-id="f4007-110">4.6</span></span>|
|<span data-ttu-id="f4007-111">Typ</span><span class="sxs-lookup"><span data-stu-id="f4007-111">Type</span></span>|<span data-ttu-id="f4007-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f4007-112">Retargeting</span></span>|
