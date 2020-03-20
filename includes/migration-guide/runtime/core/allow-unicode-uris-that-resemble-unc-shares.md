---
ms.openlocfilehash: fbc39b6e1cc19f6c2846caaabb9a8a721494b4e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67856933"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Zezwalaj na unicode w identyfikatorach URI przypominających udziały UNC

|   |   |
|---|---|
|Szczegóły|W <xref:System.Uri?displayProperty=fullName>programie skonstruowanie identyfikatora URI pliku zawierającego zarówno nazwę udziału UNC, jak i znaki Unicode nie spowoduje już identyfikatora URI z nieprawidłowym stanem wewnętrznym. Zachowanie zmieni się tylko wtedy, gdy spełnione są wszystkie poniższe elementy:<ul><li>Identyfikator URI ma <code>file:</code> schemat i następuje cztery lub więcej ukośników.</li><li>Nazwa hosta zaczyna się od podkreślenia lub innego symbolu niezarezerwowane.</li><li>Identyfikator URI zawiera znaki Unicode.</li></ul>|
|Sugestia|Aplikacje współpracujące z identyfikatorami URI konsekwentnie zawierającymi Unicode mogły wykorzystać to zachowanie do niedozwolenia odwołań do akcji UNC. Te aplikacje <xref:System.Uri.IsUnc> powinny używać zamiast tego.|
|Zakres|Brzeg|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
