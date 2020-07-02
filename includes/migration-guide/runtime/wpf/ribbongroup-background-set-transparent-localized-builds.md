---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622376"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>Tło zestawu wstążki jest ustawione jako przezroczyste w zlokalizowanych kompilacjach

#### <a name="details"></a>Szczegóły

<xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>w tle dla zlokalizowanych kompilacji zawsze jest malowany przezroczysty Pędzel, co spowodowało słabą obsługę interfejsu użytkownika. Ten problem został rozwiązany w .NET Framework 4,7 WPF, aktualizując zlokalizowane zasoby dla <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> , które z kolei zapewniają, że wybrany jest prawidłowy pędzel.

#### <a name="suggestion"></a>Sugestia

Uaktualnij do .NET Framework 4,7

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
