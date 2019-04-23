---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804669"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce obsługuje algorytm SHA-256 w aplikacjach docelowych 4.0

|   |   |
|---|---|
|Szczegóły|Wcześniej aplikacji ClickOnce za pomocą certyfikatu, który został podpisany za pomocą algorytmu SHA-256 wymaga .NET Framework 4.5 lub nowszej być obecne, nawet wtedy, gdy aplikacja docelowej 4.0. Teraz, ukierunkowane na .NET Framework 4.0 ClickOnce aplikacje mogą być uruchamiane na .NET Framework 4.0, nawet jeśli podpisany przy użyciu algorytmu SHA-256.|
|Sugestia|Ta zmiana spowoduje usunięcie tej zależności i umożliwi certyfikatów SHA-256, ma być używany do podpisywania aplikacji ClickOnce, przeznaczonych dla platformy .NET Framework 4 i starszych wersji.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
