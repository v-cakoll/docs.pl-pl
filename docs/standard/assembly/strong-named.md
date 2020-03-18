---
title: Zestawy o silnych nazwach
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
ms.openlocfilehash: 12b8df3195b2708e4556d4f8065227054db9eb14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711574"
---
# <a name="strong-named-assemblies"></a>Zestawy o silnych nazwach

Silne nazewnictwo zestawu tworzy unikatową tożsamość dla zestawu i może zapobiec konfliktom zestawów.

## <a name="what-makes-a-strong-named-assembly"></a>Co sprawia, że zestaw o silnej nazwie?

Zestaw o silnej nazwie jest generowany przy użyciu klucza prywatnego, który odpowiada kluczpubliczny dystrybuowany z zestawu i samego zestawu. Zestaw zawiera manifest zestawu, który zawiera nazwy i haszysze wszystkich plików, które tworzą zestaw. Zestawy, które mają taką samą silną nazwę powinny być identyczne.

Zestawy o silnej nazwie można używać za pomocą programu Visual Studio lub narzędzia wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Jak: Podpisywać zestaw o silnej nazwie](sign-strong-name.md) lub [Sn.exe (narzędzie Silna nazwa)](../../framework/tools/sn-exe-strong-name-tool.md).

Po utworzeniu zestawu o silnej nazwie zawiera prostą nazwę tekstową zestawu, numer wersji, opcjonalne informacje o kulturze, podpis cyfrowy i klucz publiczny, który odpowiada kluczowi prywatnemu używanemu do podpisywania.

> [!WARNING]
> Nie należy polegać na silne nazwy dla bezpieczeństwa. Zapewniają one tylko unikatową tożsamość.

## <a name="why-strong-name-your-assemblies"></a>Dlaczego silne nazwy zespołów?

Podczas odwoływania się do zestawu o silnej nazwie, można oczekiwać pewnych korzyści, takich jak przechowywanie wersji i nazewnictwa ochrony. W platformie .NET Framework zestawy o silnych nazwach można zainstalować w globalnej pamięci podręcznej zestawów, co jest wymagane do włączenia niektórych scenariuszy.

Zestawy o silnych nazwach są przydatne w następujących scenariuszach:

- Chcesz włączyć zestawy, do których mają odwoływać się zestawy o `friend` silnej nazwie lub chcesz udzielić dostępu do zestawów z innych zestawów o silnych nazwach.

- Aplikacja wymaga dostępu do różnych wersji tego samego zestawu. Oznacza to, że potrzebujesz różnych wersji zestawu, aby załadować obok siebie w tej samej domenie aplikacji bez konfliktów. Na przykład jeśli istnieją różne rozszerzenia interfejsu API w zestawach, które mają tę samą prostą nazwę, silne nazewnictwo zapewnia unikatową tożsamość dla każdej wersji zestawu.

- Nie chcesz negatywnie wpływać na wydajność aplikacji przy użyciu zestawu, więc chcesz, aby zestaw był neutralny dla domeny. Wymaga to silnego nazewnictwa, ponieważ zestaw neutralny dla domeny musi być zainstalowany w globalnej pamięci podręcznej zestawów.

- Chcesz scentralizować obsługę aplikacji, stosując zasady wydawcy, co oznacza, że zestaw musi być zainstalowany w globalnej pamięci podręcznej zestawów.

Jeśli jesteś deweloperem typu open source i chcesz korzyści tożsamości zestawu o silnej nazwie, należy rozważyć zaewidencjonowanie w kluczprywatny skojarzony z zestawem do systemu kontroli źródła.

## <a name="see-also"></a>Zobacz też

- [Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)
- [Jak: Podpisywanie zestawu o silnej nazwie](sign-strong-name.md)
- [Sn.exe (narzędzie Silna nazwa)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
