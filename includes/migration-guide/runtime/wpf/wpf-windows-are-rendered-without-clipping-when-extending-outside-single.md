---
ms.openlocfilehash: d276e2bbf24c8b2389a0a8078c62c327c3729d50
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621358"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Okna WPF są renderowane bez obcinania podczas rozszerzania poza pojedynczy monitor

#### <a name="details"></a>Szczegóły

W .NET Framework 4,6 działający w systemie Windows 8 i nowszych całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z obsługą kilku monitorów. Różni się to od poprzednich wersji .NET Framework, które powinny wyciąć okna WPF, które przekroczą pojedynczy ekran.

#### <a name="suggestion"></a>Sugestia

Takie zachowanie (bez względu na to, czy ma być obcinane czy nie) można jawnie ustawić przy użyciu <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> elementu w <code>&lt;appSettings&gt;</code> pliku konfiguracyjnym aplikacji lub przez ustawienie <code>EnableMultiMonitorDisplayClipping</code> właściwości przy uruchamianiu aplikacji.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
