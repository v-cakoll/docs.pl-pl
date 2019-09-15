---
title: Zawartość zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- assemblies [.NET Core]
- single-file assemblies
- multifile assemblies [.NET Framework]
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d9268b0ec1ea919730a2ebcd209507692284cc6
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973377"
---
# <a name="assembly-contents"></a>Zawartość zestawu
Ogólnie rzecz biorąc statyczny zestaw może składać się z czterech elementów:

- [Manifest zestawu](manifest.md), który zawiera metadane zestawu.

- Metadane typu.  

- Kod języka Microsoft Intermediate Language (MSIL) firmy Microsoft, który implementuje typy. Jest on generowany przez kompilator z jednego lub większej liczby plików kodu źródłowego.

- Zestaw zasobów.  

Wymagany jest jedynie manifestu zestawu, ale aby zestaw posiadał znaczące funkcje potrzebne będą typy lub zasoby.

Na poniższej ilustracji przedstawiono te elementy pogrupowane w jednym pliku fizycznym.

![Diagram, który pokazuje jednoplikowy zestaw o nazwie Moja Assembly. dll.](./media/contents/single-file-assembly.gif)

Na tej ilustracji wszystkie trzy pliki należą do zestawu, zgodnie z opisem w manifeście zestawu zawartym w MyAssembly.dll. Dla systemu plików są to trzy oddzielne pliki. Należy zauważyć, że plik Util.netmodule został skompilowany jako moduł, ponieważ nie zawiera żadnych informacji zestawu. Podczas tworzenia zestawu, manifest zestawu został dodany do MyAssembly.dll, wskazując na jego relację z Util.netmodule i Graphic.bmp.

Obecnie podczas projektowania kodu źródłowego, należy podejmować jawne decyzje dotyczące partycji funkcje aplikacji w jeden lub więcej plików. Podczas projektowania kodu .NET Framework, podejmiesz podobne decyzje, o tym jak podzielić funkcjonalności, tworząc jeden lub więcej zestawów.

## <a name="see-also"></a>Zobacz także

- [Zestawy w środowisku .NET](index.md)
- [Manifest zestawu](manifest.md)
- [Zagadnienia dotyczące zabezpieczeń zestawów](security-considerations.md)
