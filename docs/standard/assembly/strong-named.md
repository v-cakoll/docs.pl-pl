---
title: Zestawy o silnych nazwach
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
ms.openlocfilehash: 12b8df3195b2708e4556d4f8065227054db9eb14
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711574"
---
# <a name="strong-named-assemblies"></a>Zestawy o silnych nazwach

Silne nazewnictwo zestawu tworzy unikatową tożsamość zestawu i może uniemożliwiać konflikty zestawów.

## <a name="what-makes-a-strong-named-assembly"></a>Co sprawia, że zestaw o silnej nazwie?

Zestaw o silnej nazwie jest generowany przy użyciu klucza prywatnego, który odnosi się do klucza publicznego dystrybuowanego z zestawem, i samego zestawu. Zestaw zawiera manifest zestawu, który zawiera nazwy i skróty wszystkich plików, które tworzą zestaw. Zestawy, które mają taką samą silną nazwę, powinny być identyczne.

Zestawy o silnych nazwach można używać przy użyciu programu Visual Studio lub narzędzia wiersza polecenia. Aby uzyskać więcej informacji, zobacz [jak: podpisywanie zestawu za pomocą silnej nazwy](sign-strong-name.md) lub [SN. exe (Narzędzie silnej nazwy)](../../framework/tools/sn-exe-strong-name-tool.md).

Gdy tworzony jest zestaw o silnej nazwie, zawiera prostą nazwę tekstu zestawu, numer wersji, opcjonalne informacje o kulturze, podpis cyfrowy i klucz publiczny, który odpowiada kluczowi prywatnemu służącemu do podpisywania.

> [!WARNING]
> Nie należy polegać na silnych nazwach zabezpieczeń. Zapewniają one tylko unikatową tożsamość.

## <a name="why-strong-name-your-assemblies"></a>Dlaczego warto silne nazwy zestawów?

W przypadku odwoływania się do zestawu o silnej nazwie można oczekiwać pewnych korzyści, takich jak przechowywanie wersji i ochrona nazw. W .NET Framework zestawy o silnej nazwie można zainstalować w globalnej pamięci podręcznej zestawów, która jest wymagana do obsługi niektórych scenariuszy.

Zestawy o silnych nazwach są przydatne w następujących scenariuszach:

- Chcesz umożliwić odwołujące się do zestawów za pomocą zestawów o silnych nazwach lub chcesz dać `friend` dostęp do zestawów z innych zestawów o silnych nazwach.

- Aplikacja musi mieć dostęp do różnych wersji tego samego zestawu. Oznacza to, że potrzebujesz różnych wersji zestawu do załadowania obok siebie w tej samej domenie aplikacji bez konfliktu. Jeśli na przykład istnieją różne rozszerzenia interfejsu API w zestawach o tej samej prostej nazwie, silne nazewnictwo zapewnia unikatową tożsamość dla każdej wersji zestawu.

- Nie chcesz negatywnie wpływać na wydajność aplikacji przy użyciu zestawu, więc chcesz, aby zestaw był neutralny dla domeny. Wymaga to silnej nazwy, ponieważ zestaw neutralny dla domeny musi być zainstalowany w globalnej pamięci podręcznej zestawów.

- Chcesz scentralizować obsługę aplikacji przez zastosowanie zasad wydawcy, co oznacza, że zestaw musi być zainstalowany w globalnej pamięci podręcznej zestawów.

Jeśli jesteś deweloperem typu "open source" i chcesz, aby tożsamość była korzystna dla zestawu o silnej nazwie, rozważ sprawdzenie klucza prywatnego skojarzonego z zestawem w systemie kontroli źródła.

## <a name="see-also"></a>Zobacz także

- [Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)
- [Instrukcje: podpisywanie zestawu za pomocą silnej nazwy](sign-strong-name.md)
- [SN. exe (Narzędzie silnej nazwy)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Tworzenie i używanie zestawów o silnych nazwach](create-use-strong-named.md)
