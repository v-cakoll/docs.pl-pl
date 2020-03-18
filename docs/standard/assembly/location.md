---
title: Lokalizacja zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733127"
---
# <a name="assembly-location"></a>Lokalizacja zestawu
Lokalizacja zestawu określa, czy czas wykonywania języka wspólnego można zlokalizować, gdy odwołuje się, a także można określić, czy zestaw może być współużytkowany z innymi zestawami. Można wdrożyć zestaw w następujących lokalizacjach:

- Katalog lub podkatalogi aplikacji.

     Jest to najbardziej popularna lokalizacja do wdrażania zestawu. Podkatalogi katalogu głównego aplikacji mogą być oparte na języku lub kulturze. Jeśli zestaw ma informacje w atrybucie kultury, musi znajdować się w podkatalogu pod katalogiem aplikacji o nazwie tej kultury.

- Globalna pamięć podręczna zestawów.

     Jest to pamięć podręczna kodu całego komputera, która jest instalowana wszędzie tam, gdzie jest zainstalowany czas wykonywania języka wspólnego. W większości przypadków, jeśli zamierzasz udostępnić zestaw z wieloma aplikacjami, należy wdrożyć go w globalnej pamięci podręcznej zestawów.

- Na serwerze HTTP.

     Zestaw wdrożony na serwerze HTTP musi mieć silną nazwę; wskazywać zestaw w sekcji bazy kodu pliku konfiguracyjnego aplikacji.

## <a name="see-also"></a>Zobacz też

- [Tworzenie zestawów](create.md)
- [Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)
- [Jak program runtime lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)
