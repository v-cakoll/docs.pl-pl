---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620217"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>Deserializacja obiektów w domenach AppDomain może zakończyć się niepowodzeniem

#### <a name="details"></a>Szczegóły

W niektórych przypadkach, gdy aplikacja używa dwóch lub większej liczby domen aplikacji z różnymi bazami aplikacji, próba deserializacji obiektów w kontekście wywołania logicznego między domenami aplikacji zgłasza wyjątek.

#### <a name="suggestion"></a>Sugestia

Zobacz [łagodzenie: deserializacja obiektów w domenach aplikacji](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
