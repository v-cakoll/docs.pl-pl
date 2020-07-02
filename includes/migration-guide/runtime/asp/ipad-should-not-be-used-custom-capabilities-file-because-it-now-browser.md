---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620182"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>Tabletu IPad nie należy używać w pliku możliwości niestandardowych, ponieważ jest teraz funkcją przeglądarki

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, iPad jest identyfikatorem w domyślnym pliku możliwości przeglądarki ASP.NET, dlatego nie należy go używać w pliku możliwości niestandardowych

#### <a name="suggestion"></a>Sugestia

Jeśli są wymagane możliwości specyficzne dla tabletu iPad, należy zmodyfikować zachowanie urządzenia iPad przez ustawienie funkcji na wstępnie zdefiniowanej bramie iPad refID, &quot; &quot; zamiast wygenerowania nowego &quot; identyfikatora iPad &quot; przez dopasowanie agenta użytkownika.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
