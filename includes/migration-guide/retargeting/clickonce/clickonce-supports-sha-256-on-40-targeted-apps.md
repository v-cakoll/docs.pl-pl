---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804389"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="bff37-101">ClickOnce obsługuje SHA-256 w aplikacjach 4.0</span><span class="sxs-lookup"><span data-stu-id="bff37-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bff37-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bff37-102">Details</span></span>|<span data-ttu-id="bff37-103">Wcześniej clickonce aplikacji z certyfikatem podpisanym za pomocą SHA-256 wymagałoby .NET Framework 4.5 lub nowsze być obecny, nawet jeśli aplikacja ukierunkowane 4.0.</span><span class="sxs-lookup"><span data-stu-id="bff37-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="bff37-104">Teraz aplikacje ClickOnce kierowane przez platformę .NET Framework 4.0 można uruchomić w programie .NET Framework 4.0, nawet jeśli jest podpisana za pomocą funkcji SHA-256.</span><span class="sxs-lookup"><span data-stu-id="bff37-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="bff37-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="bff37-105">Suggestion</span></span>|<span data-ttu-id="bff37-106">Ta zmiana usuwa tę zależność i umożliwia sha-256 certyfikatów, które mają być używane do podpisywania clickonce aplikacji, które są przeznaczone dla .NET Framework 4 i wcześniejszych wersji.</span><span class="sxs-lookup"><span data-stu-id="bff37-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="bff37-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="bff37-107">Scope</span></span>|<span data-ttu-id="bff37-108">Mały</span><span class="sxs-lookup"><span data-stu-id="bff37-108">Minor</span></span>|
|<span data-ttu-id="bff37-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="bff37-109">Version</span></span>|<span data-ttu-id="bff37-110">4.6</span><span class="sxs-lookup"><span data-stu-id="bff37-110">4.6</span></span>|
|<span data-ttu-id="bff37-111">Typ</span><span class="sxs-lookup"><span data-stu-id="bff37-111">Type</span></span>|<span data-ttu-id="bff37-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="bff37-112">Retargeting</span></span>|
