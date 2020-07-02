---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614833"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Ulepszony dostęp do niektórych narzędzi zestawu SDK platformy .NET

#### <a name="details"></a>Szczegóły

W 4.7.1 SDK .NET Framework narzędzia SvcConfigEditor.exe i SvcTraceViewer.exe zostały ulepszone, rozwiązując różne problemy z dostępnością. Większość z nich dotyczyła małych problemów, takich jak nazwa, które nie są zdefiniowane lub niektóre wzorce automatyzacji interfejsu użytkownika nie są poprawnie zaimplementowane. Chociaż wielu użytkowników nie wie o tych nieprawidłowych wartościach, klienci korzystający z technologii pomocniczych, takich jak czytniki zawartości ekranu, zobaczą więcej dostępnych narzędzi zestawu SDK. Z tego powodu te poprawki zmieniają pewne poprzednie zachowania, na przykład kolejność fokusu klawiatury. Aby uzyskać wszystkie poprawki ułatwień dostępu w tych narzędziach, można wykonać następujące czynności w pliku app.config:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |
