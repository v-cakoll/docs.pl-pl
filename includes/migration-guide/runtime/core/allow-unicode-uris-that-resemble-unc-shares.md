---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621169"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Zezwalaj na kodowanie Unicode w identyfikatorach URI, które przypominają udziały UNC

#### <a name="details"></a>Szczegóły

W programie <xref:System.Uri?displayProperty=fullName> konstruowanie identyfikatora URI pliku zawierającego zarówno nazwę udziału UNC, jak i znaki Unicode nie spowoduje już wystąpienia identyfikatora URI z nieprawidłowym stanem wewnętrznym. Zachowanie zmieni się tylko wtedy, gdy spełnione są wszystkie następujące warunki:<ul><li>Identyfikator URI ma schemat <code>file:</code> i ma cztery lub więcej ukośników.</li><li>Nazwa hosta zaczyna się od znaku podkreślenia lub innego niezastrzeżonego symbolu.</li><li>Identyfikator URI zawiera znaki Unicode.</li></ul>

#### <a name="suggestion"></a>Sugestia

Aplikacje korzystające z identyfikatorów URI spójnie zawierające kod Unicode mogą korzystać z tego zachowania, aby nie zezwalać na odwołania do udziałów UNC. Aplikacje te powinny być używane w <xref:System.Uri.IsUnc> zamian.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
