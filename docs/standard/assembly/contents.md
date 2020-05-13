---
title: Zawartość zestawu
description: W tym artykule opisano zawartość zestawu .NET, który może obejmować metadane zestawu, metadane typu, kod MSIL i zasoby.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 94df452162ed7290fab7fa267d2624e6d844a587
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378571"
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

## <a name="see-also"></a>Zobacz też

- [Zestawy w środowisku .NET](index.md)
- [Manifest zestawu](manifest.md)
- [Zagadnienia dotyczące zabezpieczeń zestawów](security-considerations.md)
