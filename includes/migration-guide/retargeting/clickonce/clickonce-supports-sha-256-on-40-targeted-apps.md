---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804389"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce obsługuje SHA-256 w aplikacjach 4.0

|   |   |
|---|---|
|Szczegóły|Wcześniej clickonce aplikacji z certyfikatem podpisanym za pomocą SHA-256 wymagałoby .NET Framework 4.5 lub nowsze być obecny, nawet jeśli aplikacja ukierunkowane 4.0. Teraz aplikacje ClickOnce kierowane przez platformę .NET Framework 4.0 można uruchomić w programie .NET Framework 4.0, nawet jeśli jest podpisana za pomocą funkcji SHA-256.|
|Sugestia|Ta zmiana usuwa tę zależność i umożliwia sha-256 certyfikatów, które mają być używane do podpisywania clickonce aplikacji, które są przeznaczone dla .NET Framework 4 i wcześniejszych wersji.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
