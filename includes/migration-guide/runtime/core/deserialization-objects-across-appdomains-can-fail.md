---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804696"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>Deserializacja obiektów między domen aplikacji może zakończyć się niepowodzeniem

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach gdy aplikacja używa dwóch lub większej liczby domen aplikacji z różnymi bazami aplikacji, próba deserializacji obiektów w logicznym kontekście wywołań między domenami aplikacji zgłasza wyjątek.|
|Sugestia|Zobacz [środki zaradcze: Deserializacja obiektów między domenami aplikacji](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)|
|Zakres|Krawędź|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
