---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614771"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a>Resgen odmawia załadowania zawartości z sieci Web

#### <a name="details"></a>Szczegóły

Pliki resx mogą zawierać dane wejściowe w formacie binarnym. Jeśli spróbujesz użyć Resgen do załadowania pliku pobranego z niezaufanej lokalizacji, domyślnie nie będzie można załadować danych wejściowych.

#### <a name="suggestion"></a>Sugestia

Resgen użytkownicy wymagający ładowania binarnych danych wejściowych z niezaufanych lokalizacji mogą usunąć oznaczenie sieci Web z pliku wejściowego lub zastosować opcję rezygnacji z Quirk. Dodaj następujące ustawienie rejestru, aby zastosować opcję rezygnacji z Quirk: [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |
