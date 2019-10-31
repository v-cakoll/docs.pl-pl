---
title: Lokalizacja zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: d44fb44db35b60f99583c20432c5998573298044
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107216"
---
# <a name="assembly-location"></a>Lokalizacja zestawu
Lokalizacja zestawu określa, czy środowisko uruchomieniowe języka wspólnego może je zlokalizować w przypadku odwołania, a także określić, czy zestaw może być współużytkowany z innymi zestawami. Zestaw można wdrożyć w następujących lokalizacjach:  
  
- Katalog lub podkatalogi aplikacji.  
  
     Jest to najczęściej używane miejsce wdrożenia zestawu. Podkatalogi katalogu głównego aplikacji mogą opierać się na języku lub kulturze. Jeśli zestaw zawiera informacje w atrybucie Culture, musi znajdować się w podkatalogu w katalogu aplikacji z nazwą tej kultury.  
  
- Globalna pamięć podręczna zestawów.  
  
     Jest to pamięć podręczna kodu całego komputera zainstalowana wszędzie tam, gdzie jest zainstalowany aparat plików wykonywalnych języka wspólnego. W większości przypadków, jeśli zamierzasz udostępnić zestaw z wieloma aplikacjami, należy wdrożyć go w globalnej pamięci podręcznej zestawów.  
  
- Na serwerze HTTP.  
  
     Zestaw wdrożony na serwerze HTTP musi mieć silną nazwę; Wskaż zestaw w sekcji codebase w pliku konfiguracyjnym aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie zestawów](create.md)
- [Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)
- [Jak środowisko uruchomieniowe lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Program z zestawami](program.md)
