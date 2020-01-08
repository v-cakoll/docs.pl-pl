---
title: Zawartość zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345575"
---
# <a name="assembly-contents"></a>Zawartość zestawu

Ogólnie rzecz biorąc statyczny zestaw może składać się z czterech elementów:

- [Manifest zestawu](manifest.md), który zawiera metadane zestawu.

- Metadane typu.  

- Kod języka Microsoft Intermediate Language (MSIL) firmy Microsoft, który implementuje typy. Jest on generowany przez kompilator z jednego lub większej liczby plików kodu źródłowego.

- Zestaw [zasobów](../../framework/resources/index.md).  

Wymagany jest jedynie manifestu zestawu, ale aby zestaw posiadał znaczące funkcje potrzebne będą typy lub zasoby.

Na poniższej ilustracji przedstawiono te elementy pogrupowane w jeden plik fizyczny:

![Zestaw jednoplikowy o nazwie plik webassembly. dll](./media/contents/single-file-assembly.gif)

Podczas projektowania kodu źródłowego należy podjąć jawne decyzje dotyczące dzielenia funkcjonalności aplikacji na co najmniej jeden plik. Podczas projektowania kodu platformy .NET należy podjąć podobne decyzje dotyczące dzielenia funkcjonalności na jeden lub więcej zestawów.

## <a name="see-also"></a>Zobacz także

- [Zestawy w środowisku .NET](index.md)
- [Manifest zestawu](manifest.md)
- [Zagadnienia dotyczące zabezpieczeń zestawów](security-considerations.md)
