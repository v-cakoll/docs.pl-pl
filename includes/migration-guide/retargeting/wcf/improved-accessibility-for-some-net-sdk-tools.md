---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614833"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="0861b-101">Ulepszony dostęp do niektórych narzędzi zestawu SDK platformy .NET</span><span class="sxs-lookup"><span data-stu-id="0861b-101">Improved accessibility for some .NET SDK tools</span></span>

#### <a name="details"></a><span data-ttu-id="0861b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0861b-102">Details</span></span>

<span data-ttu-id="0861b-103">W 4.7.1 SDK .NET Framework narzędzia SvcConfigEditor.exe i SvcTraceViewer.exe zostały ulepszone, rozwiązując różne problemy z dostępnością.</span><span class="sxs-lookup"><span data-stu-id="0861b-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="0861b-104">Większość z nich dotyczyła małych problemów, takich jak nazwa, które nie są zdefiniowane lub niektóre wzorce automatyzacji interfejsu użytkownika nie są poprawnie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="0861b-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="0861b-105">Chociaż wielu użytkowników nie wie o tych nieprawidłowych wartościach, klienci korzystający z technologii pomocniczych, takich jak czytniki zawartości ekranu, zobaczą więcej dostępnych narzędzi zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="0861b-105">While many users wouldn't be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="0861b-106">Z tego powodu te poprawki zmieniają pewne poprzednie zachowania, na przykład kolejność fokusu klawiatury. Aby uzyskać wszystkie poprawki ułatwień dostępu w tych narzędziach, można wykonać następujące czynności w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="0861b-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| <span data-ttu-id="0861b-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0861b-107">Name</span></span>    | <span data-ttu-id="0861b-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="0861b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0861b-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="0861b-109">Scope</span></span>   | <span data-ttu-id="0861b-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="0861b-110">Edge</span></span>        |
| <span data-ttu-id="0861b-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="0861b-111">Version</span></span> | <span data-ttu-id="0861b-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0861b-112">4.7.1</span></span>       |
| <span data-ttu-id="0861b-113">Typ</span><span class="sxs-lookup"><span data-stu-id="0861b-113">Type</span></span>    | <span data-ttu-id="0861b-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="0861b-114">Retargeting</span></span> |
