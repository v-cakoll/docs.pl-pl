---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620477"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>Elementy DataTemplate WPF są teraz widoczne dla UIA

#### <a name="details"></a>Szczegóły

Wcześniej <xref:System.Windows.DataTemplate?displayProperty=fullName> elementy były niewidoczne dla automatyzacji interfejsu użytkownika. Począwszy od 4,5, Automatyzacja interfejsu użytkownika będzie wykrywać te elementy. Jest to przydatne w wielu przypadkach, ale może przerwać testy, które są zależne od drzew UIA, które nie zawierają <xref:System.Windows.DataTemplate?displayProperty=fullName> elementów.

#### <a name="suggestion"></a>Sugestia

Testy automatyzacji interfejsu użytkownika dla tej aplikacji mogą wymagać aktualizacji do konta dla drzewa UIA teraz, łącznie z wcześniej niewidocznymi <xref:System.Windows.DataTemplate?displayProperty=fullName> elementami. Na przykład testy, które oczekują, że niektóre elementy powinny znajdować się obok siebie, mogą teraz oczekiwać, że wcześniej niewidoczne elementy UIA między. Testy, które opierają się na określonych licznikach lub indeksach dla elementów UIA, mogą wymagać aktualizacji z nowymi wartościami.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|
